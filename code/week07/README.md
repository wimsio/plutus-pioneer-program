# Week 07 Notes

This notes follow the seventh lecture from [Lars YouTube](https://www.youtube.com/watch?v=oJupInqvJUI&t=839s). 

The main topics of this lecture is to introduce state machines for us to see how powerful and convenient they can be. This is exemplified in this lecture's app: a simple binary game:

Alice & Bob are playing a binary choice game, if both choose the same number then Alice wins and otherwise Bob wins.

When Alice chooses a number ([0,1] + nonce) hashes her chooice and sends it to Bob. Then Bob knows the hash but does not know Alice's choice so he can not cheat. Then Bob makes his choice [0.1] and sends it raw to Alice, at this point Alice already knows if she has won/lost but to prevent her from cheating now she sends her raw choice ([0,1] + nonce). Finally Bob checks that the hash of it matches the initial hashed message. 

| Action | Alice | Bob |
| --- | --- | --- |
| A turn | hash(choice ++ nonce) | waits |
| B turn | waits | choice |
| A confirms | (choice ++ nonce) | verifies hash |
| result | win/loose | win/loose |

## 1. [`EvenOdd.hs`](https://github.com/input-output-hk/plutus-pioneer-program/blob/first-iteration/code/week07/src/Week07/EvenOdd.hs)

The first implementation of the game is a bit verbose, it only makes use of Plutus and Haskell functions and follows the raw logic.

- `data Game` -> type that contains information about the steps of the game (much like the table above) plus it adds varaibles for deadlines.
- `data GameDatum` -> type that concatenates a bytestring 

## State Machines

A state machine is basically a system that reacts to inputs by transitioning to other states, it is represented as a directed graph which transitions state. Eg. in our diagram for the Alice/Bob game all the nodes (boxes) represent states and the arrows are the transitions.

```
             ______              __________
--Alice-->  | Hasb |  --Bob-->  | hasb, cb |----------|
            |______|    play    |__________|          |
                  \                   |               |
                   \                  |           Bob | claim
              Alice \ claim     Alice | reveal        |
                     \                |               /
                      \               v              /
                       \        _____________       /
                        \--->  | Final state |  <--/
                               |_____________|

```                               

---
**key idea:**
In particular in the Blockchain, the state machine will be represented by UTXOs sitting at the state machine script address and the state will be the datum of the UTXO and the transition will be a trasaction that consumes the current state/(datum of UTXO) using a redeemer that characterizes the transition and produces a new UTXO at the same address where the datum reflects the new state.
---

More information on State Machines in Plutus can be found in the [`Plutus.Contract.StateMachine`](https://github.com/input-output-hk/plutus/blob/master/plutus-contract/src/Plutus/Contract/StateMachine.hs) module. Were a quick snippet inputs

```haskell
data StateMachine s i 
```
Specification of a state machine consisting of a transition function that determines the next state from the current state and an input, and a checking function that checks the validity of the transition in the context of the current transaction.
*Constructors*
`StateMachine`
| def | description |
| --- | --- |
|`smTransition :: State s -> i -> Maybe (TxConstraints Void Void, State s)` | The transition function of the state machine. `Nothing` indicates an invalid transition from the current state |
| `smFinal :: s -> Bool` | Check whether a state is the final state |
| `smCheck :: s -> i -> ScriptContext -> Bool` | The condition checking function. Can be used to perform checks on the pending transaction that aren't covered by the constraints. `smCheck` is always run in addition to checking the constraints, so the default implementation always returns true |
| `smThreadToken :: Maybe AssetClass` | The `AssetClass` of the thread token that identifies the contract instance |



## 2. [`StateMachine.hs`](https://playground.plutus.iohkdev.io/tutorial/haddock/plutus-contract/html/Language-Plutus-Contract-StateMachine.html)

This is the implementation of the same `EvenOdd.hs` game but now using state machines. 
