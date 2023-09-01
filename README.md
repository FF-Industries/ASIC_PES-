# ASIC_PES-CLASS

ASIC PHYSICAL DESIGN
Mentor- Kunal Ghosh

## CONTENT :
- [DAY 1](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-1)
- [DAY 2](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-2)
- [DAY 3](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-3)
- [DAY 4](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-4)
- [DAY 5](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-5)
- [DAY 6](https://github.com/FF-Industries/ASIC_PES-CLASS/blob/main/README.md#day-6)

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
### HIERARCHIAL VS FLAT SYNTHESIS :
Hierarchical Synthesis Hierarchical synthesis is an approach in digital design and logic synthesis where complex designs are broken down into smaller, more manageable modules or sub-circuits, and each module is synthesized individually. These synthesized modules are then integrated back into the overall design hierarchy. It is like modularization in c which makes it much simpler to understand the code.

* We us a file called multiple-modules.v.
* There are two modules one for and gate and other for or gate and they are instantiated in the same file.
<img width="449" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/f55a137a-a7f4-486f-a10a-b3545ba5d73b">

* Launch yosys
* Command to read library file : ```read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib ```

<img width="437" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/e2ffa9c4-967f-4217-86b4-f802174de9f5">

* Command to read verilog file : ``` read_verilog multiple_modules.v ```

<img width="339" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/c1d48fce-ac74-41e0-9067-16f42620eb9d">

* Command to set it as top module : ```synth -top multiple_modules```
<img width="176" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/efbe647a-6757-41a8-8b78-77a827ff42a6">

* Command to show netlist ```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib``` and ```show multiple_modules ```

<img width="302" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/6cddbbac-4fe7-4ac0-bc93-17167734100b">

* As we can see there are two modules here replacing the and gate and the or gate.
* Do ```write_verilog -noattr multiple_modules_hier.v``` then ```!gedit multiple_modules_hier.v```

<img width="427" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/a4da5d60-427b-4931-a617-2fbc8ede8525">

<img width="427" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/0aaf8d87-c88d-4d62-ba14-62fc351d1b2c">

<img width="427" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/0764b55c-d4f7-4328-a4a5-0daf1f75405b">

Flattened Synthesis Flattened synthesis is the opposite of hierarchical synthesis. Instead of maintaining the hierarchical structure of the design during synthesis, flattened synthesis combines all modules and sub-modules into a single, flat representation.

* Following the same steps till abc command then we do command ```flatten```and then ```show```.

<img width="638" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/cd25b63a-4465-4ec6-81e2-08b1b07f2df1">

* Then do ```write_verilog -noattr multiple_modules_flat.v``` then ```!gedit multiple_modules_flat.v```

<img width="854" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/0b89095a-1333-4a96-953f-6a1405d6e551">

### Various Flop Coding Styles and Optimization :
* Flops are fundamental parts of digital circuits that help in preventing glitches and thereby endure smooth operation of the circuit.
* During the propagation of data, if there are different paths with different propagation delays, then a glitch might occur.
* Flops help prevent glitches by providing a control and synchronization for holding and propagating changes in signals in the circuit.

#### D Flip-Flop with Asynchronous Reset
* When the reset is high, the output of the flip-flop is forced to 0, irrespective of the clock signal.
* File is ```!gedit dff_asyncres_syncres.v```.

<img width="438" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/bb990bfa-16f6-490e-a0b2-f8e01703c686">

**Simulation -**
```
cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files
iverilog dff_asyncres.v tb_dff_asyncres.v
./a.out
gtkwave tb_dff_asyncres.vcd
```

<img width="866" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/ec770041-230d-453b-aa7e-ab5fa519a6f2">

**Synthesis -**
```
cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files
yosys
read_liberty -lib ../my-lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_asyncres.v
synth -top dff_asyncres
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="709" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/b28aa074-e13e-4b00-8131-18b9d442d6c5">

#### D Flip_Flop with Asynchronous Set
* When the set is high, the output of the flip-flop is forced to 1, irrespective of the clock signal.
* File is ```!gedit dff_async_set.v```

<img width="410" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/b2d7fe69-eb59-4fa2-9b43-3deadc621494">

**Simulation -**
```
cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files
iverilog dff_async_set.v tb_dff_async_set.v
./a.out
gtkwave tb_dff_async_set.vcd
```

<img width="867" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/245ace6b-c213-4068-b665-28bb4e7bd6ed">

**Synthesis -**
```
cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files
yosys
read_liberty -lib ../my-lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_async_set.v
synth -top dff_async_set
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="765" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/e72457f1-3582-4509-8039-a9921c0f88c2">

#### D Flip-Flop with Synchronous Reset
* When the reset is high on the positive edge of the clock, the output of the flip-flop is forced to 0.
* File is ```!gedit dff_syncres.v```

<img width="439" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/0a0bfd0e-88b9-46ee-9371-c2f9cfd205bb">

**Simulation -**
```
cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files
iverilog dff_syncres.v tb_dff_syncres.v
./a.out
gtkwave tb_dff_syncres.vcd
```

<img width="867" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/807081ea-e867-42b4-8623-4bd4045b24fc">

**Synthesis -**
```
cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files
yosys
read_liberty -lib ../my-lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_syncres.v
synth -top dff_syncres
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="633" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/bcd0d933-be27-4d09-8498-75137aed7dae">

#### D Flip-Flop with Asynchronous Reset and Synchronous Reset
* When the asynchronous resest is high, the output is forced to 0.
* When the synchronous reset is high at the positive edge of the clock, the output is forced to 0.
* File is ```!gedit dff_asyncres_syncres.v```

<img width="425" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/9f6475e2-eb40-46d1-b539-dd11c54fdbf2">

#### Intresting Optimizations

* `!gedit mult_2.v`

<img width="448" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/6046fb40-a73b-430e-9b6e-38e055d6b740">

* `read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
* `read_verilog mult_2.v`
* `synth -top mul2`

<img width="215" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/34780051-bdbb-4524-bc02-cc6624bcbdf6">

* `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
* `show`

<img width="301" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/00e56d5c-9206-40e9-80c7-099b968bfbb4">

* `write_verilog -noattr mul2_netlist.v`
* `!gedit mul2_netlist.v`
  
<img width="326" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/64eacad1-3e64-4661-b61b-f8617c1890fe">


* `!gedit mult_8.v`

<img width="331" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/af3275a6-943d-4e80-ab33-bd4748c9c268">

* `read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib  `
* `read_verilog mult_8.v`
* `synth -top mult8`
  
<img width="291" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/9aff0c90-8a5a-485c-b34a-aad6724a2087">

* `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
* `show`

<img width="296" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/b96de6dc-7085-49c5-b4cb-8afd921a2e64">

* `write_verilog -noattr mult8_netlist.v`
* `!gedit mult8_netlist.v`

<img width="296" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/8eccfea0-2ead-4d9f-a83c-1b3796a11a32">

## DAY 5
### INTRODUCTION TO OPTIMISATIONS :
#### Combinational Logic Optimisations
* Combinational logic refers to logic circuits where the outputs depend only on the current inputs and not on any previous states.Optimising the combinational logic circuit is squeezing the logic to get the most optimized digital design so that the circuit finally is area and power efficient.
 
**opt_check -**
```
!gedit opt_check.v
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check.v
synth -top opt_check
opt_clean -purge
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="450" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/65aab33a-3dd8-4bc6-9edf-b43aff9a1008">

<img width="193" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/26079818-2639-41fd-bd1e-e6dd0a55d6ba">

<img width="302" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/c632da06-0056-48ed-a3cd-f82877e8ef3a">

**opt_check2 -**
```
!gedit opt_check2.v
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check2.v
synth -top opt_check2
opt_clean -purge
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="450" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/dcf95eb0-9914-4c87-a68a-0372e9792014">

<img width="199" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/e03e8cf5-4dc3-4af7-a53d-64275e64232d">

<img width="302" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/19c6c5e3-2ad8-4e55-8a31-9675b8efe548">

**opt_check3 -**
```
!gedit opt_check3.v
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check3.v
synth -top opt_check3
opt_clean -purge
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="448" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/01dfd5a8-0e3e-4d38-af8f-503ffff3d910">

<img width="185" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/3bd08fda-2247-41b2-88d6-f0c0eb7c4f25">

<img width="302" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/200ec214-8e2a-44ef-b7f8-9b9fb217b67d">

**opt_check4 -**
```
!gedit opt_check4.v
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check4.v
synth -top opt_check4
opt_clean -purge
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="446" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/eb6eda1d-c2ed-47da-aff8-24b43954bde0">

<img width="187" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/a827ddff-9be2-473d-9d43-de933b3218a2">

<img width="296" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/a28113aa-987b-4ff6-b627-b136252cc981">


**multiple_module_opt -**
```
!gedit multiple_module_opt.v
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_module-opt.v
synth -top multiple_module_opt
opt_clean -purge
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
<img width="448" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/3e4a9286-e58f-4340-bbc3-73d255798d3c">

<img width="183" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/aec71efc-b65c-4897-b076-ff3bb541e336">

<img width="301" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/78072dd0-896e-43d4-bf39-23fea00f1f09">


#### Sequential Logic Optimisations
* Sequential logic optimizations involve improving the efficiency, performance, and resource utilization of digital circuits that include memory elements like flip-flops and latches.

**dff_const1**

Simulation -

```
gedit dff_const1.v
iverilog dff_const1.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const1.vcd
```

![image](https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/259679e2-cd71-428b-8c61-f7097353d713)

<img width="634" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/8f320155-0562-4838-9c82-1f6cb44c372e">

Synthesis -

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const1.v
synth -top dff_const1
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="182" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/64db811d-3ef8-46f2-bbed-cb4a78069866">

<img width="302" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/09a7e39b-98fa-4c07-85a7-6a0ddb3ee812">

**dff_const2**

Simulation -

```
gedit dff_const2.v
iverilog dff_const2.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const2.vcd
```

<img width="446" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/47321c6f-59c3-430e-8db0-30936570ca48">

<img width="649" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/a4dbb0ea-a7cc-494d-a66b-a1cf924b7e30">

Synthesis -

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const2.v
synth -top dff_const2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="192" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/2ec0bc79-277c-4659-ae17-d42f8bc9a4f1">

<img width="298" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/fcf87f94-858c-4cda-b8d1-1d31189957d2">

**dff_const3**

Simulation -

```
gedit dff_const3.v
iverilog dff_const3.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const3.vcd
```

<img width="447" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/e6ccc9f3-b9a9-4ef9-9558-02f25dba9afe">

<img width="672" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/0d4f3789-e7bf-4514-ac9c-8e5bef38e143">

Synthesis -

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const3.v
synth -top dff_const3
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="199" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/0c0763e0-6546-4bfa-831a-71c631cf1048">

<img width="513" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/b881c14a-d309-488d-a001-9afa49a6b5b8">

**dff_const4**

Simulation -

```
gedit dff_const4.v
iverilog dff_const4.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const4.vcd
```

<img width="446" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/e6bd4630-fc17-43a8-8b56-965cca2c719e">

<img width="677" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/12ed5633-38e7-49d1-bbfc-3c4117eb7581">

Synthesis -

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const4.v
synth -top dff_const4
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="192" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/df88a549-db3f-4fb6-a6ef-619872e7e8c3">

<img width="295" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/216c8cce-9726-4732-b99a-d45061caaec1">

**dff_const5**

Simulation -

```
gedit dff_const5.v
iverilog dff_const5.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const5.vcd
```

<img width="449" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/eb7ec738-f0ba-446e-8fd7-e6f72530df43">

<img width="676" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/fd0b7243-4b4a-49a4-a90d-82912b604d07">

Synthesis -

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const5.v
synth -top dff_const5
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="184" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/022efb47-9679-4994-8aa7-50038a9406ea">

<img width="505" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/6c197941-a80c-4f31-a953-79823f69eb60">

**counter_opt**

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt.v
synth -top counter_opt
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="445" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/90acebe7-0710-424e-852a-c2b8fcbc5ba2">

<img width="184" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/15ba6a49-cdb9-49fd-943b-96dd54cd80cd">

<img width="587" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/cd85b701-5615-4aa8-9719-286c19aaf79e">

**counter_opt2**

```
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt2.v
synth -top counter_opt2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

<img width="444" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/76014a68-b5cb-4e2c-9420-c544283c7645">

<img width="133" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/60b26e37-a1fb-4c62-a1f4-632cc32623e4">

<img width="683" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/c13fd42e-3146-4d2d-accf-7b447a9c22c5">

## DAY 6











 
 












  














































