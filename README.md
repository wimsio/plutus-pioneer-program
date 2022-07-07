# Plutus Pioneer Program

## Lectures

- [Lecture #1](https://youtu.be/IEn6jUo-0vU)

  - Welcome
  - The (E)UTxO-model
  - Running an example auction contract on a local Playground
  - Homework

- [Lecture #2](https://youtu.be/E5KRk5y9KjQ)

  - Triggering change.
  - Low-level, untyped on-chain validation scripts.
  - High-level, typed on-chain validation scripts.

- [Lecture #3](https://youtu.be/Lk1eIVm_ZTQ)

  - Script context.
  - Time handling.
  - Parameterized contracts.

- [Lecture #4](https://youtu.be/6Reuh0xZDjY)

  - Monads
  - The `EmulatorTrace` monad.
  - The `Contract` monad.

- [Lecture #5](https://youtu.be/6VbhY162GQA)

  - Values.
  - Native tokens & minting policies.
  - NFT's.

- [Lecture #6](https://youtu.be/wY7R-PJn66g)

  - Oracles.
  - Using the PAB.

- [Lecture #7](https://youtu.be/oJupInqvJUI)

  - Commit schemes.
  - State machines.

- [Lecture #8](https://youtu.be/JMRwkMgaBOg)

  - Another state machine example: token sale.
  - Automatic testing using emulator traces.
  - Interlude: optics.
  - Property based testing with `QuickCheck`.
  - Testing Plutus contracts with property based testing.

- [Lecture #9](https://youtu.be/-RpCqHuxfQQ)

  - Marlowe overview ([slides](Marlowe_Plutus_Pioneers_June_2021.pdf)).
  - Marlowe in Plutus.
  - Marlowe Playground demo.

- [Lecture #10](https://youtu.be/Dg36h9YPMz4)

  - Uniswap overview.
  - Uniswap implementation in Plutus.
  - Deploying Uniswap with the PAB.
  - Demo.
  - Using `curl` to interact with the PAB.

## Code Examples
 
- Lecture #1:  [English Auction](code/week01)
- Lecture #2:  [Simple Validation](code/week02)
- Lecture #3:  [Validation Context & Parameterized Contracts](code/week03)
- Lecture #4:  [Monads, `EmulatorTrace` & `Contract`](code/week04)
- Lecture #5:  [Minting Policies](code/week05)
- Lecture #6:  [Oracles](code/week06)
- Lecture #7:  [State Machines](code/week07)
- Lecture #8:  [Testing](code/week08)
- Lecture #9:  [Marlowe](code/week09)
- Lecture #10: [Uniswap](code/week10)

## Exercises

- Week #1

  - Build the [English Auction](code/week01) contract with `cabal build` (you may need to run `cabal update` first).
  - Clone the [The Plutus repository](https://github.com/input-output-hk/plutus), check out the correct commit
    as specified in [cabal.project](code/week01/cabal.project).
  - Set-up IOHK binary caches [How to set up the IOHK binary caches](https://github.com/input-output-hk/plutus#iohk-binary-cache). "If you do not do this, you will end up building GHC, which takes several hours. If you find yourself building GHC, STOP and fix the cache."
  - Enter a `nix-shell`.
  - Go to the `plutus-playground-client` folder.
  - Start the Playground server with `plutus-playground-server`.
  - Start the Playground client (in another `nix-shell`) with `npm run start`.
  - Copy-paste the auction contract into the Playground editor - don't forget to remove the module header!
  - Compile.
  - Simulate various auction scenarios.

- Week #2

  - Fix and complete the code in the [Homework1](code/week02/src/Week02/Homework1.hs) module.
  - Fix and complete the code in the [Homework2](code/week02/src/Week02/Homework2.hs) module.

- Week #3

  - Fix and complete the code in the [Homework1](code/week03/src/Week03/Homework1.hs) module.
  - Fix and complete the code in the [Homework2](code/week03/src/Week03/Homework2.hs) module.

- Week #4

  - Write an appropriate `EmulatorTrace` that uses the `payContract` contract in the [Homework](code/week04/src/Week04/Homework.hs) module.
  - Catch errors in the `payContract` contract in the same module.

- Week #5

  - Add a deadline to the minting policy in the [Homework1](code/week05/src/Week05/Homework1.hs) module.
  - Fix the token name to the empty `ByteString` in the NFT contract in the [Homework2](code/week05/src/Week05/Homework2.hs) module.

- Week #6

  - Get the Oracle demo running and extend it in some way.

- Week #7

  - Implement the game of "Rock, Paper, Scissors" using state machines.

- Week #8

  - Add a new operation `close` to the `TokenSale`-contract that allows the seller to close the contract and
    retrieve all remaining funds (including the NFT).
  - Modify the tests accordingly.

- Week #9

  - Modify the example Marlowe contract, so that Charlie must put down twice the deposit in the very beginning,
    which gets split between Alice and Bob if Charlie refuses to make his choice.

- Week #10

  - Get the Uniswap demo running and extend it in some way.

## Solutions

- Week #2

  - [`Homework1`](code/week02/src/Week02/Solution1.hs)
  - [`Homework2`](code/week02/src/Week02/Solution2.hs)

- Week #3

  - [`Homework1`](code/week03/src/Week03/Solution1.hs)
  - [`Homework2`](code/week03/src/Week03/Solution2.hs)

- Week #4

  - [`Homework`](code/week04/src/Week04/Solution.hs)

- Week #5

  - [`Homework1`](code/week05/src/Week05/Solution1.hs)
  - [`Homework2`](code/week05/src/Week05/Solution2.hs)

- Week #7

  - [`RockPaperScissors`](code/week07/src/Week07/RockPaperScissors.hs)
  - [`TestRockPaperScissors`](code/week07/src/Week07/TestRockPaperScissors.hs)

- Week #8

  - [`TokenSaleWithClose`](code/week08/src/Week08/TokenSaleWithClose.hs)
  - [`ModelWithClose`](code/week08/test/Spec/ModelWithClose.hs)
  - [`TraceWithClose`](code/week08/test/Spec/TraceWithClose.hs)

- Week #9

  - [`solution`](code/week09/app/solution.hs)

## Some Plutus Modules

- [`Language.Marlowe.Semantics`](https://github.com/input-output-hk/plutus/blob/master/marlowe/src/Language/Marlowe/Semantics.hs), contains Marlowe types and semantics.
- [`Plutus.Contract.StateMachine`](https://github.com/input-output-hk/plutus/blob/master/plutus-contract/src/Plutus/Contract/StateMachine.hs), contains types and functions for using state machines.
- [`Plutus.Contract.Test`](https://github.com/input-output-hk/plutus/blob/master/plutus-contract/src/Plutus/Contract/Test.hs), provides various ways to write tests for Plutus contracts.
- [`Plutus.Contract.Test.ContractModel`](https://github.com/input-output-hk/plutus/blob/master/plutus-contract/src/Plutus/Contract/Test/ContractModel.hs), support for property based testing of Plutus contracts.
- [`Plutus.Contracts.Uniswap`](https://github.com/input-output-hk/plutus/blob/master/plutus-use-cases/src/Plutus/Contracts/Uniswap.hs), an implementation of Uniswap in Plutus.
- [`Plutus.PAB.Webserver.API`](https://github.com/input-output-hk/plutus/blob/master/plutus-pab/src/Plutus/PAB/Webserver/API.hs), contains the HTTP-interface provided by the PAB.
- [`Plutus.Trace.Emulator`](https://github.com/input-output-hk/plutus/blob/master/plutus-contract/src/Plutus/Trace/Emulator.hs), contains types and functions related to traces.
- [`Plutus.V1.Ledger.Ada`](https://github.com/input-output-hk/plutus/blob/master/plutus-ledger-api/src/Plutus/V1/Ledger/Ada.hs), contains support for the Ada currency.
- [`Plutus.V1.Ledger.Contexts`](https://github.com/input-output-hk/plutus/blob/master/plutus-ledger-api/src/Plutus/V1/Ledger/Contexts.hs), contains the definition of the context-related types.
- [`Plutus.V1.Ledger.Interval`](https://github.com/input-output-hk/plutus/blob/master/plutus-ledger-api/src/Plutus/V1/Ledger/Interval.hs), contains the definition of and helper functions for the `Interval` type.
- [`Plutus.V1.Ledger.Slot`](https://github.com/input-output-hk/plutus/blob/master/plutus-ledger-api/src/Plutus/V1/Ledger/Slot.hs), contains the definition of the `Slot` type.
- [`Plutus.V1.Ledger.Value`](https://github.com/input-output-hk/plutus/blob/master/plutus-ledger-api/src/Plutus/V1/Ledger/Value.hs), contains the definition of and helper functions for the `Value` type.
- [`PlutusTx.Data`](https://github.com/input-output-hk/plutus/blob/master/plutus-tx/src/PlutusTx/Data.hs), contains the definition of the `Data` type.
- [`PlutusTx.IsData.Class`](https://github.com/input-output-hk/plutus/blob/master/plutus-tx/src/PlutusTx/IsData/Class.hs), defines the `IsData` class.

## Plutus community playground

- [Week 1 Community Playground(Legacy)](https://playground-week1.plutus-community.com/)
- [Week 2 Community Playground(Legacy)](https://playground-week2.plutus-community.com/)
- [Week 3 Community Playground(Current)](https://playground-week3.plutus-community.com/)
- [Week 4 Community Playground(Current)](https://playground.plutus-community.com/)


## Additional Resources

- [The Plutus repository](https://github.com/input-output-hk/plutus)
- [Learn You a Haskell for Great Good!](http://learnyouahaskell.com/)
- [Haskell & Cryptocurrencies course Mongolia](https://www.youtube.com/playlist?list=PLJ3w5xyG4JWmBVIigNBytJhvSSfZZzfTm)

## Video Links

- [`Plutus Pioneer Program   Lecture #4`] (https://www.youtube.com/watch?v=_U9sDP6ODs4).
- [`Plutus Pioneer Program   Lecture #5`] (https://www.youtube.com/watch?v=CTAPJ-HCzSs).
- [Plutus Pioneer Program   Lecture 2 (Phụ đề)] (https://www.youtube.com/watch?v=7nDGZkUIeUQ)
-[Plutus Pioneer Program   Lecture 7 (Phụ đề)] (https://www.youtube.com/watch?v=ptsltoZNl50)
-[Plutus Pioneer Program   Lecture 9 (Phụ đề)] (https://www.youtube.com/watch?v=J5as459k10E)
-[Plutus Pioneer Program  Lecture  8 (Phụ đề)] (https://www.youtube.com/watch?v=tGjEvumVBk8)
-[Plutus Pioneer Program  Lecture 10 (Phụ đề)] (https://www.youtube.com/watch?v=X_q4AHMsw5Y)
-[Plutus Pioneer Program  Lecture 3 (Phụ đề)] (https://www.youtube.com/watch?v=WG3uw-TkW2k)
-[Plutus Pioneer Program  Lecture 4 (Phụ đề)] (https://www.youtube.com/watch?v=HLJOcKlEucI)
-[Plutus Pioneer Program  Lecture 5 (Phụ đề)] (https://www.youtube.com/watch?v=bcf0vTJ-NtE)
-[Plutus Pioneer Program  Lecture 6 (Phụ đề)] (https://www.youtube.com/watch?v=X9fOkkpj-aU)
-[Plutus Pioneer Program - How to think about Monads] (https://www.youtube.com/watch?v=8-6Y93J6W1w)
-[Plutus Pioneer Program - Iteration #2 - Lecture #1] (https://www.youtube.com/watch?v=_zr3W8cgzIQ)
-[Plutus Pioneer Program - Iteration #2 - Lecture #10] (https://www.youtube.com/watch?v=CPfcyDaDtt8)
-[Plutus Pioneer Program - Iteration #2 - Lecture #2] (https://www.youtube.com/watch?v=sN3BIa3GAOc)
-[Plutus Pioneer Program - Iteration #2 - Lecture #4] (https://www.youtube.com/watch?v=g4lvA14I-Jg)
-[Plutus Pioneer Program - Iteration #2 - Lecture #5] (https://www.youtube.com/watch?v=SsaVjSsPPcg)
-[Plutus Pioneer Program - Iteration #2 - Lecture #6] (https://www.youtube.com/watch?v=24SHPHEc3zo)
-[Plutus Pioneer Program - Iteration #2 - Lecture #7] (https://www.youtube.com/watch?v=uwZ903Zd0DU)
-[Plutus Pioneer Program - Iteration #2 - Lecture #8] (https://www.youtube.com/watch?v=zW3D2iM5uVg)
-[Plutus Pioneer Program - Iteration #2 - Lecture #9] (https://www.youtube.com/watch?v=H1WPL01qWCc)
-[Plutus Pioneer Program - Lecture #1] (https://www.youtube.com/watch?v=IEn6jUo-0vU)
-[Plutus Pioneer Program - Lecture #1] (https://www.youtube.com/watch?v=igV7kMXcdpw)
-[Plutus Pioneer Program - Lecture #10] (https://www.youtube.com/watch?v=1qzToWM3ZTw)
-[Plutus Pioneer Program - Lecture #10] (https://www.youtube.com/watch?v=Dg36h9YPMz4)
-[Plutus Pioneer Program - Lecture #2] (https://www.youtube.com/watch?v=0VoSbwvq5r4)
-[Plutus Pioneer Program - Lecture #2] (https://www.youtube.com/watch?v=E5KRk5y9KjQ)
-[Plutus Pioneer Program - Lecture #2] (https://www.youtube.com/watch?v=aO96HJcQgJc)
-[Plutus Pioneer Program - Lecture #3] (https://www.youtube.com/watch?v=Dw6kzRbmLnk)
-[Plutus Pioneer Program - Lecture #4] (https://www.youtube.com/watch?v=6Reuh0xZDjY)
-[Plutus Pioneer Program - Lecture #4] (https://www.youtube.com/watch?v=FUglEDP5brI)
-[Plutus Pioneer Program - Lecture #4] (https://www.youtube.com/watch?v=6Reuh0xZDjY)
-[Plutus Pioneer Program - Lecture #5] (https://www.youtube.com/watch?v=6VbhY162GQA)
-[Plutus Pioneer Program - Lecture #5] (https://www.youtube.com/watch?v=CTvOIusN_p8)
-[Plutus Pioneer Program - Lecture #5] (https://www.youtube.com/watch?v=6VbhY162GQA)
-[Plutus Pioneer Program - Lecture #6] (https://www.youtube.com/watch?v=Tr2VBm8vOhw)
-[Plutus Pioneer Program - Lecture #6] (https://www.youtube.com/watch?v=wY7R-PJn66g)
-[Plutus Pioneer Program - Lecture #7] (https://www.youtube.com/watch?v=oJupInqvJUI)
-[Plutus Pioneer Program - Lecture #8] (https://www.youtube.com/watch?v=PaMCOHSqX0Y)
-[Plutus Pioneer Program - Lecture #8] (https://www.youtube.com/watch?v=JMRwkMgaBOg)
-[Plutus Pioneer Program - Lecture #9] (https://www.youtube.com/watch?v=RzRtPumv9VE)
-[Plutus Pioneer Program - Second cohort - Lecture #1] (https://www.youtube.com/watch?v=wqC8oiurqsI)
-[Plutus Pioneer Program - Second cohort - Lecture #4] (https://www.youtube.com/watch?v=KxGqoDS4dN8)
-[Plutus Pioneer Program - Second cohort - Lecture 10] (https://www.youtube.com/watch?v=7Lfj2mGIPLQ)
-[Plutus Pioneer Program - Second cohort - Lecture 5] (https://www.youtube.com/watch?v=XJ3w5U-xSfQ)
-[Plutus Pioneer Program - Second cohort - Lecture 6] (https://www.youtube.com/watch?v=IAywGorbpfY)
-[Plutus Pioneer Program - Second cohort - Lecture 9] (https://www.youtube.com/watch?v=FSJXxh5QuGc)
-[Plutus Pioneer Program - Semana 1] (https://www.youtube.com/watch?v=SsYIRfDtqQA)
-[Plutus Pioneer Program - Week02 - Solution] (https://www.youtube.com/watch?v=v4Y_bAuDzdI)
-[Plutus Pioneer Program - Week03 - Solutions] (https://www.youtube.com/watch?v=2NV1I5yJzh8)
-[Plutus Pioneer Program - Week05 - Solutions] (https://www.youtube.com/watch?v=FkfjhfTebIE)
-[Plutus Pioneer Program & Q1 Price Recap] (https://www.youtube.com/watch?v=1IC8GYouZ14)
-[Plutus Pioneer Program Lecture 1 (Phụ đề)] (https://www.youtube.com/watch?v=CJD8ctJqDw0)
-[Plutus pioneer program soon be again!!!Be part of the team!!!!] (https://www.youtube.com/watch?v=WImfc-GMVXs)
-[Plutus Pioneer Programme Résumé des mots de bienvenue de Lars Brünjes] (https://www.youtube.com/watch?v=iCDs7_LTIOc)
-[Plutus Pioneer’s Capstone Project Challenge (Cardano360 - October 2021)] (https://www.youtube.com/watch?v=vkkI9_MtXq0)
-[Plutus Pioneering - Elon's FUD - ADA Breaks $200!] (https://www.youtube.com/watch?v=HYr9IvUBxXw)
-[Plutus Pioneers Program: Week 1 - Set Up Virtual Machine & Visual Studio Code (Beginner's Guide)] (https://www.youtube.com/watch?v=i_PIqUjBQoE)
-[Plutus Pioneers Program: Week 2 - Validation Script & Homework! Beginner's Guide] (https://www.youtube.com/watch?v=MhhR8Xk-Oeg)
-[Plutus Pioneers Program: Week 3 - Script Context & Homework] (https://www.youtube.com/watch?v=eojRyLDCrv0)
-[Plutus Pioneers Program: Week 4 - Contract Emulator & Homework] (https://www.youtube.com/watch?v=XhFQDgLA29M)
-[Plutus Playground - Video Tutorial: Compiling and testing a Plutus App] (https://www.youtube.com/watch?v=DhRS-JvoCw8)
-[Plutus Playground Locally with Docker] (https://www.youtube.com/watch?v=q2ctG0_jrB4)
-[Plutus Playground Refresh (Cardano 2021)] (https://www.youtube.com/watch?v=dzrIcjEwOwU)
-[Plutus Playground Setup With VSCode and WSL] (https://www.youtube.com/watch?v=CXHmbOkoVG8)
-[Plutus Playground: Contrato Inteligente na blockchain Cardano] (https://www.youtube.com/watch?v=VLDl5izAF2g)
-[Plutus Smart Contract Development: Running Plutus on Windows with WSL] (https://www.youtube.com/watch?v=g2F9raiGp_s)
-[Plutus Smart Contracts In A Nutshell] (https://www.youtube.com/watch?v=yQYXfDG63WI)
-[Plutus study group 1 - (e)UTxO model a bit on Solidity how to proceed] (https://www.youtube.com/watch?v=aKZxpf7bLFA)
-[Plutus: The Tokenomics] (https://www.youtube.com/watch?v=wkj-VjWGo7c)
-[Plutuswap joins ecosystem of #Cardano #blockchain] (https://www.youtube.com/watch?v=kavP7MSknrk)
-[Project Plutus #1: Setting up the repo basic design] (https://www.youtube.com/watch?v=fobdtOdn5lY)
-[Project Plutus #2: Git setup + the basics] (https://www.youtube.com/watch?v=qTS28R2udsI)




