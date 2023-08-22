# ASIC_PES-CLASS

ASIC PHYSICAL DESIGN
Mentor- Kunal Ghosh

## CONTENT :
- [DAY 1]()

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















