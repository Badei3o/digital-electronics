# [CHAPTER 3] COMBINATIONAL CIRCUITS 

## Boolean algebra and logic gates
- **Boolean algebra** is a mathematical system for specifying and transforming logic functions. It is used to design and analyze digital systems.
  boolean algebra revolves around binary variables (variables whose value can etheir be **true** or **false**) and the use of binary functions on them.
- **Logic gates** are circuits that implements logic functions, a logic function is a function that takes 
one or several binary variables and returns one. Basical logical functions are **AND, OR, NOT**.
  - The **AND** function is denoted by a dot : (X**AND**Y) &rarr; (X•Y) or (XY).
  - The **OR** functions is denoted bu a plus : (X**OR**Y) &rarr; (X+Y).
  - The **NOT** is denoted by an overbar or a !: (**NOT** X) &rarr; (!X).

  Nowadays, logic gates are physically implemented using transistors that reprensent electronic switches that open and closes current paths. \
  The diagrams corresponding to logic gates are the following:
  <img src= ./images/chapter3/gates.png />

The order of evaluation of a boolean expression is:
 1. Expressions between brackets
 2. NOT
 3. AND
 4. OR

Some basic identities of boolean algebra are:

| 1  | X + 0 = X                 | 2  | X • 1 = X               | The **existence of 0 and 1**    |
|----|---------------------------|----|-------------------------|---------------------------------|
| 3  | X + 1 = 1                 | 4  | X • 0 = 0               | The **existence of 0 and 1**    |
| 5  | X + X = X                 | 6  | X • X = X               | The **idempotence**             |
| 7  | X + !X = 1                | 8  | X • !X = 0              | The **existence of complement** |
| 9  | !!X = X                   |    |                         | The **involution**              |
| 10 | X + Y = Y + X             | 11 | XY = YX                 | The **commutative** pair        |
| 12 | X + (Y + Z) = (X + Y) + Z | 13 | X(YZ) = (XY)Z           | The **associative** pair        |
| 14 | X(Y + Z) = XY + XZ        | 15 | X + YZ = (X + Y)(X + Z) | The **distributive** pair       |
| 16 | !(X + Y) = !X • !Y        | 17 | !(XY) = !X + !Y         | The **DeMorgan's** pair         |


## What are the minterms and maxterms of a boolean function
Logical functions can be represented in a **standard or canonical form**, two of them are 
the sum of minterms and the product of maxterms to understand them the following terms are needed:
- A **literal** is a variable within a term taht may or may not be complemented.
- A **normal term** is a product or sum term in which a variable appears no more than **once**.

### The sum of minterms (SOM)
A n-variable **Minterm** is a normal product term with **n** literals. \
Given that each literal can be either complemented or not, there are 2<sup>n</sup> minterms.

A **minterm** reprensent exactly one combination of binary variables in the truth table, it has the value 1 for that combination and 0 for the others.
The binary representation of the index of the minterm tells us which literal in the combination is **complemented or not**. \
e. g. the 4th minterm: 4 &rarr; 100 means that X = 1, Y = 0, Z = 0. \
thus in order for the fourth **minterm** to be true, the corresponding product must be &rarr; X!Y!Z.

We can implement any logical function F by "**ORing**" the minterms at which the function's result in the truth table is true.
### The product of maxterms (POM)
A n-variable **Maxterm** is a normal sum terms with **n** literals. \
Given that each literal can be either complemented or not, there are 2<sup>n</sup> maxterms.
The binary representation of the index of the maxterm tells us which literal in the combination is **complemented or not**. \
e. g. the 4th minterm: 4 &rarr; 100 means that X = 0, Y = 1, Z = 1. \
thus in order for the fourth **maxterm** to be true, the corresponding product must be &rarr; !X + Y + Z.

We can implement any logical function F by "**ANDing**" the maxterms at which the function's result in the truth table is false.
## What is the relationship between a minterm and its corresponding maxterm
Using **DeMorgan's theorem** we can deduct that the maxterm **M**<sub>i</sub> is the opposite of its corresponding minterm **m**<sub>i</sub>. \
&nbsp; DeMorgan : !(x • y) = !x + !y \
For a 2 variables example: \
&nbsp; **M**<sub>2</sub> = !x + y and **m**<sub>2</sub> = x • !y \
&nbsp; !(**M**<sub>2</sub>) = !!x • !y = x • !y =  **m**<sub>2</sub>

## SOM, POM, SOP, POS implementations, How to converts from SOM to a POM and from SOP to POS.

### SOP

The implementation of **SOP** consists of a group of **AND** gates followed by one **OR** gate (called two level implementation). \
<img src= ./images/chapter3/SOP.png width="400"/> 

For the function F = !Y + !XY!Z + XY

### POS

The implementation consists of a group of **OR** gates for the sums followed by an **AND** gate for the product.
<img src= ./images/chapter3/POS.png width="400"/> 

For the function F = X(!Y + Z)(X + Y + !Z)

### SOP to POS conversion
The **SOP** of a function is the sum of the minterms corresponding to a **1** in the function's truth table. and the **POS** is the sum of maxterms corresponding to a **0** in the function's truth table.
Thus for a set of indexes _I_ and one of its subset _A_ the set of indexes where the result of F is **1** : SOP(_A_) = POS(_I_/_A_).

## What are the literal cost and gate input cost of a circuit, how to compute it from a diagram

The **literal** and **gate input** cost criterias used in circuit optimization, which is the process of simplification of a circuit using a specific procedure or algorithm.

- The literal cost (L) is the number of literal appearances in a Boolean expression corresponding to the logic circuit diagram. \
  **e.g.** : 
  - F = BD + A!BC + A!C!D &rarr; L = 8
  - F = BD + A!BC + A!B!D + AB!C &rarr; L = 11

- The gate input cost (G and GN) is the number of inputs to the gates in the implementation corresponding exactly to the given equation or equations.
  In **POS** and **SOP** equations:
  - G = L + #Terms (excluding single literals terms)
  - GN = G + #Distinct complemented single literals

  **e.g.** :
  - F = BD + A!BC + A!C!D &rarr; L = 8, G = 11, GN = 14
  - F = (A + !B)(A + D)(B +C +!D)(!B + !C + D) &rarr; L = 10, G = 14, GN = 17

## Karnaugh maps
A Karnaugh map is a representation of a logic expression in a table (different representation of the truth table) taht allows using "adjacent" terms for simplifications
A **K-map** is a collection of squares 
- Each square represent a minterm.
- The collection of squares is a graphical representation of a Boolean function.
- Adjacent squares differs in the value of one variable (like gray coding).
- Alternative algebraic expression for the same function are derived by recognizing **patterns** of squares.

**K-maps** are useful to minimize logic functions with 2-6 input variables knowing a **K-map** for n input variable is composed of n x n squares (grows quadratically).

### Example for 2 variables
The 4 minterms are placed as below

<img src= ./images/chapter3/karnaugh.png width=350 />

We can use this table and the patterns it presents to simplify any boolean function, consider F represented by the truth table:

| A | B | F |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

We know with the **SOM** that : F(A, B) = m<sub>0</sub> + m<sub>1</sub> + m<sub>3</sub>\
- The first step in using the **K-map** is to draw it by filling with one in each region of the table corresponding to the minterms.
- Then the second step is to identify the collections of rectangles on the map representing product terms :
  <img src= ./images/chapter3/karnaugh1.png width=200 />

- The third step is to determine if any rectangle we have is necessary to cover all the 1s in the **K-map**, is there a term that we can remove from our sum that will still give us the right function.
- The fourth step is to read off the sum of products expressions, determining the corresponding product terms for the required rectangles in the map, in this example: F = !A + B, (The row where A is complemented or the column where B is not complemented).

### Example for 3 variables
Reduced literal product terms for **SOP** standard forms correspond to rectangles on **K-map** containing cell counts that are powers of 2.

<img src= ./images/chapter3/karnaugh2.png width=200 />

The values of YZ are arranged according to a cyclic gray code (a single bit change from the others).
Also remember that the sides of the **K-map** are warped, rectangles can contain seemingly non-adjacent cells.

### Map manipulation
The procedure of combining squares can be a little bit more systematic with the following terms introduced. \
For a given boolean function and its **K-map**
- An **implicant** is a product term in a boolean function if it has the values "1" for all the minterms of the product term (all the rectangles on a **K-map** made up of squares containing 1s are implicants).
- A **prime-implicant** is a product term obtained by combining the maximum possible number of adjacent squares in the map into a rectangles with the number of squares a power of 2.
- A prime implicant is called an **essential prime implicant** if it is the only prime implicant that covers one or more minterm.

<img src= ./images/chapter3/implicants.png width=450 />

Thus the systematic procedure for finding the optimized expression from the K-map is:
1. Determine all prime implicants
2. Do the logical sum of all the prime essential implicants and the other prime implicants needed to include remaining minterms not included in the essential prime implicants.

Apply the **Selection rule**: minimize the overlap among prime implicants as much as possible, in the final solution, make sure that each prime implicant selected includes at least one minterm not included in any other prime implicant selected.

### "Don't care" inputs

In certain situations the boolean function at the output is not defined or does not make sense for certain input combinations. thus the corresponding output values can be assumed either at 0 or 1 and is represented as "X" in a **K-map**.
For the simplification of the function, the X can either be treated as 1 or 0 depending what's more avantageous.

- In this example, the X is treated as 0 since it will require more implicants to simplify if treated as 1:

  <img src= ./images/chapter3/dc1.png width=300 />

- Here it's beneficial to treat it as 1 since it allows to find larger implicants which means less product terms.

  <img src= ./images/chapter3/dc2.png width=300 />

## What is an odd/even boolean function ?
### Exclusive OR and exclusive NOR operator and gates

The exclusive OR (**XOR**) is an operator that performs the function:
X **XOR** Y = X!Y + !XY 

The **XOR** complement called **XNOR**: 
X **XNOR** Y = XY + !X!Y

The **XOR** function can be extended to 3 or more variables, for more than 2 variables it's called an **odd¨** function, not a **XOR**. \
Similarly, we can extend the **XNOR** function to morre than 2 variables, which is called an **even** function.

## What are the gate propagation delay, transport delay and inertial delay
The gate propagation delay is the time required for a change in value of a signal to propagate from input to output, three propagation delays can be distinguished.
- The _high-to-low_ propagation time _t_<sub>PHL</sub> is the delay measured from reference voltage on the input IN to the reference voltage on the output OUT
  with the output voltage switching from H to L (often the reference voltage is 50% point, halfway between the minimum and the maximum values of the voltages signals).
- The _low-to-high_ propagation time _t_<sub>PLH</sub> is the delay measured from the reference voltage on the input voltage IN to the reference voltage on the output voltage OUT, with the output voltage going from L to H.
- The propagation delay _t_<sub>pd</sub> is the maximum of these two delays.

<img src= ./images/chapter3/delay.png width=400 />

### Transport delay and inertial delay 
Transport delay and inertial delay are models employed in modeling logic gates during simulations
- **Transport delay** the change in an output in response to an input change occurs after a specific **propagation delay**
- **Inertial delay** is similar to transport delay except that if changes in input causes the output to change twice in an interval of time less than the **rejection time** the change is ignored, the rejection time is a value no larger than the propagation delay (often equal to the propagation delay). \

In the following model, an **AND** gate is modeled with no delay, transport delay and inertial delay, the colored bar shows a 2ns **propagation delay** and the thinner black bar shows a 1ns **rejection time**. \

<img src= ./images/chapter3/delay2.png width=400 />

# Timing hazards in combinational circuits
So far, we've designed circuits ignoring any form of delay (steady state analysis), observing the delays and their effect is called a _transient analysis_, typically, the output of a circuit might have a short pulse due to delay that cannot be predicted by steady state analysis. \
When a combinational circuit can produce a glitch, it is called a **hazard**, hazards can be eliminated using Karnaugh maps. \

### Static 1 hazards
A static 1 hazard is the possibility of a circuit to produce a 0 glitch at the output when the steady-state would predict a 1. \
This occurs when a pair of input combination
- Differs in one variable.
- Both give one as an output so that it is possible for a momentary 0 output to occur during a transition in the differnet input variable. \

A static-1 hazard may occur in two level **AND-OR** circuits like in the example below, if we assume X , Y, Z = 1 and the system switches to X, Y, Z = 1, 1, 0. Timing delay through each gates is 1 unit of time.

<img src= ./images/chapter3/static1.png width=500 />

Static-1 hazards can be spotted in Karnaugh maps, when we look for adjactent "1" cells that are not covered by a single product term, the solution is to cover the hazardous input pair
<img src= ./images/chapter3/static12.png width=500 />

### Static 0 hazards

A static-0 hazard is the possibility of a circuit to produce a 1 glitch at the ouput, static hazards can occur in two-level **OR-AND** circuits.


