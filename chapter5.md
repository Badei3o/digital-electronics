# [CHAPTER 5] Combinational Logic Design: Functional Blocks and Arithmetic Functions
## What is a decoder ?
Decoding is the conversion of a **n** bit input code to a **m** bit output code knowing that n &le; m &le; 2<sup>n</sup>
We can build any decoder using the basic 1-to-2 decoder and **AND** gates, for example, a 2-to-4 decode is build upon 2 1-to-2 and 4 AND gates.

<img src= ./images/chapter5/decoders.png width=600 />

For a decoder of **n** inputs and 2<sup>n</sup> outputs we use a hierarchical design
- let **k** = n
- if **k** is even use 2<sup>k</sup> AND gates driven by 2 decoders of output 2<sup>k/2</sup>.
- if **k** is odd use 2<sup>k</sup> AND gates driven by a decoder of output 2<sup>(k+1)/2</sup> and one of output 2<sup>(k-1)/2</sup>.
- if **k** = 1, use a 1-to-2 decoder. 

Example with a 3-to-8 decoder:\
**First split**
- k = 3
- k is odd &rarr; 8 AND gates driven by one 2-to-4 decoder and one 1-to-2.
**Second split**
- k = 2
- k is even &rarr; 4 AND gates driven by two 1-to-2 decoders

The final schematics:

<img src= ./images/chapter5/3to8.png width=500 />

## What is an encoder ?
Encoding is the oposite of decoding, it's the conversion of a **m** bit input code to a **n** bit output code knowing that n &le; m &le; 2<sup>n</sup> and such that each valid code word produces a unique output code. \
An encoder is a circuit that performs encoding, here is an example of an octal to binary encoder:
<img src= ./images/chapter5/octaltobinary.png width=500 />

Based on the truth table we can set an equation for **A**<sub>j</sub>, **A**<sub>j</sub> is the sum of all **D**<sub>i</sub> for i the index at which **A**<sub>j</sub> is true in the truth table. \
- **A**<sub>0</sub> = **D**<sub>1</sub> + **D**<sub>3</sub> + **D**<sub>5</sub> + **D**<sub>7</sub>
- **A**<sub>1</sub> = **D**<sub>2</sub> + **D**<sub>3</sub> + **D**<sub>6</sub> + **D**<sub>7</sub>
- **A**<sub>2</sub> = **D**<sub>4</sub> + **D**<sub>5</sub> + **D**<sub>6</sub> + **D**<sub>7</sub>
 
However, ambiguities are present in this model, only one input can be on at any time otherwise the encoder produces an incorrect combination (take for example is inputs **D**<sub>3</sub> and **D**<sub>6</sub> are on, the code is 111). \
### Priority encoder
A priority encoder solves the ambiguity problem by using don't care values and a priority function, of all the inputs that are on at any time, the encoder selects the most significant input postition and and responds with the corresponding binary code for that position. \
<img src= ./images/chapter5/priorityencoder.png width=500 />

**V** is true if the output of the encoding contains a **1**, if **V** is false, we ignore the output, the input with the highest priority is the most significant one (?????).

With **Karnaugh maps** manipulations, we can deduct the following boolean equations for the 4-to-2 encoder
- **A**<sub>0</sub> = **D**<sub>3</sub> + **D**<sub>1</sub> !**D**<sub>2</sub>
- **A**<sub>1</sub> = **D**<sub>2</sub> + **A**<sub>3</sub>
- **V** = **D**<sub>0</sub> + **D**<sub>1</sub> + **D**<sub>2</sub> + **D**<sub>3</sub>

Hence the circuit:
<img src= ./images/chapter5/encodercircuit.png width=500 />


## What is a multiplexer ?
A multiplexer is a circuit that performs **selecting**, which is the process of raccording the inputs of a circuit in function of a set of **selecting** inputs.
A typical multiplexer:
- has a set of **n** control inputs called **selection inputs** (_S_<sub>n-1</sub>, ..., _S_<sub>0</sub>)
- has a set of 2<sup>n-1 </sup> **information inputs** (_D_<sub>2<sup>n-1</sup></sub>, ..., _D_<sub>0</sub>)
- an output **Y**.
Multiplexer can be seen as individual switches that are controlled by a decoder.

The desing of a 2-to-1 multiplexer is the following:
- 2-to-1 means a set of 2 **information input** (_I_<sub>0</sub>, _I_<sub>1</sub>) and thus a set of _log_<sub>2</sub> 2<sup>1</sup> = 1 **selection input** (_S_). \
The truth table and circuit: 

<img src= ./images/chapter5/2to1multiplexer.png width=500 />

Like said above, a multiplexer can be broken down to a decoder(s), enabling circuits and OR gates, for a 2-to-1:
- 1-to-2 decoder
- 2 enabling circuits
- 1 two inputs OR gate

<img src= ./images/chapter5/2to1multiplexer1.png width=600 />

Now for any **2<sup>n</sup>** multiplexer and n > 1 selecting inputs:
- a n-to-2<sup>n</sup> decoder generating the minterms m<sub>i</sub>
- a 2<sup>n</sup> x 2 AND-OR circuit combining the enabling circuits (ANDs) and the OR gate.
  
e. g for n = 2 :

<img src= ./images/chapter5/2tonmultiplexer.png width=600 />

## What is a half-adder/full adder ?
### Half adder
A half adder is a 2-input 2-output functional block that performs the addition of the two input bits.
<img src= ./images/chapter5/halfadder.png width = 400 />


### Full adder
A full adder is a 3-input, 2-output functional block that performs the addition of the three input bits in addition of a third carry input bit obtained from a previous adder

<img src= ./images/chapter5/fulladder.png width = 500 />

On the logical diagram we can observe that a full adder consists of 2 half adders.

<img src= ./images/chapter5/fulladderdiagram.png width = 500 />


## What are ripple carry adder and carry lookahead adder ?
### Ripple carry adder
### Carry lookahead adder
## How is the 2s complement used in a substractor
## How does an adder/substractor operates ?
## How is overflow detected in a binary adder ?




