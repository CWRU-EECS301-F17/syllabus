---

# Lab 7 Questions

Note:
Lab 7 Questions, Issues, Feedback?

---

## FPGA Computations

* FPGA fabric ALMs optimized for addition
	* 2-bits per ALM (Cyclone V)
	* Fast-Carry Chains
* Possible to implement Multipliers with ALMs
	* Requires lots of resources
	* Limited clock rates due to combinatorial layers
* Most FPGA architectures provide Hard-IP multipliers

---

## FPGA DSP Blocks

* Hard-IP to support Digital Signal Processing
* Optimized propagation times for high clock rates
* Fused Multiplier and Accumulators (FMA)
* Internal Pipeline Registers
* Carry-chains to combine multiple DSP Blocks
* Tailored for most common MAC algorithms
* 5CSEMA5F31 FPGA has 87 DSP Blocks

Note:
Hard-IP are FPGA features implemented in Silicon instead of FPGA fabric.
MAC = Multiply-accumulate
Fused Multiply Accumulate (A*B + C) maintains precision by having an adder wide enough to accept the multiplier outputs without rounding.

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture08/Slides/images/DSPBlockArchitecture.png&size=auto 90%

---

### Multiply-Accumulate Algorithms

* Dot Products
* FFT and FIR Filters
* Polynomials
* Matrix Multiplications

Note:
https://en.wikipedia.org/wiki/Multiply–accumulate_operation

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture08/Slides/images/DotProductExample.png&size=auto 90%

---

### Computation Pipelines

* Minimize resource usage by splitting operations across multiple clock cycles using same computation block
* Series functions
	* Polynomials (Horner's Method Series)
	* Filters (FIR, CIC)

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture08/Slides/images/PolynominalExample.png&size=auto 90%

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture08/Slides/images/FIRFilterExample.png&size=auto 90%

---

# Fall Break
