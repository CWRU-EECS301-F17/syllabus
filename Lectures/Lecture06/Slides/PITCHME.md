---

# Lab 5 Review

Note:
Lab 5 Questions, Issues, Feedback?

---

## Serial Bus Protocols

* SPI (Serial Peripheral Interface)
* I2C (Inter-Integrated Circuit)
* UNI/O (One-Wire)

---

### SPI BUS

* 3-wire (Clock, Bi-direction Data, Chip-select)
* 4-wire (Clock, Data In, Data Out, Chip-select)
* Many different device dependent protocols
* Point-to-point or shared bus using Chip Selects
* Used for interfacing Memory, ADCs, DACs, Accelerometers, JTAG, etc...
* Data rates 20MHz or greater (only limited by physical interconnect)

Note:
https://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture06/Slides/images/SPI_Read_Sequence.png&size=90% auto

---

### I<sup>2</sup>C BUS

* 2-wire (Clock and Bi-directional Data)
* Shared multi-device bus using protocol addressing
* Standardized protocol by NXP Semi (formerly Philips)
* Most devices support 400kHz Fast-Mode.
* Speeds up to 5MHz with latest Ultra Fast-Mode
* Used for device config, small memories, temp sensors, power supply controllers, etc...

Note:
https://en.wikipedia.org/wiki/I²C
https://www.i2c-bus.org

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture06/Slides/images/I2C_Read_Sequence.png&size=auto 90%

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture06/Slides/images/I2C_Start_Stop_Bits.png&size=90% auto

---

### UNI/O BUS

* 1-wire (Clock/Data/Power)
* UNI/O is Microchip version of Dallas 1-Wire
* Shared multi-device bus using protocol addressing
* Used for ID chips and small sensors
* Encoded data bits to allow clock and power extraction from data line
* Bus rates between 10kHz to 100kHz

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture06/Slides/images/UNIO_Read_Sequence.png&size=auto 90%

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture06/Slides/images/UNIO_Bit_Values.png&size=auto 90%

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture06/Slides/images/UNIO_Scope_Plot.png&size=auto 90%

---

# Lab 6 Overview

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture06/Slides/images/Lab6_DevBoardSetup.png&size=auto 90%

---

## Logic Analyzer Demo

---

# Questions?