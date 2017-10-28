---

# Lab 7 Issues

Note:
Lab 7 Questions, Issues, Feedback?

---

## Verilog Signed Math

```verilog
wire signed [15:0] a, b;
wire signed [31:0] q;

assign q = a * 16'sh0123 + b * 16'sh8123;
```

---

## Test Bench Overview

---

### Types of Test Benches

* Functional Test Bench
* Formal Verification Test Bench

---

### Functional Test Bench

* Quick tests for debugging without hardware
* Manual output checking (ModelSim waveforms)
* Requires knowledge of expected UUT operation
* Full access to UUT signals for code debugging
* Examples:
	* `TF_WS2812_LED_Transmitter`
	* `TF_Serial_Terminal_Parser`

---

### Formal Verification Test Bench

* Automated result verification
* Pass/Fail results do not require full UUT knowledge
* Regression testing for later design phases
* Full coverage testing (Ideally)
* Examples: 
	* `TF_LWS_Accel_Position_Computator`

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture09/Slides/images/TestBenchArchitecture.png&size=90% auto

---

## LCD Panel

![LCD](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture09/Slides/images/LCD_Image.png)

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture09/Slides/images/FPGA_to_LCD_Communications.png&size=90% auto

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture09/Slides/images/LCD_HSYNC_TimingDiagram.png&size=90% auto

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture09/Slides/images/LCD_VSYNC_TimingDiagram.png&size=90% auto


---

### Sprites

* State of the Art 1980's Technology

![boo](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture09/Slides/images/boo_image.png)

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture09/Slides/images/pixilart_screen.png&size=90% auto


---

# Lab 8 Overview

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture09/Slides/images/Lab8-DevBoardLayout.png&size=auto 90%

s
---

