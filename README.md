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

## Gimbalands Project Based Learning Plutus

000.- [Securing Wallet, getting ADA and Staking on Cardano ](https://gimbalabs.com/pbl/csk/csk000)
001.- [Getting Started with GitHub and the Marlowe Playground](https://gimbalabs.com/pbl/csk/csk001)
002.- [Talking About Cardano](https://gimbalabs.com/pbl/csk/csk003)
003.- [ Where does blockchain fit in the development stack?](https://gimbalabs.com/pbl/csk/csk004)
004.- [A mini-csk on Transaction Metadata ](https://gimbalabs.com/pbl/csk/csk005)
005.- [The Gimbalabs Local ADA Spending Challenge](https://gimbalabs.com/pbl/csk/csk006)
006.- [What can I do with Transaction Metadata on Cardano](https://gimbalabs.com/pbl/csk/csk007)
007.- [Building Transactions on cardano-cli](https://gimbalabs.com/pbl/csk/csk008)
008.- [Metadata, Minting, and Messing with Unsigs](https://gimbalabs.com/pbl/csk/csk009)
009.- [The Lobster Challenge](https://gimbalabs.com/pbl/csk/csk010)
010.- [What can I do with GameChanger Wallet? (Part 1) ](https://gimbalabs.com/pbl/csk/csk011)

## Video Links

- [Plutus Pioneer Program   Lecture #4](https://www.youtube.com/watch?v=_U9sDP6ODs4)
- [Plutus Pioneer Program   Lecture #5](https://www.youtube.com/watch?v=CTAPJ-HCzSs)
- [Plutus Pioneer Program   Lecture 2 (Phụ đề)](https://www.youtube.com/watch?v=7nDGZkUIeUQ)
- [Plutus Pioneer Program   Lecture 7 (Phụ đề)](https://www.youtube.com/watch?v=ptsltoZNl50)
- [Plutus Pioneer Program   Lecture 9 (Phụ đề)](https://www.youtube.com/watch?v=J5as459k10E)
- [Plutus Pioneer Program  Lecture  8 (Phụ đề)](https://www.youtube.com/watch?v=tGjEvumVBk8)
- [Plutus Pioneer Program  Lecture 10 (Phụ đề)](https://www.youtube.com/watch?v=X_q4AHMsw5Y)
- [Plutus Pioneer Program  Lecture 3 (Phụ đề)](https://www.youtube.com/watch?v=WG3uw-TkW2k)
- [Plutus Pioneer Program  Lecture 4 (Phụ đề)](https://www.youtube.com/watch?v=HLJOcKlEucI)
- [Plutus Pioneer Program  Lecture 5 (Phụ đề)](https://www.youtube.com/watch?v=bcf0vTJ-NtE)
- [Plutus Pioneer Program  Lecture 6 (Phụ đề)](https://www.youtube.com/watch?v=X9fOkkpj-aU)
- [Plutus Pioneer Program - How to think about Monads](https://www.youtube.com/watch?v=8-6Y93J6W1w)
- [Plutus Pioneer Program - Iteration #2 - Lecture #1](https://www.youtube.com/watch?v=_zr3W8cgzIQ)
- [Plutus Pioneer Program - Iteration #2 - Lecture #10](https://www.youtube.com/watch?v=CPfcyDaDtt8)
- [Plutus Pioneer Program - Iteration #2 - Lecture #2](https://www.youtube.com/watch?v=sN3BIa3GAOc)
- [Plutus Pioneer Program - Iteration #2 - Lecture #4](https://www.youtube.com/watch?v=g4lvA14I-Jg)
- [Plutus Pioneer Program - Iteration #2 - Lecture #5](https://www.youtube.com/watch?v=SsaVjSsPPcg)
- [Plutus Pioneer Program - Iteration #2 - Lecture #6](https://www.youtube.com/watch?v=24SHPHEc3zo)
- [Plutus Pioneer Program - Iteration #2 - Lecture #7](https://www.youtube.com/watch?v=uwZ903Zd0DU)
- [Plutus Pioneer Program - Iteration #2 - Lecture #8](https://www.youtube.com/watch?v=zW3D2iM5uVg)
- [Plutus Pioneer Program - Iteration #2 - Lecture #9](https://www.youtube.com/watch?v=H1WPL01qWCc)
- [Plutus Pioneer Program - Lecture #1](https://www.youtube.com/watch?v=IEn6jUo-0vU)
- [Plutus Pioneer Program - Lecture #1](https://www.youtube.com/watch?v=igV7kMXcdpw)
- [Plutus Pioneer Program - Lecture #10](https://www.youtube.com/watch?v=1qzToWM3ZTw)
- [Plutus Pioneer Program - Lecture #10](https://www.youtube.com/watch?v=Dg36h9YPMz4)
- [Plutus Pioneer Program - Lecture #2](https://www.youtube.com/watch?v=0VoSbwvq5r4)
- [Plutus Pioneer Program - Lecture #2](https://www.youtube.com/watch?v=E5KRk5y9KjQ)
- [Plutus Pioneer Program - Lecture #2](https://www.youtube.com/watch?v=aO96HJcQgJc)
- [Plutus Pioneer Program - Lecture #3](https://www.youtube.com/watch?v=Dw6kzRbmLnk)
- [Plutus Pioneer Program - Lecture #4](https://www.youtube.com/watch?v=6Reuh0xZDjY)
- [Plutus Pioneer Program - Lecture #4](https://www.youtube.com/watch?v=FUglEDP5brI)
- [Plutus Pioneer Program - Lecture #4](https://www.youtube.com/watch?v=6Reuh0xZDjY)
- [Plutus Pioneer Program - Lecture #5](https://www.youtube.com/watch?v=6VbhY162GQA)
- [Plutus Pioneer Program - Lecture #5](https://www.youtube.com/watch?v=CTvOIusN_p8)
- [Plutus Pioneer Program - Lecture #5](https://www.youtube.com/watch?v=6VbhY162GQA)
- [Plutus Pioneer Program - Lecture #6](https://www.youtube.com/watch?v=Tr2VBm8vOhw)
- [Plutus Pioneer Program - Lecture #6](https://www.youtube.com/watch?v=wY7R-PJn66g)
- [Plutus Pioneer Program - Lecture #7](https://www.youtube.com/watch?v=oJupInqvJUI)
- [Plutus Pioneer Program - Lecture #8](https://www.youtube.com/watch?v=PaMCOHSqX0Y)
- [Plutus Pioneer Program - Lecture #8](https://www.youtube.com/watch?v=JMRwkMgaBOg)
- [Plutus Pioneer Program - Lecture #9](https://www.youtube.com/watch?v=RzRtPumv9VE)
- [Plutus Pioneer Program - Second cohort - Lecture #1](https://www.youtube.com/watch?v=wqC8oiurqsI)
- [Plutus Pioneer Program - Second cohort - Lecture #4](https://www.youtube.com/watch?v=KxGqoDS4dN8)
- [Plutus Pioneer Program - Second cohort - Lecture 10](https://www.youtube.com/watch?v=7Lfj2mGIPLQ)
- [Plutus Pioneer Program - Second cohort - Lecture 5](https://www.youtube.com/watch?v=XJ3w5U-xSfQ)
- [Plutus Pioneer Program - Second cohort - Lecture 6](https://www.youtube.com/watch?v=IAywGorbpfY)
- [Plutus Pioneer Program - Second cohort - Lecture 9](https://www.youtube.com/watch?v=FSJXxh5QuGc)
- [Plutus Pioneer Program - Semana 1](https://www.youtube.com/watch?v=SsYIRfDtqQA)
- [Plutus Pioneer Program - Week02 - Solution](https://www.youtube.com/watch?v=v4Y_bAuDzdI)
- [Plutus Pioneer Program - Week03 - Solutions](https://www.youtube.com/watch?v=2NV1I5yJzh8)
- [Plutus Pioneer Program - Week05 - Solutions](https://www.youtube.com/watch?v=FkfjhfTebIE)
- [Plutus Pioneer Program & Q1 Price Recap](https://www.youtube.com/watch?v=1IC8GYouZ14)
- [Plutus Pioneer Program Lecture 1 (Phụ đề)](https://www.youtube.com/watch?v=CJD8ctJqDw0)
- [Plutus pioneer program soon be again!!!Be part of the team!!!!](https://www.youtube.com/watch?v=WImfc-GMVXs)
- [Plutus Pioneer Programme Résumé des mots de bienvenue de Lars Brünjes](https://www.youtube.com/watch?v=iCDs7_LTIOc)
- [Plutus Pioneer’s Capstone Project Challenge (Cardano360 - October 2021)](https://www.youtube.com/watch?v=vkkI9_MtXq0)
- [Plutus Pioneering - Elon's FUD - ADA Breaks $200!](https://www.youtube.com/watch?v=HYr9IvUBxXw)
- [Plutus Pioneers Program: Week 1 - Set Up Virtual Machine & Visual Studio Code (Beginner's Guide)](https://www.youtube.com/watch?v=i_PIqUjBQoE)
- [Plutus Pioneers Program: Week 2 - Validation Script & Homework! Beginner's Guide](https://www.youtube.com/watch?v=MhhR8Xk-Oeg)
- [Plutus Pioneers Program: Week 3 - Script Context & Homework](https://www.youtube.com/watch?v=eojRyLDCrv0)
- [Plutus Pioneers Program: Week 4 - Contract Emulator & Homework](https://www.youtube.com/watch?v=XhFQDgLA29M)
- [Plutus Playground - Video Tutorial: Compiling and testing a Plutus App](https://www.youtube.com/watch?v=DhRS-JvoCw8)
- [Plutus Playground Locally with Docker](https://www.youtube.com/watch?v=q2ctG0_jrB4)
- [Plutus Playground Refresh (Cardano 2021)](https://www.youtube.com/watch?v=dzrIcjEwOwU)
- [Plutus Playground Setup With VSCode and WSL](https://www.youtube.com/watch?v=CXHmbOkoVG8)
- [Plutus Playground: Contrato Inteligente na blockchain Cardano](https://www.youtube.com/watch?v=VLDl5izAF2g)
- [Plutus Smart Contract Development: Running Plutus on Windows with WSL](https://www.youtube.com/watch?v=g2F9raiGp_s)
- [Plutus Smart Contracts In A Nutshell](https://www.youtube.com/watch?v=yQYXfDG63WI)
- [Plutus study group 1 - (e)UTxO model a bit on Solidity how to proceed](https://www.youtube.com/watch?v=aKZxpf7bLFA)
- [Plutus: The Tokenomics](https://www.youtube.com/watch?v=wkj-VjWGo7c)
- [Plutuswap joins ecosystem of #Cardano #blockchain](https://www.youtube.com/watch?v=kavP7MSknrk)
- [Project Plutus #1: Setting up the repo basic design](https://www.youtube.com/watch?v=fobdtOdn5lY)
- [Project Plutus #2: Git setup + the basics](https://www.youtube.com/watch?v=qTS28R2udsI)
- [Cardano Plutus Pioneer Program: Lecture 3 Overview | Script Context & Homework](https://wwwyoutubecom/watch?v=TEFG0g6pa6M)
- [Cardano Plutus Pioneer Program: Lecture 4 Part 1 Overview](https://wwwyoutubecom/watch?v=bCLp8FgNacU)
- [Cardano Plutus Pioneer Program: Lecture 4 Part 1 Overview | Maybe Either and Writer w/ Monads](https://wwwyoutubecom/watch?v=NM8uqILIR0I)
- [Cardano Plutus Pioneer Program: Week 1 | UTxO & Homework Setup Instructions](https://wwwyoutubecom/watch?v=Cdu0gzCiYbY)
- [Cardano Plutus Pioneer Program: Week 2 Overview | Validation Scripts & Homework](https://wwwyoutubecom/watch?v=-fbHUjBcFU8)
- [Cardano Plutus Pioneer Program: Week 2 Overview | Validation Scripts & Homework](https://wwwyoutubecom/watch?v=Z9E5Fc5oPUE)
- [Cardano Plutus Pioneer: Week 05 - Homework 2 Recap](https://wwwyoutubecom/watch?v=Q-X5GuX-o_s)
- [Cardano Plutus Pioneer: Week01](https://wwwyoutubecom/watch?v=9bjaHsl4xwE)
- [Cardano Plutus Pioneer: Week021](https://wwwyoutubecom/watch?v=mBZOaePLHkU)
- [Cardano Plutus Pioneer: Week022](https://wwwyoutubecom/watch?v=AYCI3CszFX4)
- [Cardano Plutus Pioneer: Week03](https://wwwyoutubecom/watch?v=RRCiBQFCwnk)
- [Cardano Plutus Pioneer: Week04](https://wwwyoutubecom/watch?v=XWgzPPpwM40)
- [Cardano Plutus Pioneers Program Lesson 1 Homework on Debian using Window Hyper-V Virtualization](https://wwwyoutubecom/watch?v=i5X_i6HXIjg)
- [Cardano Plutus Project Starter Fix | Plutus Playground Smart Contracts + Haskell Explanation](https://wwwyoutubecom/watch?v=5lwOJmS5BsU)
- [Cardano Plutus Smart Contract Guessing Game Coding Tutorial](https://wwwyoutubecom/watch?v=wNXKiQanLTc)
- [Cardano Plutus Smart Contract Tutorial #2 | Endpoints and Validator Script Blockchain Development](https://wwwyoutubecom/watch?v=Sq4q-86LRis)
- [Cardano Plutus Smart Contract Workshop by Hassan Michael](https://wwwyoutubecom/watch?v=HoH__7mLA1w)
- [Cardano Plutus Tutorial #1: Hello World | Plutus Playground Smart Contracts + Haskell Explanation](https://wwwyoutubecom/watch?v=HtjOWAEzWL8)
- [Cardano Plutus Tutorial #3: Game Project | Smart Contracts DApp and Haskell Explanation](https://wwwyoutubecom/watch?v=1vTsPQpCcTE)
- [PPP 030101 - Welcome and Introduction](https://www.youtube.com/watch?v=X80uNXenWF4)
- [PPP 030102 - The EUTxO-Model](https://www.youtube.com/watch?v=bfofA4MM0QE)
- [PPP 030103 - Building the Example Code](https://www.youtube.com/watch?v=zPaDp4R9X7o)
- [PPP 030104 - Auction Contract in the EUTxO-Model](https://www.youtube.com/watch?v=Bj6bqRGT1L0)
- [PPP 030105 - Auction Contract on the Playground](https://www.youtube.com/watch?v=K61Si6iQ-Js)
- [PPP 030106 - Homework](https://www.youtube.com/watch?v=tfanOE2ARho)
- [PPP 030202   Low Level Untyped Validation Scripts](https://www.youtube.com/watch?v=xgnmMl-eIIM)
- [PPP 030203 - High Level Typed Validation Scripts](https://www.youtube.com/watch?v=HoB_PqeZPNc)
- [PPP 030204 - Summary](https://www.youtube.com/watch?v=V5P2gKHos48)
- [PPP 030205 - Homework](https://www.youtube.com/watch?v=_r-EpXzQGKo)
- [PPP 030301   Configuring Playground Time Out](https://www.youtube.com/watch?v=sLMhsqiWeGU)
- [PPP 030302   Script Contexts](https://www.youtube.com/watch?v=B66xLrGXwmw)
- [PPP 030303   Handling Time](https://www.youtube.com/watch?v=mf06ll-4j2w)
- [PPP 030304   A Vesting Example](https://www.youtube.com/watch?v=ae7U_yKIQ0Y)
- [PPP 030305   Parameterized Contracts](https://www.youtube.com/watch?v=XqFILXV_ACM)
- [PPP 030306   Deploying to the Cardano Testnet](https://www.youtube.com/watch?v=ABtffZPoUqU)
- [PPP 030307   Homework](https://www.youtube.com/watch?v=GGUT2O_0urQ)
- [PPP 030308   Summary](https://www.youtube.com/watch?v=uyaPtayBRb8)
- [PPP 030401 - Introduction](https://www.youtube.com/watch?v=gxMW9uXTEj4)
- [PPP 030402 - Monads](https://www.youtube.com/watch?v=f2w-MB3X4a0)
- [PPP 030403 - The EmulatorTrace Monad](https://www.youtube.com/watch?v=qoUfgaHs1CI)
- [PPP 030404   The Contract Monad](https://www.youtube.com/watch?v=yKX5Ce8Y0VQ)
- [PPP 030405   Homework & Summary](https://www.youtube.com/watch?v=sxRLzR0jdiY)
- [PPP 030502 - Values](https://www.youtube.com/watch?v=4iNTgjovMRg)
- [PPP 030503 - A Simple Minting Policy](https://www.youtube.com/watch?v=DBUdFsZpW7A)
- [PPP 030504 - A More Realistic Minting Policy](https://www.youtube.com/watch?v=4SROikF8JwE)
- [PPP 030505 - NFT's](https://www.youtube.com/watch?v=2lKN0ZL_EQU)
- [PPP 030506 - Homework](https://www.youtube.com/watch?v=j7yT2OqGY6U)
- [PPP 030601 - Introduction](https://www.youtube.com/watch?v=TfWKxdli4eI)
- [PPP 030602 - The Minting Policy](https://www.youtube.com/watch?v=w7_27sQIqkY)
- [PPP 030603 - Minting with the CLI](https://www.youtube.com/watch?v=kfvzrC9J02k)
- [PPP 030604 - Deployment Scenarios](https://www.youtube.com/watch?v=tW7uoY16gC0)
- [PPP 030605  - The Contracts](https://www.youtube.com/watch?v=JgNhY_uuuGA)
- [PPP 030606 - Minting with the PAB](https://www.youtube.com/watch?v=X6AyZIZ0vaE)
- [PPP 030607 - Summary](https://www.youtube.com/watch?v=KmNOFltlRiA)
- [PPP 030701 - Introduction](https://www.youtube.com/watch?v=CLOHdIGgy90)
- [PPP 030702 - Commit Schemes](https://www.youtube.com/watch?v=JXKf1JwVAOE)
- [PPP 030704 - State Machines](https://www.youtube.com/watch?v=7jiaQRA-wKI)
- [PPP 030705 - Homework](https://www.youtube.com/watch?v=J0rD_hmsMVo)
- [PPP 030801 - Introduction](https://www.youtube.com/watch?v=mqHifIPefus)
- [PPP 030802 - Another State Machine Example: Token Sale](https://www.youtube.com/watch?v=y5O58-NpnJ4)
- [PPP 030803 - Automatic Testing using Emulator Traces](https://www.youtube.com/watch?v=LG9O8YbBXyM)
- [PPP 030804 - Test Coverage](https://www.youtube.com/watch?v=wJQnQtLxi2E)
- [PPP 030805 - Interlude: Optics](https://www.youtube.com/watch?v=naLA0OMIF1Q)
- [PPP 030806   Property Based Testing with QuickCheck](https://www.youtube.com/watch?v=9mrYT9UXLO8)
- [PPP 030807 - Property Based Testing of Plutus Contracts](https://www.youtube.com/watch?v=49oAw.ySp6Ys)
- [PPP 030808 - Homework](https://www.youtube.com/watch?v=u2Plwc3Gkrs)
- [PPP 030901 - Introduction](https://www.youtube.com/watch?v=433VbouC-30)
- [PPP 030902 - Simon Thompson: Marlowe Overview](https://www.youtube.com/watch?v=ce_Yv8BlW7c)
- [PPP 030905 - Marlowe Playground Demo](https://www.youtube.com/watch?v=l0LXjh8J-go)
- [PPP 030906 - Homework](https://www.youtube.com/watch?v=iYdyUaq_enA)
- [PPP 031001 - Introduction](https://www.youtube.com/watch?v=AnID8hn68DA)
- [PPP 031002 - The Private Testnet](https://www.youtube.com/watch?v=xhEMEH0C2XU)
- [PPP 031003 - Plutus & Staking](https://www.youtube.com/watch?v=kFi-7HyBN-s)
- [PPP 031004 - Trying it on the Testnet](https://www.youtube.com/watch?v=5cBu4J5RRZ4)
- [PPP 031005 - Conclusion](https://www.youtube.com/watch?v=9oWmDXoxtmI)
- [Pioneer Demos Field360 Select Program](https://wwwyoutubecom/watch?v=0RRUBgjDT7k)
- [Pioneer Learning Lab - Aha Radio](https://wwwyoutubecom/watch?v=3dH87NsVaQs)
- [Pioneer Plays Festival - August 2022 : Old Skool Garage House Amapiano & Party Vibes #ukevents](https://wwwyoutubecom/shorts/ZQS3w78mGOQ)
- [Pioneer Program](https://wwwyoutubecom/watch?v=0bWQyi6Ijqo)
- [Pioneer Rekordbox   VIDEO 1Quantizeimport filesloop and hot cue](https://wwwyoutubecom/watch?v=lhqNHf0ywA8)
- [Pioneer takes a knock from maize deal](https://wwwyoutubecom/watch?v=1zf08yVhTOo)
- [Plutus Application set up](https://wwwyoutubecom/watch?v=nmgep-bUu6E)
- [Plutus Capitals testimonial](https://wwwyoutubecom/shorts/6mdFolzl5yI)
- [Plutus Development: Creating a Basic Smart Contract](https://wwwyoutubecom/watch?v=Q2SaoISFgRE)
- [Plutus explained: a secure smart contracting language from IOG](https://wwwyoutubecom/watch?v=3Z1ddDRvWGY)
- [Plutus Investment 2021 - Week 1](https://wwwyoutubecom/watch?v=Agj4OEIhxUk)
- [Plutus Nesting Visualized](https://wwwyoutubecom/watch?v=ZLURnogC_kU)
- [Plutus Pioneer - Alonzo Blue - First Cardano Smart Contracts in public Testnet](https://wwwyoutubecom/watch?v=XCrpxPj07gk)
- [Plutus Pioneer Capstone EMEA challenge](https://wwwyoutubecom/watch?v=afWjFIoCgA8)
- [#1 Reason Cardano Will Dominate Smart Contracts: Developer Adoption Strategy](https://wwwyoutubecom/watch?v=eWDTSSfNZ8g)
- [ADA - NEW ATH $244 - NEW Plutus Program and African Partners (NEW Book - Cryptionary)](https://wwwyoutubecom/watch?v=hdNvcJOPigs)
- [ADA Alonzo Smart Contract Timeline Breakdown! Uniswap Clone on Cardano? | Cardano360 Highlights!](https://wwwyoutubecom/watch?v=urs9EzaVjG0)
- [ADA Drops 50% In One Week Perfect Buying Opportunity](https://wwwyoutubecom/watch?v=b9qYEF5vVbo)
- [ADA I Bitboy Crypto: Cardano Will Go 100X In January!](https://wwwyoutubecom/watch?v=atEWezt7M-k)
- [ADA-Ethiopia deal D-Day and becoming a Plutus Pioneer - weekly recap!](https://wwwyoutubecom/watch?v=nfkJ1J4N7ms)
- [AdaPulse [Fund8] - DEMU is Decentralizing Music on Cardano Blockchain  First phase Jukebox dapp](https://wwwyoutubecom/watch?v=I5lCjHTyUFE)
- [Alonzo Orion Partnership NFTs on Cardano P2P and more!](https://wwwyoutubecom/watch?v=OYdvNOu-7VQ)
- [Alonzo roadmap ERC20 Converter Marlowe Plutus and more!](https://wwwyoutubecom/watch?v=av_-V7HdYAg)
- [Alonzo Updates ERC20 Converter Self Governance Bug Bounty so much more!](https://wwwyoutubecom/watch?v=JvfZm5MKEYc)
- [An Ethereum Developer's Take on Cardano's Plutus](https://wwwyoutubecom/watch?v=RQ6WuGGDeec)
- [An Introduction to what is utxo ? #shorts #crypto_glossary #utxo](https://wwwyoutubecom/shorts/39a6OpogVFU)
- [Atala PRISM - full demo](https://wwwyoutubecom/watch?v=wemcgPA3IPQ)
- [Atala PRISM: powering the trust economy and Acuant announcement](https://wwwyoutubecom/watch?v=yVL-AitXjTo)
- [Atala versus Cardano (Permissioned versus Permissionless)](https://wwwyoutubecom/watch?v=uZgDxPCXgPo)
- [Audio Podcast - EP018 - Combining traditional hedge fund with decentralised finance on Cardano](https://wwwyoutubecom/watch?v=Lbj4S0YBmWU)
- [Automated funding catalyst projects - Tien Nguyen Anh - Cardano2vn - Fund8 - Cardano Catalyst TV](https://wwwyoutubecom/watch?v=h8CL36HRTBU)
- [Binance dominance? Catalyst Fund4 - ADA on iTrust - Weekly Recap!](https://wwwyoutubecom/watch?v=2QClM8zqeF4)
- [Bootstrapping a DeFi Stack on Cardano](https://wwwyoutubecom/watch?v=8WIHlAai_Fc)
- [BREAKING!! Cardano Orion Partnership Occamfi Liquidity Mission Stakepools IOHK Delegation](https://wwwyoutubecom/watch?v=oP8MipQI7DA)
- [Build your Own Crypto !! - Plutus Pioneer](https://wwwyoutubecom/watch?v=ev1HLeHMuww)
- [Building A Smart Contract On Cardano - Marlowe Playground Example Walk-through Part 1](https://wwwyoutubecom/watch?v=UQK-o3BPy28)
- [Building DApps with Plutus](https://wwwyoutubecom/watch?v=2Hyl6WaWt5E)
- [Cardano - Stake Pool Diary 5: Building the Docker Image to the Raspberry Pi](https://wwwyoutubecom/watch?v=oh8nYbgBwMM)
- [Cardano - Πλήρης Αποκέντρωση Live Τετάρτη 31/03 21:00 ώρα Ελλάδος](https://wwwyoutubecom/watch?v=h7ShCthDsK8)
- [Cardano (ADA) Universe Getting Huge | Cardano Rumor Rundown #55](https://wwwyoutubecom/watch?v=xELk_H6OgFs)
- [Cardano 360 Mini - June 2021](https://wwwyoutubecom/watch?v=HjQkh9wTLu8)
- [Cardano 360 Mini July Edition](https://wwwyoutubecom/watch?v=KOOvGtGYoaQ)
- [CARDANO 360 MONTHLY RECAP & NEWS! (WATCH PARTY!)](https://wwwyoutubecom/watch?v=iFlwfka5Y44)
- [CARDANO Actualizaciones  - Obtén 50 Tokens Space Coins](https://wwwyoutubecom/watch?v=tSfO4_g8R3M)
- [Cardano Alonzo Ledger changes explained](https://wwwyoutubecom/watch?v=efQD8l8r4ug)
- [Cardano Catalyst TV - Fund7 - Cardano Technical hub in Vietnamese- Cardano2vnio - To Nguyen Duy Tan](https://wwwyoutubecom/watch?v=MZ4I-ea1suM)
- [Cardano Coffee lounge in Vietnam - Cardano2vnio - Fund8 - Cardano Catalyst TV](https://wwwyoutubecom/watch?v=SHcUhpdnX1Q)
- [Cardano Dapp Certification From Idea To Program](https://wwwyoutubecom/watch?v=GgNmJQSFNlM)
- [Cardano Ecosystem Update 12/28/21:SundaeSwap AuditWMT Arbitration and 175+ Protocols for ADA Q1 22](https://wwwyoutubecom/watch?v=gEEF2z-JC24)
- [Cardano Forest In Vietnam - Quoc ADAUP - Cardano Catalyst TV - Fund8](https://wwwyoutubecom/watch?v=HMJi1OwT6Fg)
- [Cardano Haskell Development Set Up in Visual Studio Code](https://wwwyoutubecom/watch?v=fuQi3sAJOA8)
- [CARDANO MASTER PLAN REVEALED: ETH IN TROUBLE!?](https://wwwyoutubecom/watch?v=wnNLST6CSpo)
- [Cardano NFT Maker - Patrick Tobler Founder & BABEL Stakepool Operator](https://wwwyoutubecom/watch?v=AfVtcCsPPlw)
- [Cardano Paper: A brief overview of The Extended UTXO Model](https://wwwyoutubecom/watch?v=Ro6s2fLYh7A)
- [Cardano Plutus Core V Ethereum VM](https://wwwyoutubecom/watch?v=cc6u-7QevGM)
- [Cardano Rumor Rundown #18: Learning Plutus/Haskell from Scratch?](https://wwwyoutubecom/watch?v=zQKHhkH_2c8)
- [Cardano Sense DC Fund show ep20 - Today: Plutus Docs Dapp Naming Service Deep Data Management](https://wwwyoutubecom/watch?v=zNuvCwS1IB4)
- [Cardano Starter Kit 007: Building Transactions on cardano-cli](https://wwwyoutubecom/watch?v=mkKRNA3TfyM)
- [Cardano Summit Plutus Pioneers Capstone PPC2021](https://wwwyoutubecom/watch?v=deUxZvxzNPA)
- [Cardano Technical Briefing: Plutus by John Woods](https://wwwyoutubecom/watch?v=zUerLu_GOQs)
- [Cardano Token Registry Process - CatalystFUND3 Episode3](https://wwwyoutubecom/watch?v=kiZ0HmNrpG0)
- [Cardano vs Ethereum Explained](https://wwwyoutubecom/watch?v=Wju_TFyqS6Y)
- [Cardano: Plutus Smart Contracts Explained (Deep Dive!)](https://wwwyoutubecom/watch?v=SvaFFSqyVwM)
- [Cardano's Plutus smart contract and Marlowe smart contract an overview of what the future holds](https://wwwyoutubecom/watch?v=R00xySyoBqw)
- [Cardano360 - August 2021](https://wwwyoutubecom/watch?v=baS9efSa2F8)
- [Cardano360 - December 2021 End of Year Edition](https://wwwyoutubecom/watch?v=mhfxSWrTrtI)
- [Cardano360 - January 2022](https://wwwyoutubecom/watch?v=yaa8Vys1Sms)
- [Cardano360 - July 2021](https://wwwyoutubecom/watch?v=AG5DspF9tuA)
- [Cardano360 - June 2021](https://wwwyoutubecom/watch?v=al5m14299ww)
- [Cardano360 March Mini (2021)](https://wwwyoutubecom/watch?v=OR72La6eQe4)
- [Cardano360 Mini - May 2021 Edition](https://wwwyoutubecom/watch?v=DkrzlLywi9Y)
- [Catalyst Challenge Setting Proposals for Fund 7 After Town Hall  August 25 2021](https://wwwyoutubecom/watch?v=iU8lSHQ0JAo)
- [Chapter2 lecture#2 JAVA](https://wwwyoutubecom/watch?v=m-luBBr9ZNQ)
- [Charles Hoskinson - Any regrets during Cardano development?](https://wwwyoutubecom/watch?v=C6EkOvrfMHc)
- [Charles Hoskinson on Plutus](https://wwwyoutubecom/watch?v=fNvZugWP0ow)
- [Charles Hoskinson on What is the Easiest to start developing on Cardano](https://wwwyoutubecom/watch?v=AIlwGlVEZJg)
- [Charles Hoskinson on Will there be another Plutus Pioneer Program starting soon](https://wwwyoutubecom/watch?v=lUTQ7kWvtXM)
- [Charli3 Oracle Solution Built on Cardano!](https://wwwyoutubecom/watch?v=3bCBxDxZ6A8)
- [Conversation with Lars Brunjes IOHK Director of Education and Maria Carmo and Keith from Lovelace](https://wwwyoutubecom/watch?v=7rgtZ6_MeAA)
- [CRYPTO CLASS: PLUTUS | NEW LISTING ON KUCOIN | PLUTON REWARDS EXPLORED | PLUTUS PERKS | BENEFITS](https://wwwyoutubecom/watch?v=C7NQRmLjdHE)
- [CRYPTO CLASS: PLUTUS | TOKENOMICS BREAKDOWN | PLUTON LEGEVITY | PLU DIFFERENCE | COMPANY BACKGROUND](https://wwwyoutubecom/watch?v=xgiVt6jEfJw)
- [Darkorbit/2021/ру123/Испытание Plutus](https://wwwyoutubecom/watch?v=pzp_9F-glXA)
- [Debugging and Working with UTXO's in Plutus](https://wwwyoutubecom/watch?v=uUhikJwPaQA)
- [Dev Talk 11-07-21 | Cardano Node Server on GCP](https://wwwyoutubecom/watch?v=ZByJYVDS9AA)
- [Dev's Experience with Plutus Pioneers Program | NFT-DAO Podcast #5](https://wwwyoutubecom/watch?v=W6765Q2dntc)
- [Driving Project Catalyst ATH 012622](https://wwwyoutubecom/watch?v=pK9ecNG910s)
- [EBU Plutus/Haskell  - In partnership with Cardano/IOHK](https://wwwyoutubecom/watch?v=qs0qK-4ErCE)
- [EP 218 | SUPERSPORT | BROADCASTING | DIRECTING | PRODUCING | PRESENTING | COMMENTARY](https://wwwyoutubecom/watch?v=VR5mTnBgGLQ)
- [EP004 - Non Fungible Tokens & Interview with Patrick Tobler from NTF-Makerio](https://wwwyoutubecom/watch?v=o8eowUHtaU0)
- [EP030 - DeFi Project Evaluations](https://wwwyoutubecom/watch?v=ufq1ivyVXyM)
- [Episode 9 - Restart the node in Block Producing mode - Raspberry PI Cardano Stake Pool Tutorial](https://wwwyoutubecom/watch?v=wXjuiHgqR0s)
- [Fireside Chat with Ben Hart - "Director of Operations - Cardano" at MLabs](https://wwwyoutubecom/watch?v=MuQV4_HQNx4)
- [Fireside Chat with Dr Lars Brünjes - Director of Education @IOHK](https://wwwyoutubecom/watch?v=rJF3y4BqHxU)
- [For the pioneer academics program](https://wwwyoutubecom/watch?v=xK0mOggdD3A)
- [Fred Gregaard CEO of the CF with Latest News and AMA | Cardano Live #14](https://wwwyoutubecom/watch?v=xbMSQUA1lss)
- [Functional smart contracts on Cardano](https://wwwyoutubecom/watch?v=MpWeg6Fg0t8)
- [GEMINI x CARDANO (ADA)?? ETH DEVS COMING TO CARDANO!! +MORE NEWS (Cardano Daily #53)](https://wwwyoutubecom/watch?v=URISHN7AMUY)
- [Gimbalabs Weekly Update #38](https://wwwyoutubecom/watch?v=puM7i9GcI34)
- [Goguen Alonzo Development Update - 14 May 2021](https://wwwyoutubecom/watch?v=5mPC4uLMdEw)
- [Haskell Course For Beginner/ Vietnamese - Quang Daniel - Fund8 - Cardano Catalyst TV](https://wwwyoutubecom/watch?v=mWvgegef6yc)
- [Haskell Plutus Marlowe | EP01 Introduction](https://wwwyoutubecom/watch?v=SarNhAgpaRM)
- [Hello Plutus! (A Plutus Playground Walkthrough)](https://wwwyoutubecom/watch?v=BiZNIB-oLQQ)
- [HOT CUES NOT LOADING PROBLEM FIXED | How to Auto load hot cues on Pioneer CDJs when loading a track](https://wwwyoutubecom/watch?v=1zCtyj4khFE)
- [HOW I DID RESEARCH IN HIGH SCHOOL + how to get a research internship ONLINE during COVID-19!!!](https://wwwyoutubecom/watch?v=0GJYe3YMfdY)
- [how i got involved in research as a high schooler](https://wwwyoutubecom/watch?v=7_CPlKViIm8)
- [how to buy @Pluta token using @Plutuswap](https://wwwyoutubecom/shorts/QdeMLCukJR0)
- [How to debug and rewrite the Gift Smart Contract for the new Plutus version on Cardano](https://wwwyoutubecom/watch?v=UbTOZWr1-yM)
- [How to Get Started Developing on Cardano!](https://wwwyoutubecom/watch?v=02C1HbcNvrk)
- [How to implement a Simple Escrow Contract With Plutus | Plutus Tutorial | Cardano Development](https://wwwyoutubecom/watch?v=RoR62b7gAKA)
- [How to thrive in the overwhelming ecosystem by Angela Plutus pioneer](https://wwwyoutubecom/watch?v=SwP9avf3FAw)
- [I've quit my job to become a cardano smart contract developer](https://wwwyoutubecom/watch?v=Ikk8fcO2k5c)
- [input-output-hk/plutus-pioneer-program - Gource visualisation](https://wwwyoutubecom/watch?v=wlriEWmg_cY)
- [Interview with Stevie Huh from Genesis Auction House CNFT Marketplace](https://wwwyoutubecom/watch?v=2PcK17RcBFM)
- [Introduction to Cardano Blockchain](https://wwwyoutubecom/watch?v=uWldFWS2g6Y)
- [Introduction to Smart Contracts Development on Cardano (Plutus Pioneer Program Week 1)](https://wwwyoutubecom/watch?v=kGs1gYDRrtQ)
- [IOHK PlutusFest 2018 | Manuel Chakravarty Keynote](https://wwwyoutubecom/watch?v=TFezjgwuw8Y)
- [Is Haskell/Plutus hard to learn?](https://wwwyoutubecom/watch?v=r1ohkcgbgH0)
- [Is it too late to buy ADA ? DEEP DIVE GOGUEN ERA CARDANO](https://wwwyoutubecom/watch?v=qvdXndJKnqk)
- [Kbit: what are Oracles and Cardano Chainlink partnership](https://wwwyoutubecom/watch?v=P0dlrKCbk9s)
- [Keynote: Building great products on Cardano](https://wwwyoutubecom/watch?v=9JeYZ6Rsl60)
- [Learn Haskell for Plutus (Cardano ADA Contracts) Day 1](https://wwwyoutubecom/watch?v=5b-YG558ft8)
- [Learn Haskell for Plutus (Cardano ADA Contracts) Day 2](https://wwwyoutubecom/watch?v=PivVZNNciDY)
- [Learn Haskell for Plutus (Cardano ADA Contracts) Day 4](https://wwwyoutubecom/watch?v=awXA9U0LBUI)
- [Learn Haskell for Plutus (Cardano ADA Contracts) Day 5](https://wwwyoutubecom/watch?v=2Yf2UXEMW8Y)
- [Lecture #1 | Instalación de Plutus](https://wwwyoutubecom/watch?v=a0YhSH1g-eE)
- [Lecture #2 | Datum Redeemer y Context](https://wwwyoutubecom/watch?v=21_GZ_3BeMg)
- [Lecture 1: Intro to the Plutus Course (Advanced Lambda Calculus Proofs and Types)](https://wwwyoutubecom/watch?v=D0URsi9E9H4)
- [Lecture 14 (Week 5)](https://wwwyoutubecom/watch?v=t5X4xGozsO0)
- [Legendado Maria e Keith Conversa com Lars Brünjes - Diretor Educacional da IOHK #cardano #ada #lars](https://wwwyoutubecom/watch?v=lg3povLKXl4)
- [Les modèles UTXO et EUTXO](https://wwwyoutubecom/watch?v=kyltXgKkEOQ)
- [Let's Begin the Cardano Plutus Pioneer Program 3rd Cohort Intro](https://wwwyoutubecom/watch?v=ih0htOSrnSI)
- [Let's play plutus on cardano! (part 1)](https://wwwyoutubecom/watch?v=-dghCJjaiwo)
- [Let's play plutus on cardano! (Part 2)](https://wwwyoutubecom/watch?v=3O5veSwfqj8)
- [Let's Talk About Cardano Plutus Pioneer Program Lecture 3 - Vesting Module [Week 3]](https://wwwyoutubecom/watch?v=6QIvVzSkfwE)
- [Let's Talk About Cardano Plutus Pioneer Program Lecture 4 - Monad Module [Week 4]](https://wwwyoutubecom/watch?v=x0Ftz9IwpH4)
- [Lobster Challenge: How to participate](https://wwwyoutubecom/watch?v=6xEAnMaov3E)
- [Marlowe Build a Smart Contract with a Drag & Drop Smart Contract Builder](https://wwwyoutubecom/watch?v=8aXn1QwzMaY)
- [Marlowe On Cardano Explained - May 2021](https://wwwyoutubecom/watch?v=vv2rJLN2Y1c)
- [May 2021 Cardano 360 review in 20 minutes](https://wwwyoutubecom/watch?v=mx4VmRWLauE)
- [Mini June 2021 Cardano 360 - that covers on all the key partnership news & technology updates](https://wwwyoutubecom/watch?v=KlShsFwtPt4)
- [Mini Proposal Workshop #7](https://wwwyoutubecom/watch?v=V_tBoLQWELw)
- [My first week of the Plutus Pioneer Program review [Week 1]](https://wwwyoutubecom/watch?v=DIIMy5Fb1SU)
- [My Plutus Development Experience in 2021: Problems and Why It Will Be Okay](https://wwwyoutubecom/watch?v=NSSbIMQaXM0)
- [New Coinbase Listing! Pluton - PLU - low market cap gem! #plu #pluton #crypto #lowmarketcap](https://wwwyoutubecom/shorts/si2RMBzaX3g)
- [P2P Haskell Tutorial 1 - The Basics and Your First Function](https://wwwyoutubecom/watch?v=Kupn9pW1lyE)
- [Programme supports tech driven solutions](https://wwwyoutubecom/watch?v=11XUp_hHOl4)
- [Project Catalyst - Weekly Town Hall](https://wwwyoutubecom/watch?v=Pw6VdcWi8NE)
- [Project Catalyst Fund5 weekly town hall and Q&A #9 May 2021](https://wwwyoutubecom/watch?v=kUS_VXa6zKk)
- [Quick-Fire Chat With Plutus CEO & Founder](https://wwwyoutubecom/watch?v=2dyjxb3ABZk)
- [Refactoring TokenSale endpoints](https://wwwyoutubecom/watch?v=LeMDZE60QhE)
- [Research with Professors for College Credit @ Pioneer Academics](https://wwwyoutubecom/watch?v=HnS2O8HAeXI)
- [Running Plutus on WSL - Create Cardano (ADA) Contracts on Windows 10](https://wwwyoutubecom/watch?v=mnfItts6VbU)
- [Scene from Aristophanes' Plutus (Western Tradition I)](https://wwwyoutubecom/watch?v=N7y49mZiL6s)
- [Shweta Chauhan | Cardano Plutus Pioneers Alonzo Testnet Goguen](https://wwwyoutubecom/watch?v=d5NXty5eLaQ)
- [Simple NFT Minter with Plutus & React | Plutus Tutorial | Cardano Development](https://wwwyoutubecom/watch?v=NBf8nezLIaU)
- [Smart contracts: the Plutus developer experience](https://wwwyoutubecom/watch?v=rZ0lHVTM2Hk)
- [Snapbrillia MVP Detailed Technical Plan - ATH - April 20th 2022](https://wwwyoutubecom/watch?v=zSSddSS2U_k)
- [Solidity Blockchain and Smart Contract Course – Beginner to Expert Python Tutorial](https://wwwyoutubecom/watch?v=M576WGiDBdQ)
- [STOIC Pool Update: Epoch 255 - Block Schedule Plutus Pioneers & (Almost) 1K](https://wwwyoutubecom/watch?v=p--syzr4DwY)
- [STOIC Pool Update: Epoch 256 - Upgrading The Pool & Learning Haskell](https://wwwyoutubecom/watch?v=nci5gfb9K6w)
- [Summer Programs in US | Everything you need | How to Apply](https://wwwyoutubecom/watch?v=Hp2Q-QcF5bA)
- [TADATek Insights - HungNhu - Fund8 - Cardano Catalyst TV](https://wwwyoutubecom/watch?v=7LtMcfuz3gk)
- [The Cardano Hereafter Party [Ep2] - Alonzo ERC20 Smart Contracts Elon Musk and crypto issues](https://wwwyoutubecom/watch?v=yT1c9pNG9Ag)
- [The Plutus platform](https://wwwyoutubecom/watch?v=usMPt8KpBeI)
- [The Plutus Platform - Cardano Virtual Summit 2020](https://wwwyoutubecom/watch?v=siwILkdBLWM)
- [The Power of Catalyst](https://wwwyoutubecom/watch?v=B1yWDINDnFI)
- [The Serious Cardano Issue](https://wwwyoutubecom/watch?v=eXYOF3RwAQg)
- [Townhall Channel in Vietnamese - ELPI - Fund8 - Cardano Catalyst TV](https://wwwyoutubecom/watch?v=NaHXYSriukw)
- [Validation in Cardano Plutus Scripts is this week's lesson Plutus Pioneer Program! [Week 2]](https://wwwyoutubecom/watch?v=QnXAqC9yxDI)
- [Want to learn Cardano Development? Start here](https://wwwyoutubecom/watch?v=7yf2jtny5uM)
- [Weis Wave with Speed Index Plutus Automated](https://wwwyoutubecom/watch?v=cb9fX2fK3b0)
- [Welcome to the Path to Plutus Channel](https://wwwyoutubecom/watch?v=Flgy2VkE1-g)
- [Where to get started in the Cardano Developer Ecosystem!](https://wwwyoutubecom/watch?v=AZXcrBx9dw4)
- [Why does the ERC-20 converter matter?](https://wwwyoutubecom/watch?v=SPcBZXIVXI8)
- [Why is Project Catalyst essential for Cardano? | EP11 | Understanding Cardano](https://wwwyoutubecom/watch?v=m8JnKTP8VNw)
- [Why Plutus?](https://wwwyoutubecom/watch?v=XoOXOKew-uY)
