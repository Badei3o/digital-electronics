# [CHAPTER 4] SEQUENTIAL LOGIC CIRCUITS: Latches and flip-flops

## What is a sequential circuit ?
As opposed to a **combinational** circuits whose output values only depends on its inputs' values, a **sequential** circuit's output depends on **current and prior inputs** (memory).
A sequential circuit is formed by interconnecting combinational circuits and **storage elements** that stores binary information
We can specify a sequential circuit as a time sequence of inputs, eternal states and outputs.

### Differences between synchronous and asynchronous sequential circuits
In asynchronous sequential systems:
- The behavior is defined from knowledge of inputs at any time instant and the order in which inputs change.
- change in state occur at any time instant.

In synchronous sequential systems:
- The behavior is defined from knowledge of all inputs at the same discrete time instants
- changes in state occur at these specific discrete times.
- synchronization is achieved by a clock generator producing clock pulses, state changes only occurs at a tick of the signal.

## What is a bitstable SRAM cell ?
We can observe that any gate with the delay _t_<sub>G</sub> that doesn't apply any function (used as a buffer), holds the information of the input for the duration _t_<sub>G</sub>.
We can use this observation and a feedback mechanism to hold the information for an unlimited time.

<img src= ./images/chapter4/cell1.png width=200 />
This circuit is bitstable, it has 2 stable operating points (Q = 0, Q = 1), for this circuit to be stable, there must be no inversion of the signal in the loop. \
The bitstable circuit has no inputs, when power is applied to the circuit, it randomly comes up in one state or the other. \

We could load a new value in the memory cell by briefly breaking the feedback path and loading a new value.

<img src= ./images/chapter4/ram1.png width=400 />

A practical application of this circuit is an SRAM cell or a "bus driver".

### Where are the equilibrium points and the metastable point ?

We can observe that a contraption of this kind can stay in **3 equilibrium states** depending on the possible voltages of _V_<sub>in1</sub>, _V_<sub>in2</sub>, _V_<sub>out1</sub> and _V_<sub>out2</sub>. \

<img src= ./images/chapter4/equilibrium.png width=400 />

The 3 equilibrium states that we can distinguish are at the intersection of the red and black curves. \
In theses states, we say that the loop is **stable**
- _V_<sub>in1</sub> = 0V, _V_<sub>out1</sub> = 3V, _V_<sub>out2</sub> = 0 = _V_<sub>in1</sub>
- _V_<sub>in1</sub> = 3V, _V_<sub>out1</sub> = 0V, _V_<sub>out2</sub> = 3 = _V_<sub>in1</sub>
And they represent the intersection at the "extremities" of the graph. \
The third intersection point is called the **metastable point** and it should be avoided to operate in. 
Like the graph suggests, the smallest amount of voltage change will make the circuit switch in one of the other stable equilibrium states, random noise could trigger such a behavior and would make the circuit nearly impossible to predict.

## SR and D latches
The lacth is an **asynchronous** memory circuit, it uses logic gates and a feedback loop.
### SR latch 
It is formed by 2 cross-coupled NOR gates its states are defined by outputs **Q** and **!Q** and are:
- the set state **Q** = 1, **!Q** = 0.
- the reset state **Q** = 0, **!Q** = 1.
The inputs **S** (set) and **R** (reset) bring the system in set and reset states. \
The SR latch circuit and truth table are:

<img src= ./images/chapter4/SRlatch.png width=400 />




## SR pulse-triggered and D edge-triggered flip-flops
### Circuits
### Truth tables
### Timing diagrams

## What is the main difference between a latch and a flip flop ?
### What is the advantage of a flip-flop over a latch ?
### What is a master-slave flip-flop ? 
### What is an edge-triggered flip-flop ?
### What is a pulse-triggered flip-flop ?
### What is the first catching problem in pulse-triggered SR flip-flops ? 

## How can a T flip-flop be realized from a D flip-flop and logic gates ?

## Give the truth table of a T and JK flip-flop/latch


