# CHAPTER 2

## Analog and digital systems
To reprensent information, we use signals from the real world, which are all continuous.

### What makes a digital system different from an analog system ?
- An analog signal is a signal whose amplitude is **continuous** as a function of time.
- A digital signal is a signal whose amplitude is **discrete**.
-
### What is the noise margin of a logic gate ?
The noise margin is a concept used when trying to convert a real world analog signal to a digital one.
We will define tresholds that will determine wether the difference in signal value is intended or noise.
The noise margins in voltage ranges are can be interpreted as follows:
- Any potential below 0.8V is interpreted as a binary **0**.
- Any potential above 2V is interpreted as a binary **1**.

## What is the difference between asynchronous and synchronous circuits ?
If we consider a clock that ticks at some frequence, we can distinguish an asynchronous signal from a synchronous one.
- An asynchronous signal is a signal whose value update regardless of the synchonization imposed by the clock.
- A synchronous signal is a signal that updates each time the clocks ticks, the signal is synchronized with the clock.
The difference between an asynchronous **circuit** and a synchronous one is similar, a synchronous circuit follows a clock signal while an asynchronous one doesn't.

## What is the difference between combinational and sequential circuits ?
A combinational system circuit is a circuit that:
- Does not have internal states (memory)
- The output is a **function** of the input (no side-effects due to memory).

A sequential circuit is a circuit that:
- Have internal states and the output of the system depends on the previous inputs.
Thus sequential systems need to be updated, they are either at:
- Certain, periodic discrete times, they are **synchronous** (or clocked) systems, thus the output at time **T**:\
  `output(T) = function(internal_states(T-1), inputs(T-1))`
- Any instant in time, they are **asynchronous**\
  `output(T) = function(input(t), internal_states(T))`

## What are positional/nonpositional number systems
- **Positional number systems** reprensent numbers as a string of digits and a `.` called the radix point.
The radix point distinguishes the integer portion from the fraction portion of the number.
The value of the number is then : (Integer portion) + (Fraction portion), and the value of each portion is the weighted sum of the digits.

- **Non-positional number systems** are systems in which the placement of a digit does not change its value (e.g Roman numerals).
## What's the parity bit ?
In a binary reprensented number, the parity bit is the least significant bit, it defines whether the number is even or odd.
## What are BCD code and Gray code ?



