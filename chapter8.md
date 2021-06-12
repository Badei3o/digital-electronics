# [CHAPTER 8] Registers and Counters
## What is a register ?
A **n** bit register is a set of **n** flip-flops with additional combinational gates that implement their state transitions.
A register is used to 
- store a vector of binary values 
- perform shift of binary words

There is three main types of registers 
### Storage register
The clock input triggers all flip-flops, at that time, the binary information available in the 4 D inputs is transferred in the 4 bits register.
The 4 Q outputs can be read at any time to read the information stored in the register.

<img src= ./images/chapter8/storageregister.png width = 600 />

The transfer of new information into a register is reffered as "loading the register" and is controlled by a **Load** signal that inderictly control the clock ticks at which the flip-flops react.
_C_<sub>inputs</sub> = !_Load_ + _Clock_

- If **Load** = 1, _C_<sub>inputs</sub> = _Clock_, the register is clocked normally. 
- If **Load** = 0, _C_<sub>inputs</sub> = 1, the register is clocked normally with constant input, no pulse nor edge, the contents remain unchanged.

The previous technique is called block gating could lead to a problem of **clock skew**.
A more reliable solution would consider a register as a set of cell consisting of D flip-flops with an ENABLE signal and a 2-to-1 multiplexer
- For EN = 0, values are stored in the register.
- For EN = 1, input values are loaded into the register.

<img src= ./images/chapter8/FFenable.png width = 400 />

Thus each cell are connected to the same **EN** signal

<img src= ./images/chapter8/FFenable1.png width = 200 />

### Shift register
A shift register is a register made of a chain of flip-flops, its purpose is to move the data laterally within the register towards the MSB or LSB, all flips-flops have a common clock-pulse that activates the shift.

<img src= ./images/chapter8/shiftregister.png width = 600 />

- The data input is called the **serial input**.
- The vector _Q_<sub>1</sub>, _Q_<sub>2</sub>, ..., _Q_<sub>n</sub> is called the **parallel output**.
- The data output _Q_<sub>n</sub> is the **serial output**.
- At each clock pulse, the serial input **SI** is placed at MSB, bits from _1_ to _n-1_ are shifted one position to the right, the **serial output** is shifted out of the register.

The data can also be moved to the left using the following circuit:
<img src= ./images/chapter8/shiftregister1.png width = 600 />

- The serial output is _Q_<sub>1</sub>.
- At each clock pulse, the serial input is moved to LSB.
- Bits _2_ to _n_ are moved one position left.
- Serial output is removed from the register.

With a bit more circuitry, we can design a shift register with a parallel load, the ability to change the states of the flip-flops within the register.

<img src= ./images/chapter8/shiftregister2.png width = 400 />

- If **SHIFT** = 0, _D_<sub>A</sub> and _D_<sub>B</sub> are loaded and replace A and B.
- If **SHIFT** = 1, The previously loaded data is shifted one posistion to the right.

### General register
By placing a 4-input multiplexer in front of each D flip-flop, we can implement a circuit that is able to perform the 4 operations discussed above (shift left/right, load, hold).

<img src= ./images/chapter8/generalregister.png width = 600 />

## What is a counter ? 
A counter is a sequential circuit that goes through a **prescribed sequence** of states upon the application of successive clock pulses (or pulses from another source),
it is made of a set of n flip-flops, and follows the binary number sequence (can count from 0 to 2<sup>n</sup> - 1).

## What is a ripple counter ?
A ripple counter is asynchronous, the flip-flops output transitions are used as the sources of triggering changes in other flip-flops.
As an example of how it works, the circuit of a 1 bit ripple counter and its behavior over time.


<img src= ./images/chapter8/1bitcounter.png width = 400 />

Whenever there is a positive edge on the clock, the output A is complemented (since D is linked to Q*, its complement), the counter thus forms a sequence of 0&rarr; 1&rarr;0&rarr;1&rarr;0&rarr;1&rarr;0&rarr;1, it is a binary modulo-2 counter.

Whe can build a **ripple counter** by connecting n cells of 1 bit counters, the output of cell _i_ is connected to the clock input of cell _i+1_ 

<img src= ./images/chapter8/4bitcounter.png width = 200 />

## What is a synchronous counter ?
All the flip-flops in a synchronous counter use a common clock signal.

## How do you initialize a counter ?

