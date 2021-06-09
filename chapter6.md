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

<img src= ./images/chapter6/moorefsm.png width = 400/>

### Mealy states machines
A Mealy state machine describes the output as a function of **both** the states and the inputs : _output(t) = f(states(t), inputs(t))_

<img src= ./images/chapter6/mealymachine.png width=500 />

conventions in the **Mealy machines** states that:
- The "/" in the directed edges isn't included because the output depends only on the state and not the input values, instead, the output is now included after a "/" following the state in a vertex.
- There are two input conditions for each state transition and they're separated by a comma. 

<img src= ./images/chapter6/mealyfsm.png width = 300 />

## What are equivalent states ? 
Two states are equivalent if their response for each possible input sequence result in an identical output sequence.
In this graph, states 2 and 3 (10 and 11) are identical since they have the same output for the same inputs and identical next state.

<img src= ./images/chapter6/mealyfsm.png width = 300 />

Thus S2 and S3 are merged in a new state S'2 

<img src= ./images/chapter6/merge1.png width = 200 />

Since S'2 and S1 are equivalent we merge them in a new state S'1 

<img src= ./images/chapter6/merge2.png width = 200 />

Finally, 2 states remain, meaning the system can be implemented using only one bit (one flip-flop).

Some systems combine Moore and Mealy representations, if in some state, the output does not depend on the input (only on the state) we remove it and include it in the state vertex (similar to a Moor model).

## Name different ways of assigning the states of a system to n variables
For a sequential system with **m** states must be assigned a unique binary code, the minimum number of bits (n) required is such that n &ge; ceiling(_log_<sub>2</sub> m)
A state assignment with the minimum numbers of bits provides a system with the minimum number of flip flops, however it doesn't always provide the circuit with the minimum **cost** as the cost of the combinational circuit also needs to be taken into account.

For n bits, there are 2<sup>n</sup>! possible assignments, the simplest states doesn't always generate the simplest circuit.
Some guidelines are used by designer to find fitting assignments:
- minimize the number of state variable that change on each transition
- maximize the number of state variables that do not change in a group of related states
- decompose the set of state variable into individual bits

And some popular state assignments
- Binary coded in counting order
- Gray assignment 
- One-hot assignment (0001, 0010, 0100, 1000)
- Almost one-hot assignment (0000, 0001, 0010, 0100, 1000)

For example, the assignment using binary code is the following : 


<img src= ./images/chapter6/assignment1.png width = 500 />

With Karnaugh map optimization, we find the following excitation equations
- _Y_<sub>1</sub>(t + 1) = _Y_<sub>1</sub>!_Y_<sub>0</sub> + !_Y_<sub>1</sub>_Y_<sub>0</sub>_X_ 
- _Y_<sub>0</sub>(t + 1) = _Y_<sub>1</sub>!_Y_<sub>0</sub>!_X_ + !_Y_<sub>1</sub>!_Y_<sub>0</sub>_X_ + _Y_<sub>1</sub>_Y_<sub>0</sub>_X_
- _Z_(t) = _Y_<sub>1</sub>_Y_<sub>0</sub>_X_

While the use of a gray code assignment would lead to the excitation equations : 
- _Y_<sub>1</sub>(t + 1) = _Y_<sub>1</sub>_Y_<sub>0</sub> + _Y_<sub>0</sub>_X_ 
- _Y_<sub>0</sub>(t + 1) = _X_
- _Z_(t) = _Y_<sub>1</sub>!_Y_<sub>0</sub>_X_

## What are race conditions ?
Race conditions are uncertain behaviors which is dependent which is dependent on the speed of gates, a race condition occurs when the output of a system depends on a specific execution.

