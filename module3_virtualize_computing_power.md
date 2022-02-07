# Virtualize CPU instructions #

## Check your knowledge ##
1. The Set CPU timer instruction from IBM System/370 replaces the CPU internal timer with the contents of a location in memory 
if the CPU is in system mode and traps if it is not. What is the type of this instruction?
__Control Sensitive__

2. The Load Real Address instruction from IBM takes a virtual address and saves the corresponding physical address in a specified general-purpose register. 
The result of the value stored in the register depends on the state of the physical memory resource. What is the type of this instruction?
__Behavior Sensitive__

3. According to Popek and Goldberg's theorem, a hypervisor can be constructed only if:  
__Every sensitive instruction traps to the hypervisor if executed in user mode.__

# Full virtualization vs. paravirtualization #

## Check your knowledge ##
1. Critical instructions are problematic because they are:
__A subset of the set of unprivileged instructions. They can modify the configuration of the system resources and do not trap if executed in user mode.__

2. Can an efficient hypervisor be constructed for an ISA with only one critical instruction? __No__

3. One way to deal with critical instructions is to scan the guest code before execution and replace the critical instructions with traps to the hypervisor. 
In what way is this approach efficient?  __Allows most of the virtual environments to run in user space but without modifying the guest OS__

4. The virtualization approach that executes a set of hypercalls that correspond to critical instructions is called:
__Paravirtualization__

# Implement virtualization by using emulation #

## Check your knowledge ##
1. When the guest and host ISAs are different, the only CPU virtualization mechanism that can be used is:
__Emulation__

2. The process of decoding an instruction only once, saving the extracted information in an intermediate form, 
and reusing the instruction each time it is encountered is called:
__Predecoding__

3. A major limitation of indirect-threaded interpretation is the requirement of looking up a table on each dispatch. 
To get rid of such a level of indirection, it was suggested in 1973 to replace the instruction opcodes contained in 
the intermediate form with the actual addresses of the interpreter routines. What is this method called?
__Direct-threaded interpretation__

4. With predecoding, all the source instructions of the same types are extracted with the same interpretation routine. 
Performance can be significantly enhanced by mapping each individual source binary instruction to its own customized target code. 
This process of converting the source binary program into a target binary program is called:
__Binary translation__

5. Consider the following snippet of an interpreter code that steps through the source program, decodes each instruction 
(that is, the extract() function), and calls a corresponding routine depending on the observed opcode. (All routines are omitted, 
except the first one, for the brevity of the presentation.)

```java
While (!halt && !interrupt)
{
    inst = code[PC];
    opcode = extract(inst, 31, 6);

    switch(opcode)
        {
            case LoadWordAndZero: LoadWordAndZeroRoutine(inst);
            case ALU: ALUrouting(inst);
            case Branch: BranchRoutine(inst);
            ...
        }
}

LoadWordAndZeroRoutine(inst)
{
    RT = extract(inst, 25, 5);
    RA = extract(inst, 20, 5);
    Displacement = extract(inst, 15, 16);
    
    if (RA == 0)
        Source = 0;
    else
        Source = reys[RA];

    address = source + displacement;
    reys[RT] = (data[address] << 32) >> 32;
    PC = PC + 4;
}
```

Which of the following statements best describes the above interpreter?

__This interpreter is a direct-and-dispatch one because it is structured around a central loop, 
a decoder, and a dispatcher. In addition to the test for a halt or an interrupt at the top of the loop, this interpreter exhibits four branches.__

6. Consider the following snippet of an interpreter code.

```java
inst = code[PC];
opcode = extract(inst, 31, 6);

switch(opcode)
    {
        case LoadWordAndZero: LoadWordAndZeroRoutine(inst);
        case ALU: ALUrouting(inst);
        case Branch: BranchRoutine(inst);
    }

LoadWordAndZeroRoutine(inst)
{
    RT = extract(inst, 25, 5);
    RA = extract(inst, 20, 5);
    Displacement = extract(inst, 15, 16);
    
    if (RA == 0)
        Source = 0;
    else
        Source = reys[RA];
    address = source + displacement;
    reys[RT] = (data[address] << 32) >> 32;
    PC = PC + 4;
    
    if (halt || interrupt)
        goto emit;
    
    inst = code[PC];
    opcode = extract(inst, 31, 6);
    extended_opcode = extract(inst, 10, 10);
    routine = displacement[opcode, extended_opcode];
    
    goto *routine
}
...
```
Which of the following statements best describes the above interpreter?

__This interpreter differs from a decode-and-dispatch interpreter as it appends a portion of the dispatch code to the end of each interpreter routine. 
As compared to a decode-and-dispatch interpreter, this interpreter removes tree branches after calling the first interpreter routine. Thus, this interpreter performs faster than a decode-and-dispatch interpreter.__

# Use virtual CPUs #

## Check your knowledge ##

1. What is a virtual machine with a width of 12 called? __A symmetric multiprocessor virtual machine__

2. At different points in time, a vCPU can run at different pCPUs. __True__

3. Assume an SEDF scheduler has the following three vCPUs:
vCPU1: slice = 20 ms and period = 100 ms
vCPU2: slice = 2 ms and period = 10 ms
vCPU3: slice = 5 ms and period = 10 ms
Assume all of the vCPUs are in the ready state. Which of the three vCPUs will be selected next by SEDF? __vCPU3__

4. Assume a machine with one pCPU and a credit scheduler has the following two vCPUs:
vCPU1: weight = 128 and cap = 25%
vCPU2: weight = 256 and no cap
Which of the following statements is correct? __vCPU2 will get twice as much pCPU time as vCPU1 until vCPU1 reaches its cap of 25%.__
