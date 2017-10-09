---

# Lab 4 Review

Note:
Lab 4 Questions, Issues, Feedback?

---

## Group Projects

* Team Shared Lab Assignment Repos
	* lab5-assignment-team1
* 1st team member creates group, 2nd joins
* Synchronize your work through GitHub
* Resolve merge conflicts with WinMerge

---

## Git Merge Conflicts

* Git tries to merge changes when possible
* Unresolvable changes result in a Conflict file
* Conflict files have to be manually edited
	* Text editor or WinMerge
* Resolve conflicts by selecting changes to keep
* Commit the merged files to the Git repo
* Always pull updates before pushing changes

---

## Serial Devices

* UART (RS-232)
* PS/2 (Keyboard)
* Telegraph

---

## UART 
#### (Asynchronous Receiver-Transmitter)

* Data Framing and Signaling Protocol
* Used for RS-232, RS-422, RS-485 Bus Standards
* Supported by most embedded systems (terminal)
* Basic Error Detection (Optional)
* Configurable Speed and Data Payloads (7/8/9-bits)
* Anyone remember dial-up modems?

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture05/Slides/images/UART_Data_Frame.png&size=95% auto

Note:
Typical Data Frame: 8 Data Bits, No Parity Bit, 1 Stop Bit
Speed Configuration dependent on physical bus (300 Baud - 1000k Baud)
Baud Rate 

---

### Asynchronous Transmit

* Data transmitted without accompanying Clock
* Transmitter and Receiver have independent Clocks
* No phase relationship between Transmitter and Receiver
* Receiver re-aligns to Transmitter on Start Bit
* Transmission speed called Baud Rate

Note:
Baud Rate defined in symbols per second but for UART same as bits per second.

---

## PS/2 Keyboard Bus

* Introduced by IBM in 1987 (PS/2 Computer)
* Mostly phased out by USB (with exceptions)
	* Better security and BIOS compatibility than USB
* Synchronous Clock and Data Signals
* Bi-directional Data

Note:
PS/2 used on systems with USB disabled for security.
Better BIOS support than USB

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture05/Slides/images/PS2_Keyboard_Data_Frame.png&size=95% auto


---?image=https://upload.wikimedia.org/wikipedia/commons/b/b5/International_Morse_Code.svg&size=auto 90%


---

# Lab 5 Overview

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture05/Slides/images/Lab5_DevBoardLayout.jpg&size=auto 90%

---

# Questions?