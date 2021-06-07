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

## SR and D-latches
The lacth is an **asynchronous** memory circuit, it uses logic gates and a feedback loop.
### SR-latch 
It is formed by 2 cross-coupled NOR gates its states are defined by outputs **Q** and **!Q** and are:
- the set state **Q** = 1, **!Q** = 0.
- the reset state **Q** = 0, **!Q** = 1.
The inputs **S** (set) and **R** (reset) bring the system in set and reset states. \
The SR-latch circuit and truth table are:

<img src= ./images/chapter4/SRlatch.png width=400 />

Since the SR-latch is asynchronous and can update at any instant, if **S** and **R** are set simultaneously (within recovery time of each other (5ns), defined in datasheet) Q and !Q are both set to 0 and the latch enters the undefined state, which later lead to either metastability or oscillation when **S** and **R** eventually return to 0. \

This calls the need for a synchronous type of latch called the **D-latch**

### D-latch
The D-latch imposes different values for **S** and **R** using an inverter, also, changes in **S** and **R** are taken into account only if they are synchronized with a **C** clock signal. \
- **C** = 1, **D** = 1 is equivalent to **S** = 1 in SR-latch.
- **C** = 1, **D** = 0 is equivalent to **R** = 1 in SR-latch.
- **C** = 0 maintains previous state.

The D-latch circuit and truth table are : 

<img src= ./images/chapter4/Dlatch.png width=450 />

However, the D-latch can still become metastable if changes in **D** occurs in the falling edge of **C**.

<img src= ./images/chapter4/Dlatch1.png width=450 />

## What is the main difference between a latch and a flip flop ?
Even controlled by a clock, latches stay asynchronous, meaning that during **C**, they will follow their input change and can lead to unwanted states, it a transparency issue, as soon as an input change, the output change to match it, ideally one state change is allowed by clock pulse. \
The **flip-flop** is a purely synchronous basic memory cell, the difference between a latch and a flip-flop is that latches operate with signal levels and flip-flops are controlled by a clock transition.

flip-flops are usually built by connecting two latches in a _master-slave_ configuration.
### What is the advantage of a flip-flop over a latch ?

### What is a master-slave flip-flop ? 

### What is an edge-triggered flip-flop ?
The state change is triggered by the positive or negative edge of the clock (from 0 to 1 or from 1 to 0).
### What is a pulse-triggered flip-flop ?
The change of state is triggered the value of the clock.

## SR pulse-triggered and D edge-triggered flip-flops
### SR pulse-triggered flip-flop

Two clocked SR-latch are connected in cascade the clock is inverted for the second latch, the first latch is the master, the second is the slave.
- When the clock signal is **ON**
  - the master latch is in **transparent** mode, meaning it will directly react to its inputs
  - the input from master latch is observed and passed to the output Y
  - the slave latch is in **memorizing** mode, meaning the previous state is memorized and output **Y** (the new state) cannot pass to the slave latch
- When the clock signal is **OFF**
  - the master latch is in **memorizing** mode, any change in **S** and **R** will not be observed in **Y**.
  - the slave latch is in transparent mode, meaning it will react to the signal in **Y**.

<img src = ./images/chapter4/SRflipflop.png width=400 />

#### The ones catching issue
Like said above, the expected behavior of a SR flip-flop is that **Q** corresponds to the input values at the time of the trigger (which is, in that case, the falling edge of the clock). \
If **S** or **R** briefly pulses (during a shorter time than one clock pulse), the master will catch a signal and transmit it to the output which is not correponding to the input at trigger time (at the falling edge) of the clock, which violates the intended behavior of the flip-flop. \

<img src= ./images/chapter4/onescatching.png width=350 />

### D edge-triggered flip-flop
Edge-triggered flip-flops are triggered either by the **rising** or **falling** edge of the clock, solving the ones catching issue. \
they're built by using a D-latch instead of an SR-latch as master.
#### Positive edge-triggered
Change in state occurs at the rising edge of the clock.

<img src= ./images/chapter4/positiveedge.png width=400 />


#### Negative edge-triggered
Change in state occurs at the falling edge of the clock 

<img src= ./images/chapter4/negativeedge.png width=400 />

## JK and T flip-flops
### JK flip-flops
The JK flip-flop is analogous to the SR pulse-triggered flip-flop except that we allow the configuration **J** = **K** = 1 by returning a complemented state. \
JK flip-flop circuit and truth table: 

<img src= ./images/chapter4/jkflipflop.png width=400 />

### T flip-flops
**T** = 0 &rarr; no change in state. \
**T** = 1 &rarr; change to complemented state. \

T flip circuit and truth table: 

<img src= ./images/chapter4/tflipflop.png width=400 />




