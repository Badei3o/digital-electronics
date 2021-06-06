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

### Where are the equilibrium points and the metastable point ?
### What is metastability

## SR and D latches
### Circuits
### Truth tables
### Timing diagrams

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


