#HSLIDE

## LAB 1 REVIEW

#HSLIDE

## Hardware Description Language

* Programmatically describe digital logic circuits
* Differences from other programming languages
	* Concurrent processes
	* Notion of time (required for simulation)
	* Emphasis on simulation
* Two major HDLs for FPGAs: **Verilog** and **VHDL**


#HSLIDE

## VHDL

* Developed by request of the Dept. of Defense in the late 1980s
* VHSIC HDL (Very High Speed Integrated Circuit Hardware Description Language)
* Based on ADA (which was also developed by DoD)
* Standardized in 1987 as IEEE 1076
* Quartus defaults to the VHDL 1993 standard

#HSLIDE

## Verilog

* Originally developed by **Gateway Design Automation** in the early 1980s
* Popularized by **Cadence Design Systems** for logic simulation
* Many features borrowed from the C language
* Standardized in 1995 as IEEE 1364
* Quartus defaults to the Verilog-2001 standard

#HSLIDE

## System Verilog

* Superset of the Verilog-2005 standard
* Added modern language features
* Comparing SystemVerilog to Verilog is like comparing C++ to C
* Vendor support is stablizing

#HSLIDE

## RTL Logic (Register Transfer Level Logic)

![RTL Logic](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture02/Slides/rtl-logic.png)

* HDL behavioral models are translated to RTL logic
* RTL logic is synthesized into Gate-level logic
* Gate-level logic is mapped to the FPGA cell structure

#HSLIDE

### FPGA Fabric (Altera Cyclone V)

![Cyclone V Floorplan](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture02/Slides/cv_floorplan.gif)

* FPGA fabrics consist mainly of ALMs
* Other Hard-IP features added for additional capabilities

#HSLIDE

### ALM (Adaptive Logic Module)

* Cyclone V 5CSEA5 FPGA has 32,075 ALMs

![Cyclone V ALM](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture02/Slides/cv_alm01.png)

#HSLIDE

## Verilog vs VHDL

* Both languages are designed to solve the same problem
* Both have similar structures to accomplish the same tasks
* Syntax is the biggest difference
	* VHDL is not case-sensitive, whereas Verilog is
	* VHDL has stronger type checking than Verilog
	* Verilog is more flexible for generating simulation models
	* Verilog is more succinct, whereas VHDL is verbose


#HSLIDE

### Modular Design

* Partition design into small functional blocks
* Easier code reuse and refactoring
* Enables unit-testing of modules
* Well supported by both Verilog and VHDL

#HSLIDE

**Verilog Module**

```
module Example_Logic_Block
#(
	parameter CLK_RATE = 50 // MHz
)
(
    input a, b, c,
    output z
);

	assign z = (a & b) ^ c;  

endmodule
```

#HSLIDE

**VHDL Entity/Architecture**

```
library ieee;
use ieee.std_logic_1164.all;

entity Example_Logic_Block is
generic 
(
	CLK_RATE : integer := 50 -- MHz
);
port
(
	a, b, c : in std_logic;
	z : out std_logic
);
end entity;

architecture rtl of Example_Logic_Block is
begin
	z <= (a and b) xor c;
end rtl;
```

#HSLIDE

## Good Coding Practice

* One module definition per file
* Include comment header block for each module
	* Example: See any Lab Assignment module
* Name of file should match name of module
* Prefix the filename of grouped modules
	* Example: `CLS_Scanner_Module.v`


#HSLIDE

### Signal Types

* wire     (combinatorial signal)
* reg      (registered signal)
* integer  (unsigned integer, _usually_ 32-bit)
* real     (floating point, IEEE 64-bit)
* vectors (either wire or reg) are specified with [u:l]
	* `wire [7:0] bus_wire_of_8_bits`

#HSLIDE

### Numerical Constants

* Number constants specified in format: ```width'radix value```
* width is number of bits
* radix defines base of value
	* `h` for hexidecimal : `8'h3D`
	* `d` for decimal : `8'd61`
	* `o` for octal : `8'o055`
	* `b` for binary : `8'b00101101`

#HSLIDE

### Signal Assignments

**Verilog**

```
wire a, b, c; // Defined anywhere in module (above usage)

assign c = (a & ~b) | (~a & b);
```

**VHDL**

```
signal a, b, c: std_logic; -- Defined in 

c <= (a and not b) or (not a and b);
```

#HSLIDE

### Register

* `always` block with edge sensitive clock creates register

```Verilog
reg [15:0] data_reg;

always @(posedge CLK)
begin
	data_reg <= some_data;
end
```

#HSLIDE

### Multiplexer
**(non-registered)**

* Continuous assignment using always block
* `mux` output selected by `mux_sel`

```Verilog
always @*
begin
	case (mux_sel)
		2'h0 : mux <= a;
		2'h1 : mux <= b;
		2'h2 : mux <= c;
		2'h3 : mux <= d;
	endcase
end
```

#HSLIDE

### Rollover Counter

```Verilog
// Generate a clock tick every 75 clock cycles
reg [8:0] counter_reg;  // 9-bit counter
wire      clock_tick;

// Use the counter rollover as the clock tick
assign clock_tick = counter_reg[8]; // Rollover bit

always @(posedge CLK)
begin
	if (clock_tick)
		counter_reg <= (9'h100 - 9'd75 + 1'b1); // Reload the counter
	else
		counter_reg <= counter_reg + 1'b1; // Increment the counter
end
```

#HSLIDE

## Parameters

* Similar concept to overloading in C++
* Parameters make module functionality flexible
* Simple parameters
	* Specify signal widths
	* Set delay parameters
* Complex parameters
	* Coupled with `generate` can completely change a module's function

#HSLIDE

### Parameter Examples

```Verilog
parameter CLK_RATE = 50; // MHz
parameter DELAY_TIME = 1000; // nS
	
localparam DELAY_TICKS = DELAY_TIME / (1000.0 / CLK_RATE);
localparam COUNT_WIDTH = bit_index(DELAY_TICKS);
localparam ROLLOVER_VAL = { 1'b1, {(CNT_WIDTH){1'b0}} };
localparam COUNT_LOADVAL = ROLLOVER_VAL - DELAY_TICKS + 1'b1;

reg [COUNT_WIDTH:0] count_reg;
```

#HSLIDE

**Rollover Counter (Parameterized)**

```Verilog
// Generate a clock tick every 75 clock cycles
localparam CLOCKS_PER_TICK = 75;

// Compute Counter Parameters
localparam COUNTER_WIDTH = bit_index(CLOCKS_PER_TICK);
localparam COUNTER_LOADVAL = {1'b1, {COUNTER_WIDTH{1'b0}}} - CLOCKS_PER_TICK + 1'b1;

reg [COUNTER_WIDTH:0] counter_reg;
wire                  clock_tick;

// Use the counter rollover as the clock tick
assign clock_tick = counter_reg[COUNTER_WIDTH];

always @(posedge CLK)
begin
	if (clock_tick)
		counter_reg <= COUNTER_LOADVAL;
	else
		counter_reg <= counter_reg + 1'b1;
end
```


#HSLIDE

## Lab 2 Overview

![LED Scanner](https://raw.githubusercontent.com/CWRU-EECS301-F17/syllabus/master/Lectures/Lecture02/Slides/led_scanner.gif)
