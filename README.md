# ASIC_PES-CLASS

ASIC PHYSICAL DESIGN
Mentor- Kunal Ghosh

## CONTENT :
- [DAY 1](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-1)
- [DAY 2](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-2)
- [DAY 3](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-3)
- [DAY 4](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-4)

## DAY 1
* Introduction to RISC-V ISA and GNU compiler toolchain , The C-program is converted into Assembly Code( here for RISC-V processor). Then the assembly code is converted into binary. An RTL implements this code for the particular layout of the RISC-V processor and the output is visible.
* Create a simple C program That calculates sum from 1 to N -> sum_1_to_N.c .
### 1. CODE :
<img width="299" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/76d9aac4-9f31-4113-a5c1-81a02c17e81b">

__Commands to compile and run c code in normal compiler__

```
gcc (filename).c
./a.out
```

### NORMAL COMPILER :
<img width="312" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/4dd335eb-a195-4c16-99e2-19b6c67e1137">

__Commands to compile and run c code in RISK compiler__

```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o (filename).o (filename).c
riscv64-unknown-elf-objdump -d (filename).o | less
```


### RISK COMPILER :
<img width="617" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/9d230df6-c2a2-4eb0-a1bc-7911c5f8c4c8">
<img width="617" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/cfd9db7c-b902-432e-8684-cbbd243b575a">

### SPIKE SIMULATION AND DEBUGGER :
```spike pk (filename).o```is a command similar to ```./a.out``` and is used to show the output of the risk compiler.

<img width="677" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/e8ae3654-7c2d-404f-8e69-0d840bdadb46">

```spike -d pk (filename).c``` is a command used for debugging , it shows what is stored in the registers .

<img width="751" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/899f1c5a-19cd-4628-a997-82e4d8276c81">

* Pressing Enter goes to next succesive line.
* Writing reg 0 a1 or any other reg value gives what is stored in it.
* To Quit the debugger press on q.

### 2. CODE for highest and lowest signed and unsigned integers:
<img width="624" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/f54238ee-88a0-4215-be32-2d4b62327d8d">

### OUTPUT :
<img width="423" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/b6fb963c-022c-41bd-b4ed-159543bc91da">

## DAY 2
### APPLICATION BINARY INTERFACE :
* An Application Binary Interface (ABI) is a set of rules and conventions that dictate how binary code interacts with and communicates with other binary code, typically at the level of machine code or compiled code.

* It defines the interface between two software components or systems that are written in different programming languages, compiled by different compilers, or running on different hardware architectures.

* When an application needs to use the harware resources of a system it is working on, it uses these resources with the help of system calls. These system calls are performed through an interface called the Application Binary Interface(ABI). It is also called the System Call Interface.

### MEMORY ALLOCATION FOR DOUBLE WORDS :
64-bit number (or any multi-byte value) can be loaded into memory in little-endian or big-endian. It involves understanding the byte order and arranging the bytes accordingly

* Little-Endian: In little-endian representation, you store the least significant byte (LSB) at the lowest memory address and the most significant byte (MSB) at the highest memory address.

* Big-Endian: In big-endian representation, you store the most significant byte (MSB) at the lowest memory address and the least significant byte (LSB) at the highest memory address.

### LOAD, ADD AND STORE INSTRUCTIONS :
1. Load Instructions:
  Load instructions are used to transfer data from memory to registers. They allow you to fetch data from a specified memory address and place it into a register for further processing.

  Some Examples-
- `ld` is the load double-word instruction.
- `x6` is the destination register.
- `8(x5)` is the memory address pointed to by register `x5` (base address + offset).
2. Store Instructions:
  Store instructions are used to write data from registers into memory.They store values from registers into memory addresses

  Some Examples-
- `sd` is the store double-word instruction.
- `x8` is the source register.
- `8(x9)` is the memory address pointed to by register `x9` (base address + offset).
3. Add Instructions:
  Add instructions are used to perform addition operations on registers. They add the values of two source registers and store the result in a destination register.

  Some Examples-
- `add` is the add instruction.
- `x9` is the destination register.
- `x10` and `x11` are the source registers.

### ABI NAMES :
ABI names for registers serve as a standardized way to designate the purpose and usage of specific registers within a software ecosystem. These names play a critical role in maintaining compatibility, optimizing code generation, and facilitating communication between different software components. RISC-V RV64 architecture has 32 general-purpose registers.

<img width="319" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/c3b662e5-220e-487b-948b-54fe32c6b610">

### SUM OF NUMBERS FROM 1 TO N USING ASM:

#### CODE :
1to9_custom.c file -

<img width="517" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/473cb257-2648-4120-a00a-e5f7cdb41253">

load.s file -

<img width="517" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/b1f93a2b-2900-4a00-87c2-8e8f00e3ecbc">

#### OUTPUT :

<img width="891" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/9726e76e-1afc-42fc-8726-a7cde70a4f9b">

### STEPS TO RUN C CODE ON RISC-V :

`git clone https://github.com/kunalg123/riscv_workshop_collaterals.git`

`cd riscv_workshop_collaterals`

`ls -ltr`

`cd labs`

`ls -ltr`

`chmod 777 rv32im.sh`

`./rv32im.sh`

#### OUTPUT :

![image](https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/2f29b026-8c15-410e-a18a-433caeb0f11b)

## DAY 3
### LABS USING YOSYS AND SKY130 PDK :

**RTL Design**: In simple terms RTL design or Register Transfer Level design is a method in which we can transfer data from one register to another. In RTL design we write code for Combinational and Sequential circuits in HDL(Hardware Description Language) like Verilog or VerilogHDL which can model logical and hardware operation.

**Test Bench**: Using Verilog we can write a test bench to apply stimulus to the RTL design and verify the results of the design by instantiating design with in test bench. Up-front verification becomes very important as design size increases in size and complexity while any project progresses. This ensures simulation results matches with post synthesis results.

**Simluator**: Simulator is the tool used for this process. It looks for changes on input signals to evaluate outputs. No change in output if there is no change in input signals.

<img width="815" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/6e1eca88-aaec-483c-b830-78f163da0fe6">

**iverilog**: iverilog stands for Icarus Verilog. Icarus Verilog is an implementation of the Verilog hardware description language.

<img width="887" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/fd82d360-da4d-463f-9f79-12dafcff1c21">

#### Lab examples using iverilog and gtkwav:
**Commands to run the code**:

<img width="906" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/a5614629-b94e-47ac-83d2-3fd70a1dd57e">

**Output**:

<img width="925" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/09e21d0b-7b66-4995-94b3-cb872956f289">

**Code**:

<img width="922" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/893ee372-1633-4aaf-b009-d71bbb0c7fd2">

#### Using YOSYS synthesizer :
<img width="903" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/8ff77a55-1ce5-46a7-9341-2b45bb80eac7">

**Yosys**: Yosys is a framework for RTL synthesis and more. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application domains. Yosys is the core component of most our implementation and verification flows.

<img width="612" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/6723dc3f-8bd2-4397-9ee4-9d82248af091">

**Synthesizer**: It is a tool we use to convert out RTL design code to netlist.

<img width="672" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/b24b1242-1955-4fd1-8cdc-cd13928e31b7">

Below are the commands to perform above synthesis.

- RTL Design  - read_verilog
- .lib        - read_liberty
- netlist file- write_verilog

<img width="638" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/f2cad5a9-8471-4b29-a845-f4a839f49aae">

- Clock to Q of flipflop A
- Propagation delay of combinational circuit
- Setuptime of flipflop B

<img width="288" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/bfec632e-17fc-4a6b-a972-2c1fb461d2a1">

Formula :

<img width="227" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/fadead63-52ac-4a50-a693-b63a59d5a537">

**YOSYS** :

Command to read form which director in yosys :
```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="425" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/79bab388-2076-4167-b39c-98462a37e576">

Command to read the code :
```
read_verilog (filename).v
```

<img width="289" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/027240e4-5f22-474a-b3de-0707449a4e7d">

Command to run the code :
```
synth -top (filename)
```

<img width="297" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/b47660e4-6285-4e9b-b418-f0b4c16b3ade">

Command to generate the netlist :
```
abc -liberty ../my_lib//lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

<img width="267" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/6d82898e-47c3-4997-9b06-b6b000e55e86">

Command to show synthesized design :
```
show
```
<img width="299" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/546fbd53-5137-479e-9c2e-271da9a57168">

Command to check netlist file :
```
write_verilog good_mux_netlist.v
!gedit good_mux_netlist.v
```
<img width="449" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/d5e14b5d-079d-47f8-a643-313d71292056">

For neater netlist:```write_verilog -noatrr good_mux_netlist.v```

<img width="449" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/68ea1899-7195-482d-8e7a-aed2d40035fa">

## DAY 4
### INTRODUCTION TO TIMING DOT LIBS :
We use command ```gedit ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib``` to view the content in the file.

<img width="927" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/52f26036-c21f-410e-8b86-1b8460b5b41a">


*Sky130 is a 130nm library , here 130nm refers to the channel lenght of the mosfet.
*"tt" refers to typical ,they can be faast or slow libraries.
*025c is the temperature.
*1v9 refers to the voltage.
*PVT is PROCESS VOLTAGE TEMPERATURE.
*Some more parameters :

<img width="259" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/fdd4a5d8-f526-4fdd-879d-698fc27afc33">

<img width="619" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/96e8e332-c009-47f5-90fd-a23109a7d7d4">

Leakage power consumption is the power consumed by the sub threshold currents and by reverse biased diodes in a CMOS transistor.
### HIERARCHIAL VS FLAT SYNTHESIS:
Hierarchical Synthesis Hierarchical synthesis is an approach in digital design and logic synthesis where complex designs are broken down into smaller, more manageable modules or sub-circuits, and each module is synthesized individually. These synthesized modules are then integrated back into the overall design hierarchy. It is like modularization in c which makes it much simpler to understand the code.


  














































