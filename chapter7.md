# [CHAPTER 7] Technology parameters and timing issues
## What are integrated circuits ? PCB ? What is glue logic ? What are logic families ?
Digital circuits are constructed with integrated circuits, an integrated circuit (or chip) is a semi-conductor crystal, most of the time made of silicon containing the electronic components, gates and memory storage
Integrated circuits are connected through pins on a PCB (printed circuit board)

An integrated circuit can range from many dimensions and can count up to a few billions transistors, nowadays, chips are fabricated on wafer.
Digital integrated circuits were categorized by how many gates they contained
- **SSI** (small scale integration) containing between 1-20 gates are very rarely used now except as **glue logic** which is a type of circuitry that allows different types of chips to work together.
- **MSI** (medium scale integration) containing between 20-200 gates.
- **LSI** (large scale integration) containing 1000s of gates.
- **VLSI** (very large scale integration) containing between 10<sup>4</sup> -10<sup>9</sup> gates.

### Logic families 
Digital circuits are also classified according to families, a **logic** family is a collection of integrated circuits with similar input/output and internal circuitry. Chips from the same family can be interconnected while they may not be compatible between logic families.
The most common logic families are:
- **TTL** (transistor - transistor logic) that uses bipolar juction transistors
- **CMOS** (complementary metal-oxide-semiconductor logic) mostly used nowadays. CMOS circuits account for the majority of circuits nowadays, the basic building blocks of CMOS are the MOS transistors
  - **NMOS** transistors: n-channel MOS transistors
  - **PMOS** transistors: p-channel MOS transistors

## How does a transistor works ?
MOS transistors have 3 terminals, the **gate** (not to confuse with logic gates) is the **controlling** node, the **source** is electrically charged and the **drain** is not, powering the **gate**
allows current to flow from the **source** to the **drain**. \
The conduction between drain and source is either very high (ON) or very low (OFF) and is controlled by the power passed to the gate.
for an NMOS transistor :
- _V_<sub>G</sub> - _V_<sub>S</sub> > _V_<sub>t</sub> &rarr; switch is closed.
- _V_<sub>G</sub> - _V_<sub>S</sub> &lt; _V_<sub>t</sub> &rarr; switch is open. 

We can model logic variables with transistors
- For **NMOS** transistors: S is connected to a low voltage D connected to high voltage, G is connected to input &rarr; X, a logic variable.
  - The switch is closed if X = 1
  - The switch is open if X = 0

  <img src= ./images/chapter7/NMOS.png width = 300 />

- For **PMOS** transistors, it's the oppposite, S connected to high voltage, D connected to low voltage, G connected to input signal &rarr; X, a logic variable.
  - The switch is closed if X = 0
  - The switch is open if X = 1

  <img src= ./images/chapter7/PMOS.png width = 300 />

## What are the inverter, NAND and NOR transistor circuits
The inverter circuit is the following, 
- Q2 is active when the input is low, meaning the current from VDD will pass and return 1 when input is 0. \
- Q1 is active when the input is high and discards the signal, the current from VDD cannot pass since Q2 is inactive. \

<img src= ./images/chapter7/inverter.png width = 400 />

The NAND gate circuit is the following:
- If A is low and B is high (and symmetrically B low A high), Q2 or Q4 are on meaning Z will receive high current from VDD.
- If both A and B are high, Q1 and Q3 will enable and discard VDD, meaning Z will be low.
- If both A and B are low, Q2 and Q4 are on and Z will receive high from VDD.

<img src= ./images/chapter7/nand.png width = 200 />

The NOR gate circuit is the following:
- If A is high and B low (and symmetrically B high A low), Q1 or Q2 will be closed and VDD cannot pass meaning Z is low
- If Both A and B are low, VDD can pass and can only go to Z.

<img src= ./images/chapter7/nor.png width = 200 />

## What means fan-in and fan-out ?
## What is CMOS static electrical behavior what is ESD ?
## Calculate static and dynamic power consumption in CMOS circuits
## Which timing needs to be respected to ensure the correct operation of a flip-flop ?
## Sequential circuit timing
## What is clock skew ?
## What are transmission gates, Schmitt trigger inputs, three-state buffers, open drain outputs and how do these circuits work? 
## Synchronization, synchronizers, synchronizer failure and metastability
