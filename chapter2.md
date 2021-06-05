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
Adding a **parity bit** is a method used to detect error in communication/data processing, it's an additional bit added in the end of a binary string to indicate
whether the number of **1s** in the binary representation is odd or even.
- With __even parity__ we set the parity bit to **1** if the number of **1s** in the original string is **odd**, we make it even. \
  1000001 -> 0 1000001. (parity bit is MSB).
- With __odd parity__  we set the parity bit to **1** if the number of **1s** in the original string is **even**, we make it odd. \
  1000001 -> 1 1000001. (parity bit is MSB).

## What are BCD code and Gray code ?
### A bit about coding
Coding elements of a set means to represent them in another way, we can define a n-bit binary code as : \
__A group of n bits that assume 2 to the power of n combinations of 0s and 1s which each combination represent one element of the set being coded__\
The minimum number (n) of bits needed to encode a set of **M** elements is: \
**n** = log **M**.

The difference between conversion and coding:
- Coding 13 -> 0001 | 0011
- Converting 13 -> 1101

### BCD

**BCD** code or __binary-coded decimal__ is the code most commonly used for decimal digis, its the straight forward binary assignment.

i.e BCD Code is used in 7-segment decoder, each digit can be treated as a separate signal/circuits.
### Gray code
The **Gray code** tries to make the change from the number **i** to **i+1** by only changing a single bit.
The representation of decimal digits in **Gray code** is then:
|   |    |
|---|----|
| 0 |0000|
| 1 |0001|
| 2 |0011|
| 3 |0010|
| 4 |0110|
| 5 |0111|
| 6 |0101|
| 7 |0100|
| 8 |1100|
| 9 |1101|



