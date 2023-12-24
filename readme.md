This is a 16-bit, 5-stage RISC processor. RTL description in Verilog. Includes assembler, simulator, and example programs.

### Overview
This project is about a 16-bit processor made using Verilog, which has five main stages: instruction fetch, decode, execute, memory access, and register writeback. The processor uses the Harvard architecture, meaning it has separate memories for programs and data. If there's a data issue called a RAW hazard, the processor might pause. 

There's also a simulator for this processor made with Verilator, an open-source tool available on Github or through Ubuntu. Plus, there's a Python tool in the project that turns programs in the swt16 assembly language into machine code.

## Directory structure
```
├── bench        : Simulator directory
├── doc          : ISA documentation
├── prog         : Example / test programs
├── README.md    : This readme
├── rtl          : Processor description in Verilog
└── utils        : Utilities: automated tests
```

To install Verilator, GTKWAVE, and Python, execute the following command (on Ubuntu Linux):

sudo apt-get install verilator gtkwave python

Example simulation run:

./swt16/Vswt16_top --simTime 200 --pmemFile ../prog/test_load_store.pmem --dmemFile ../prog/test_load_store.dmem --dmemDump

In this example, --simTime <timeUnits> specifies the number of time units for which the simulation is run. The option --pmemFile <filename> specifies the program file that is loaded into the program memory. Similarly, --dmemFile <filename> specifies the data file that is loaded into the data memory.

### Writing a program
This project contains an assembler written in Python. The assembler generates machine code for the processor from programs written in the swt16 assembly language. To invoke the assembler, execute the following:

cd utils && python asm.py -i <asm_file> -o <machine_code_file>

You can try out the assember by regenerating the machine code test programs located in [prog]. For example, to regenerate the machine code for the factorial test program, execute the following:

cd utils && python asm.py -i ../prog/test_factorial.asm

Refer to [doc/ISA.odt] for an overview of the current state of the assembly language and the ISA.

Note: This project is developed and tested using Ubuntu Linux.
