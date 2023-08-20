# ASIC_PES-CLASS

ASIC flow course
Mentor- Kunal Ghosh

## DAY1
* Introduction to RISC-V ISA and GNU compiler toolchain , The C-program is converted into Assembly Code( here for RISC-V processor). Then the assembly code is converted into binary. An RTL implements this code for the particular layout of the RISC-V processor and the output is visible.
* Create a simple C program That calculates sum from 1 to N -> sum_1_to_N.c .
### CODE:
<img width="299" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/76d9aac4-9f31-4113-a5c1-81a02c17e81b">

__Commands to compile and run c code in normal compiler__

```
gcc (filename).c
./a.out
```

### NORMAL COMPILER:
<img width="312" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/4dd335eb-a195-4c16-99e2-19b6c67e1137">

__Commands to compile and run c code in RISK compiler__

```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o (filename).o (filename).c
riscv64-unknown-elf-objdump -d (filename).o | less
```


### RISK COMPILER:
<img width="617" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/9d230df6-c2a2-4eb0-a1bc-7911c5f8c4c8">
<img width="617" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/cfd9db7c-b902-432e-8684-cbbd243b575a">

### SPIKE SIMULATION AND DEBUGGER
```spike pk (filename).o```is a command similar to ```./a.out``` and is used to show the output of the risk compiler.

<img width="677" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/e8ae3654-7c2d-404f-8e69-0d840bdadb46">

```spike -d pk (filename).c``` is a command used for debugging , it shows what is stored in the registers .
<img width="751" alt="image" src="https://github.com/FF-Industries/ASIC_PES-CLASS/assets/136846161/899f1c5a-19cd-4628-a997-82e4d8276c81">

* Pressing Enter goes to next succesive line.
* Writing reg 0 a1 or any other reg value gives what is stored in it.
* To Quit the debugger press on q.









