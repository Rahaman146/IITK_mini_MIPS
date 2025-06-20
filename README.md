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
src/
├── registers.v         # Register file implementation
├── memory.v           # Instruction and data memory
├── instruction_formats.v  # Instruction format definitions
├── instruction_fetch.v    # Instruction fetch stage
├── instruction_decode.v   # Instruction decode stage
├── alu.v              # Integer ALU implementation
├── fpalu.v            # Floating-point ALU implementation
├── iitk_mini_mips.v   # Main processor module
└── testbench/
    └── iitk_mini_mips_tb.v  # Testbench for verification
```

## Implementation Details

### Memory System
- 4KB instruction memory (4096 x 32-bit words)
- 4KB data memory (4096 x 32-bit words)
- Word-aligned memory access
- Byte-addressable memory interface

### Register File
- 32 general-purpose registers (R0-R31)
- 32 floating-point registers (F0-F31)
- Special registers (PC, HI, LO)
- Register 0 hardwired to 0
- Synchronous write with enable

### Instruction Formats
- R-type: opcode (6 bits), rs (5 bits), rt (5 bits), rd (5 bits), shamt (5 bits), funct (6 bits)
- I-type: opcode (6 bits), rs (5 bits), rt (5 bits), immediate (16 bits)
- J-type: opcode (6 bits), address (26 bits)

### ALU Operations
- Integer arithmetic: add, subtract, multiply
- Logical operations: AND, OR, XOR, NOT
- Shift operations: SLL, SRL, SLA, SRA
- Comparison operations: SLT
- Overflow and carry detection

### Floating-Point ALU
- IEEE 754 single-precision format
- Operations: add, subtract, multiply, compare
- Special cases handling (NaN, infinity)
- Overflow and underflow detection

## Testing

The testbench (`iitk_mini_mips_tb.v`) includes test cases for:
1. Basic arithmetic operations (add)
2. Memory operations (load/store)
3. Branch instructions (beq)
4. Floating-point operations (add.s)
5. Jump instructions (j)

To run the testbench:
1. Compile all Verilog files:
   ```bash
   vlog *.v
   ```
2. Run the simulation:
   ```bash
   vsim -c iitk_mini_mips_tb -do "run -all"
   ```
3. View the waveform output:
   ```bash
   view wave
   ```

## Usage

1. Clone the repository
2. Compile the Verilog files using your preferred simulator
3. Run the testbench to verify functionality
4. Modify the test program in the testbench to test different instructions

## Contributing

This is an educational project. Feel free to use and modify the code for learning purposes.

## License

This project is part of CS220 coursework and should be used in accordance with academic integrity policies. 