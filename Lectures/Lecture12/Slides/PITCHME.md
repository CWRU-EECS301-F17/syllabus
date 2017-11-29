---

# Lab 9 Questions

Note:
Lab 9 Questions, Issues, Feedback?

---

### Signal Digitizer

* Capture digital waveforms to memory buffer
* Common applications
	* Oscilloscope
	* Data Acquisition 
	* Audio Recording
* Used in Lab 9 to capture DDS waveforms

---

### Digitized Waveform

* Fixed interval sampling

![Sampled Waveform](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture12/Slides/images/Sampled_Waveform.png)

Note:
* Fixed sample rate doesn't require time samples
* Variable sample rate requires time stamps time domain correlation

---

### SCPI Trigger Model

* Basis for most Instrumentation Trigger Systems
* SCPI Trigger Model Layers
	* Idle
	* Initiate
	* Arm
	* Trigger
	* Device Action
* http://www.ivifoundation.org/docs/scpi-99.pdf

Note:
Standard Commands for Programmable Instruments (SCPI)
IVI Foundation Standard
SCPI Standard defines Trigger Model used by many instrumentation products.
http://www.ivifoundation.org/docs/scpi-99.pdf

---?image=https://raw.githubusercontent.com/CWRU-EECS301-Sum17/syllabus/master/Lectures/Lecture12/Slides/images/TriggerModel.png&size=auto 90%

---?image=https://raw.githubusercontent.com/CWRU-EECS301-Sum17/syllabus/master/Lectures/Lecture12/Slides/images/TriggerModelSamplingExample.png&size=90% auto


---

## Clock Domains

* Large designs may contain multiple clock sources
* A **Clock Domain** contains all logic synchronized by one clock source
* Metastable events can occur when passing signals between domains
* Always use proper synchronization structures when crossing domains

---

### Clock Domain Crossing (CDC)

* Signals crossing from one domain to another are **asynchronous**
* Asynchronous inputs can cause metastability

![Clock Domain Crossing](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture12/Slides/images/Clock_Domains_01.png)

---

### Synchronization Buffers

* Same method used for Key and Push Button inputs
* Works for slow clock to fast clock domains

![Clock Domain Crossing](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture12/Slides/images/Clock_Domains_02.png)

---

### Sync with Edge Detection

* Generate single clock pulse on edge transition

![Clock Domain Crossing](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture12/Slides/images/Clock_Domains_03.png)

---

### Other CDC Structures

* Flancter
* True-Dual Port Block RAM
* FIFO
* Mailbox

---

# Questions


