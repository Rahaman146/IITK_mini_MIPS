# IITK-Mini-MIPS Processor

This project implements a simplified MIPS processor called IITK-Mini-MIPS, designed as part of the CS220 course assignment. The processor supports both integer and floating-point operations, with a focus on educational purposes.

## Features

- 32-bit word and instruction size
- Separate instruction and data memories (4KB each)
- 32 general-purpose registers
- 32 floating-point registers
- Support for R-type, I-type, and J-type instructions
- Basic integer arithmetic and logical operations
- IEEE 754 single-precision floating-point operations
- Branch and jump instructions
- Load and store operations

## Project Structure

```
├── src/
│ ├── alu.v 
│ ├── data_memory.v 
│ ├── fpalu.v # Floating-point ALU 
│ ├── instruction_decode.v 
│ ├── instruction_fetch.v 
│ ├── instruction_memory.v 
│ ├── iitk_mini_mips.v 
│ └── registers.v 
│
├── testbench/
│ ├── iitk_mini_mips_tb.v 
│ ├── instructions.mem 
│ ├── run_test.do 
│ ├── run_simulations.do 
│ └── run_test 
│
├── README.md
├── .gitignore

```


## Implementation Details

### Memory System
- 4KB instruction memory (4096 x 32-bit words)
- 4KB data memory (4096 x 32-bit words)
- Word-aligned memory access
- Byte-addressable memory interface

### Register File
- 32 general-purpose registers (R0–R31)
- 32 floating-point registers (F0–F31)
- Special-purpose registers: `PC`, `HI`, `LO`
- Register R0 is hardwired to zero
- Synchronous write with write-enable

### Instruction Formats
- **R-type**: `opcode (6) | rs (5) | rt (5) | rd (5) | shamt (5) | funct (6)`
- **I-type**: `opcode (6) | rs (5) | rt (5) | immediate (16)`
- **J-type**: `opcode (6) | address (26)`

### ALU Operations
- Integer: `add`, `sub`, `mul`
- Logical: `and`, `or`, `xor`, `not`
- Shifts: `sll`, `srl`, `sla`, `sra`
- Comparison: `slt`
- Overflow and carry detection

### Floating-Point ALU
- IEEE 754 single-precision format
- Operations: `add.s`, `sub.s`, `mul.s`, `cmp.s`, `eq.s`, `lt.s`, `le.s`, `gt.s`, `ge.s`
- Handles normalized values, overflow, and underflow
- Partial handling of NaN and infinity cases

## Testing

The testbench (`iitk_mini_mips_tb.v`) includes test cases for:

1. Integer arithmetic (e.g., `add`)
2. Memory operations (e.g., `lw`, `sw`)
3. Branch instructions (e.g., `beq`)
4. Floating-point operations (e.g., `add.s`)
5. Jump instructions (e.g., `j`)
6. Halting using `FINISH` instruction

### Run with ModelSim:

1. command to compile the code:

```bash
vsim -do testbench/run_simulations.do
```
or 

```bash
vsim -do testbench/run_test.do
```
2. coomand to view the waveform output:

```bash
view wave
```
### Run with Icarus Verilog:

1. command to compile the code:

```bash
cd testbench
./run_test
```
2. coomand to view the waveform output:

```bash
gtkwave dump.vcd
```

### Requirements
- ModelSim
- Or Icarus Verilog and GTKWave

## Usage

1. Clone the repository
2. Compile the Verilog files using your preferred simulator
3. Run the testbench to verify functionality
4. Modify the test program in the testbench to test different instructions

## Contributing

This is an educational project. Feel free to use and modify the code for learning purposes.

## License

This project is part of the CS220: Computer Architecture coursework at IIT Kanpur and should be used in accordance with academic integrity policies. 