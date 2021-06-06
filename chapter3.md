# [CHAPTER 3] COMBINATIONAL CIRCUITS 

## Boolean algebra and logic gates
- **Boolean algebra** is a mathematical system for specifying and transforming logic functions. It is used to design and analyze digital systems.
  boolean algebra revolves around binary variables (variables whose value can etheir be **true** or **false**) and the use of binary functions on them. \
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



## What is an odd/even boolean function ?

## What are the gate propagation delay, transport delay and inertial delay

## Timing hazards in combinational circuits

