# Lecture 3 notes
Lecture notes based on the first ever official [Plutus-Pioneer program](https://github.com/input-output-hk/plutus-pioneer-program). This notes follow the [YouTube lecture 3](https://www.youtube.com/watch?v=Lk1eIVm_ZTQ).

## warnings! 
Codes for lectures 1 & lecture 2 will not work from this point onwards because the cabal tag has been updated. If you desire to work with the past week's codes you should return to an older git status of the main plutus repo. This can be achieved by typing

    $git checkout 3746610e53654a1167aeb4c6294c6096d16b0502
     
and rebuild Plutus with nix

## 0. Outline
This week we will focus on the last piece of the puzzle regarding Scripts: context. We will see how these enable hughe possibilities for smart contracts.


Among other announcements: xew changes to the syntax as we move towards the Alonzo hard-fork event. Check and compare [`IsData.hs week02`](https://github.com/Igodlab/plutus-pioneer-program/blob/main/code/week02/src/Week02/IsData.hs) to this week's updated version: [`IsData.hs`](https://github.com/Igodlab/plutus-pioneer-program/blob/main/code/week03/src/Week03/IsData.hs)

## 1 [`Vesting.hs`](https://github.com/Igodlab/plutus-pioneer-program/blob/main/code/week03/src/Week03/Vesting.hs)
Scripts contain all the pertinent information for transactions. They are composed by three pieces of information: Datum, Redeemer & Context and are represented in the code by the `Data` typeclass. The first two have the flexibility to be other datatypes (like Boolean, Integer, etc..) as we have seen in the previous lecutre. This lecture we will explore on how to build a context to then embeed it into the script.

#### 1.1 Script code from the UTXO

#### 1.2 Few caveats before continuing
It is important to make the distinction that, unlike other projects, Scripts in Cardano **do not** run on the blockchain right after creation. They run on the wallet, allowing to check the correctness of the outcomes before broadcasting and draining fees.


#### 1.3 Time handling in Contexts
An often required funtionality of smart contracts is programability. This is a conditional based on some pre-defined elapse of time e.g. gift some ADA to your kids with the condition that they can retrieve those tokens wjen they are 18 or older. This is a litle problematic when it comes to Scripts because they will handle a different time being run in the wallet in contrast to when they are actually broadcasted into the blockchain. 

Cardano solves this by introducing time-ranges to give back that deterministic aspect. More details in the [`Contexts.hs`](https://github.com/input-output-hk/plutus/blob/master/plutus-ledger-api/src/Plutus/V1/Ledger/Contexts.hs) file.

#### 1.4 import public key

To get the 	Public key hash we have to go to the repl in a nix-local terminal

    repl$ import Wallet.Emulator
    repl$ import Ledger
    repl$ pubKeyHash $ walletPubKey $ Wallet 2
    
Now we are able to simulate the transaction in the Plutus-Playground. Note that the address for the Script is the same for any `give` actions from the wallets, this is because we have the same validator. In the `Vesting.hs` contract we have coded the benefitiary and the deadline into the Datum. Other choices a to **parametrize** the script as we will see in the next section.
    

## 2. Parametrize Scripts, code [Parametrized.hs](https://github.com/Igodlab/plutus-pioneer-program/blob/main/code/week03/src/Week03/Parametrized.hs)

Instead of coding the datum as in the previous file:
```haskell
    data VestingDatum = VestingDatum
        { beneficiary :: PubKeyHash
        , deadline    :: Slot
        } deriving Show
    
    {-# INLINABLE mkValidator #-}
    mkValidator :: VestingDatum -> () -> ScriptContext -> Bool
    mkValidator dat () ctx =
    .
    .
    .
    inst :: Scripts.ScriptInstance Vesting
    inst = Scripts.validator @Vesting
        $$(PlutusTx.compile [|| mkValidator ||])
        $$(PlutusTx.compile [|| wrap ||])
    .
    .
    .
```
Now we will parameterize datum. Instead of using `vestingDatum` in the input for `mkValidator`, now we just use unit datum `()` and add a new argument data. This data is just the renamed data from `data VestingDatum` to `data VestingParam`. We also we need to update a few other things in the code, note the instance for the Script in which we used **Template Haskell** to run inline, now this will not work because `mkValidator` takes an additional parameter `inst p` and in Template Haskell variables have to be known at *compilte-time*. However, if we would add the `p` like this: `$$(PlutusTx.compile [|| mkValidator p ||])` it will not work because `inst p` is read at *run-time*.


The solution to the above issue is reached using a plutus coded class named **Lift** found in  [`Class`](https://github.com/input-output-hk/plutus/blob/master/plutus-tx/src/PlutusTx/Lift.hs)
```haskell
    data VestingParam = VestingParam
        { beneficiary :: PubKeyHash
        , deadline :: Slot
        } deriving Show
        
    {-# INLINABLE mkValidator #-}
    mkValidator :: VestingParam -> () -> () -> ScriptContext -> bool
    mkValidator p () () ctx
    .
    .
    .
    inst :: VestingParam -> Scripts.ScriptInstance Vesting
    inst p = Scripts.validator @Vesting
        ($$(PlutusTx.compile [|| mkValidator ||]) `PlutusTx.applyCode` PlutusTx.liftCode p)
        $$(PlutusTx.compile [|| wrap ||])
        
        .
        .
        .
```
In summary what we have done with the last part is converting the Haskell value `p` into a Plutus-Script value using `PlutusTx.liftCode p` and we applied it into the splice with `PlutusTx.applyCode`. The last missing part is that we need a lift instance. We can add this easily using `PlutusTx.makelift ''VestingParam`. 
