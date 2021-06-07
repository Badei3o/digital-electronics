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

## What is a multiplexer ?
## What is a half-adder/full adder ?
## What are ripple carry adder and carry lookahead adder ?
## How is the 2s complement used in a substractor
## How does an adder/substractor operates ?
## How is overflow detected in a binary adder ?




