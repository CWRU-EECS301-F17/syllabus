---

# Lab 8 Review

Note:
Lab 8 Questions, Issues, Feedback?

---

### Direct Digital Synthesis

* Arbitrary Waveform Generation
* Precision Phase Control
* Wide frequency output range (MHz to mHz)
* Fast Waveform Switching

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/DigitalPhaseWheel_n2.png&size=90% auto

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/DigitalPhaseWheel_n4.png&size=90% auto

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/DigitalPhaseWheel_n8M1.png&size=90% auto

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/DigitalPhaseWheel_n8M2.png&size=90% auto

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/DigitalPhaseWheel_n8M3.png&size=90% auto

---

![DDS Waveform Demo](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/Generator-Demo.jpg)

---

### DDS Architecture

![DDS Block Diagram](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/DDS_Block_Diagram.png)

---

### Phase Accumulator

* Simple Counter Register
* Tuning Word **M** added at constant rate **f<sub>o</sub>**
* Frequency Resolution determined by Width
	* f<sub>res</sub> = f<sub>o</sub> / 2<sup>N</sup>
* Frequency Output determined by Tuning Word
	* f<sub>out</sub> = M * f<sub>o</sub> / 2<sup>N</sup>
* Upper bits used to index memory pattern

---

### WM8731 Audio Codec

![WM8731 Block Diagram](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/WM8731_Block_Diagram.png)

---

### Audio Bus

![WM8731 Audio Bus Timing](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/WM8731_Audio_Bus_Timing.png)

---

### Sample Rate Parameters

* Sample Data = 16-bit
* Sample Rate (fs) = 48kHz
* Two Audio Channels
* BCLK Rate = 48000 x 16 x 2 = 1.536MHz
* Base Over-sample = 384fs
* XCK Rate = 48000 x 384 = 18.432MHz

---

### Finite Impulse Response (FIR)

* Many DSP applications
	* High, Low or Band-pass filters
* No feedback loop
* Deterministic timing
* Easy to implement in FPGA logic
* IP Cores available

---

### FIR Band-pass Filter

![FFT Bandpass Filter](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/FFT_Bandpass_Freq_Resp.png)

---

![Lab 6 Scope Plot](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture11/Slides/images/Lab6_ScopePlot.png)



---

# Lab 9 Questions


