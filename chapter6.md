# [CHAPTER 6] Sequential circuits, analysis and design
While the functionnality of a combinational circuit can be described using a truth table, a sequential circuit's output depends on the current inputs as well as the past inputs.
We can thus determine the output of a sequential circuit based on a combination of its present inputs and its **state**.
## Finite state machines
A **finite state machine** (FSM) is a computation model used to simulate sequential logic. We often use the term state machine as a synonym for sequential circuits. \
A state is defined by the combination of values of the states variables, the state is linked to the **flip-flops** contained in the circuit, one flip-flop contributes to one state variable. \
Each of the states is coded in binary values: to represent m states, m bits are required where n &ge; _log_<sub>2</sub>(m), each bit correspond to a **state variable**.

## State tables, diagrams and excitation equations.
In any sequential circuit, the part of the combinational circuit that generates the signals for the flip-flops, **computes the next state** is a set of Boolean functions called the _flip-flops input equations_ or the _excitations equations_.
**Convention** : to distinguish these equations and their effects, the dependent variable of the flip-flops input equations is represented by the flip-flop input symbol with the name of the flip-flop output as the subscript for the variable. \
Consider two flip-flops, the first one can either be in state A and !A and the second one in states B and !B both inputs are called D
- _D_<sub>A</sub> = _F_<sub>1</sub>(x, y, ..., z)
- _D_<sub>B</sub> = _F_<sub>2</sub>(x, y, ..., z)

State tables are tables that lists tbe relationships between inputs, outputs and flip-flops states of a sequential circuit.

<img src= ./images/chapter6/statetables.png width=400 />

They can also be represented more compactly : 

<img src= ./images/chapter6/statetablescompact.png width=400 />

Thus computation of the next state is equivalent to the excitations equations:
- _A_(t+1) = _D_<sub>A</sub> = _AX_ + _BX_
- _B_(t+1) = _D_<sub>B</sub> = _!AX_

And the output is a function of the inputs and the states. \
_Y_ = _A!X_ + _B!X_


## What is a Moore/Mealy state machine ?
### Moore state machines
A Moore state machine describes the output **only** as a function of the states : _output(t) = f(state(t))_ 

<img src= ./images/chapter6/mooremachine.png width=500 />

conventions in the **Moore machines** states that:
- The directed edges in the graph are labelled with the **G/H** pair (in binary)
  - **G** is the input value during the present state.
  - **H** is the expected output during the present state with the given input applied.
- A directed edge connecting a vertex with itself indicates that no changes occurs.

### Mealy states machines
A Mealy state machine describes the output as a function of **both** the states and the inputs : _output(t) = f(states(t), inputs(t))_

<img src= ./images/chapter6/mealymachine.png width=500 />

conventions in the **Mealy machines** states that:
- The "/" in the directed edges isn't included because the output depends only on the state and not the input values, instead, the output is now included after a "/" following the state in a vertex.
- There are two input conditions for each state transition and they're separated by a comma. 

## What are equivalent states ? 

## What are race conditions ? How to detect them ?

## What is the internal state of a sequential circuit
## Name different ways of assigning the states of a system to n variables 
## Analyse a given sequential circuit or design 
