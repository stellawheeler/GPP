# GPP
A 16-bit general purpose processor modeled using VHDL in Quartus II 13.0.  
The processor includes a custom datapath, control unit, ALU, and register file.  
Functional verification was performed using ModelSim waveform simulations.

## Features
The project can test individual parts of the general purpose processor, like the ALU, latch registers, decoders and seven-segment displays using ModelSIM and Quartus II waveform simulator.  
The FSM (Finite State Machine) cycles through the numbers from 1 to 8 and displays 5, 0, 1, 2, 8, 8, 8, 0, 5 according to each digit. For example, the 0 represents a 2.  
For all parts of the project, there are 2 latch registers that hold the inputted numbers for operation.
There is a 4-to-16 decoder that takes 4 bit input from the FSM, to cycle through the microcode. The decoder was made using 2 3-to-8 decoders as seen below.  
The original seven-segment display (sseg) has 2 inputs and 2 outputs, whereas the modified seven-segment display (sseg2) has 1 input and 1 output, seen in Part3.

### Part1
The first part of the project takes the inputted numbers and uses the operations below for the ALU (Arithmetic Logic Unit).
| Function | Microcode              | Operation  |
|----------|------------------------|------------|
| 1        | 0000000000000001       | A + B      |
| 2        | 0000000000000010       | A - B      |
| 3        | 0000000000000100       | NOT A      |
| 4        | 0000000000001000       | A NAND B   |
| 5        | 0000000000010000       | A NOR B    |
| 6        | 0000000000100000       | A AND B    |
| 7        | 0000000001000000       | A XOR B    |
| 8        | 0000000010000000       | A OR B     |
| 9        | 0000000100000000       | A XNOR B   |

### Part2
The second part of the project takes the inputted numbers and uses a different operation table, as seen below for the ALU (Arithmetic Logic Unit).
| Function | Microcode              | Operation                    |
|----------|------------------------|------------------------------|
| 1        | 0000000000000001       | A >> 2 (fill with 1s)       |
| 2        | 0000000000000010       | (A - B) + 4                  |
| 3        | 0000000000000100       | (A > B) ? A : B              |
| 4        | 0000000000001000       | A[7:4] ↔ B[3:0]              |
| 5        | 0000000000010000       | A + 1                        |
| 6        | 0000000000100000       | A AND B                      |
| 7        | 0000000001000000       | (~A[7:4], A[3:0])            |
| 8        | 0000000010000000       | ROTATE_LEFT(B, 3)            |
| 9        | 0000000100000000       | 00000000                     |

### Part3
The third part displays if the cycled FSM digits of 5, 0, 1, 2, 8, 8, 8, 0, 5 are even or odd parity as binary numbers. 
| Number (Binary) | Decimal | Parity Type | Output |
|-----------------|---------|------------|--------|
| 0101            | 5       | Even       | y      |
| 0000            | 0       | Even       | y      |
| 0001            | 1       | Odd        | n      |
| 0010            | 2       | Odd        | n      |
| 1000            | 8       | Odd        | n      |
| 1000            | 8       | Odd        | n      |
| 1000            | 8       | Odd        | n      |
| 0000            | 0       | Even       | y      |
| 0101            | 5       | Even       | y      |
## Project Structure
The current project structure is below:
```
GPP/
 ├── GPP.zip
 ├── README.md
 ├── LICENSE
 └── .gitignore
```
The unzipped GPP.zip file is below:
```
GPP/
 ├── atom_netlists
 │    └── GPP.qsf
 ├── db
 ├── incremental_db
 ├── output_files
 ├── simulation
 │    ├── modelsim
 │    ├── qsim
 │    └── work
 ├── ALU.bsf
 ├── ALU.vhd
 ├── ALU.vwf
 ├── ALU_2.bsf
 ├── ALU_2.vhd
 ├── ALU_2.vwf
 ├── ALU_3.bsf
 ├── ALU_3.vhd
 ├── ALU_3.vwf
 ├── dec.bsf
 ├── dec.vhd
 ├── dec4to16.bdf
 ├── dec4to16.bsf
 ├── dec4to16.vhd
 ├── dec4to16.vwf
 ├── FSM.bsf
 ├── FSM.vhd
 ├── FSM.vwf
 ├── GPP.qsf
 ├── GPP.qpf
 ├── latch.bsf
 ├── latch.vhd
 ├── latch.vwf
 ├── sseg.bsf
 ├── sseg.vhd
 ├── sseg.vwf
 ├── sseg2.bsf
 ├── sseg2.vhd
 ├── sseg2.vwf
 ├── part1.bdf
 ├── part1.vwf
 ├── part2.bdf
 ├── part2.vwf
 ├── part3.bdf
 └── part3.vwf
```
## Conclusion
Through this project, I developed a deeper understanding of how CPU operations are executed at the hardware level. I gained practical experience designing a datapath and control unit, and learned how microcoded control signals coordinate ALU operations, register transfers, and instruction execution.

This project also strengthened my understanding of latches and sequential logic in CPU architecture. I learned how clocked storage elements maintain state, enable synchronous data movement, and ensure predictable processor behavior across clock cycles.

Additionally, I improved my skills in:
- VHDL structural and behavioral modeling
- Finite State Machine (FSM) design
- Simulation and debugging using ModelSim
- Verifying functionality through waveform analysis

Next time, I will have better documentation of the hardware implementation on the Cyclone-II EP2C35F672C6 FPGA board and improve file organization.
