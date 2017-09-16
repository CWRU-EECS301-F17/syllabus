---

# Lab 2 Review

Note:
Lab 2 Questions, Issues, Feedback?


---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/BadSimulation.png&size=90% 90%

Note:
Red signals are uninitialized registers

---

#### Register Initialization

```verilog
reg [31:0] count_reg;

initial
begin
	count_reg <= 32'h00000000;
end

always @(posedge CLK)
begin
	count_reg <= count_reg + 1'b1;
end
```

Note:
Counters have feedback so an uninitialized values propagate.
Either initialize or reset all registers.

---

### Asynchronous Signals

* FPGAs are intended to be synchronous systems
* Most Off-chip signals occur asynchronously
* Unsynchronized signals cause metastability failures

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/RegisterTiming.png&size=90% auto

---

### SN74S74 Datasheet Parameters

![74S74 Specs](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/Specs_SN74S74.png)

---

## Metastability Demo

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/MetastabilityDemoCircuit.png&size=90% 90%

---

### Cyclone FPGA LE Parameters

![Cyclone Specs](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/Specs_Cyclone.png)

---

### Synchronizer Register Chain

![Sync Chain](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/SyncChain.png)

Note:
Typical synchronizer chain length is 2 or 3 registers.
Faster clock rates need longer chains due to metastability bleed though which is shown in the Faster Clock slide.
overflow

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/MsWf01.png&size=auto 90%

Note:
Normal Synchronizer Register Operation without input violations.

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/MsWf02.png&size=auto 90%

Note:
Input Data violates the tsu parameter of the register.

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/MsWf03.png&size=auto 90%

Note:
At faster clock rates, the metastability can cascade through multiple registers.

---

### Design Tips for Reliability

* Always use synchronous logic designs with FPGAs
* Apply proper timing constrains (make Quartus help)
* Minimize clock domain crossings (CDC) when possible
* Use proper CDC structures to transfer signals between domains
* Do not use data signals as clocks
* Treat rising and falling clock edge as separate domains

Note:
Rising and falling edges of the same clock should be considered two separate clock domains with the exact same frequency and a 180 phase shift.

---

## Lab 3 Topics

---

### Generate Blocks

* Programmatically instantiate logic at compile time
* Parametrizable
* Increases code flexibility and module reuse
* Conditional blocks (using **if** statements)
* Loops (using **for** statements)

---

```verilog
module Generate_Module
#(
	parameter DATA_WIDTH = 16
)
(
	input  [DATA_WIDTH-1:0] A,
	input  [DATA_WIDTH-1:0] B,
	output [DATA_WIDTH-1:0] Q,
	input  CLK
);

	wire [DATA_WIDTH:0] carry;
	
	genvar i;
	
	generate
	begin
		for (i=0; i < DATA_WIDTH; i=i+1)
		begin : multi_bit_adder_gen
	
			assign carry[0] = 1'b0;
	
			One_Bit_Adder adder_bit
			(
				.A( A[i] ),
				.B( B[i] ),
				.CIN( carry[i] ),
				.COUT( carry[i+1] ),
				.CLK( CLK )
			);
		
		end
	end
	endgenerate

endmodule
```

---

### Shift Register Chains

* Serial-in, Parallel-out (serial receiver)
* Parallel-load, Serial-out (serial transmitter)
* Linear-feedback Shift Register (cryptography)
* Serial-in, Serial-out (Delay-lines)
* Serial Loop-Back, Parallel-out (Ring Counters)

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/ShiftRegisterRingCounter.png&size=90% 90%


---


### Refactoring Code

* Repurposing existing code for a different application
* Saves time starting with something rather than nothing
* Faster time to market

---

# Lab 3 Overview

---?image=https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture03/Slides/Lab3-DevBoardLayout.png&size=90% auto
