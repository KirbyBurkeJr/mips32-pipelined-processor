# MIPS32 Pipelined Processor

![Processor diagram](https://github.com/KirbyBurkeJr/mips32-pipelined-processor/blob/main/doc/mips32_processor_diagram.png)

## Overview

This repository contains the Verilog design for a MIPS32 pipelined processor that supports multiple concurrent instructions and includes dedicated resources to mitigate data and control hazards. For more information, visit the [MIPS32 Pipelined Processor](https://kirbyburkejr.com/projects/mips32-pipelined-processor) page on my portfolio site.

## Features

This processor includes a five-stage pipelined datapath, sets of pipeline registers, and two hazard mitigation units that work together to process a subset of MIPS32 instructions.

### Five-Stage Datapath

The design includes a classic five-stage datapath, with banks of pipeline registers between each stage.

**Datapath**

- Instruction Fetch (IF)
- Instruction Decode (ID)
- Execution (EX)
- Memory Access (MEM)
- Write Back (WB)

**Pipeline Registers**

- IF/ID
- ID/EX
- EX/MEM
- MEM/WB

### Hazard Mitigation Units

Data Forwarding unit performs execution forwarding, for data hazards, when possible.

Hazard Detection unit supports Data Forwarding with stalling, and handles control hazards with stalling and flushing.

### Supported MIPS32 Instructions

This processor supports a subset of 21 MIPS32 R-, I-, and J-type instructions.

**R-Type (12)**

- Arithmetic (4): ADD, SUB, MULT, & DIV
- Logical (4): AND, OR, NOR, & XOR
- Shift (3): SLL, SRL, & SRA
- Compare (1): SLT


+ Non-standard implementations used for div and mult instructions.

**I-Type (8)**

- Arithmetic (1): ADDI
- Logical (3): ANDI, ORI, & XORI
- Load/Store (2): LW & SW
- Branch (2): BEQ & BNE

**J-Type (1)**

- J (jump)

## Directories

**docs/**

- mips32_instruction_specifications.png
- mips32_processor_diagram.png

**src/design/**

Contains the MIPS32_Processor.v design file and designs for its 16 dependencies.

**src/testbench/**

- tb_MIPS32_Processor.v

**sim/**

- tb_MIPS32_Processor_behav.wcfg
- tb_mips.csv

## Instructions

### Cloning the Repository

```bash
git clone https://github.com/KirbyBurkeJr/mips32-pipelined-processor.git
cd mips32-pipelined-processor
```

### Running the Simulation

The simulation includes a sequence of 22 test cases to validate the execution of instructions and hazard mitigation responses.

1. Open Vivado and create a new project.
2. Add the files in the `src/design/` and `src/testbench/` directories.
3. Run the simulation using the `tb_MIPS32_Processor.v` test bench file.
 a. Select "Run Simulation" to initiate the simulation.
 b. Select "Run All" to complete the simulation because its duration exceeds the stardand Vivado time limit.

Simulation output includes the display of a performance summary in the Tcl console, saving a detailed performance report to a CSV file (tb_MIPS32.csv), and a waveform diagram.

## Documentation

Detailed block diagram of parent MIP32 Processor module, including submodules, internal bus signals, and port mapping.

Tables with bit allocation for each instruction type.

### Tools Used

- [Vivado v2023.2 (64-bit)](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/2023-2.html) for Verilog module design and waveform generation.

## License

This project is licensed under the [MIT License](LICENSE).

## Contributing

Feel free to submit issues or pull requests to improve this project.
