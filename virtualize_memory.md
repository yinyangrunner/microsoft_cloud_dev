# One Level Page Mapping #

## Check Your Knowledge ##

1. In traditional virtual memories, each process is provided with: __A virtual address space with a page table.__
2. Assume a system has a 64-KB virtual address space, 32 KB of physical memory, and a page size of 4 KB. 
If the virtual and physical pages are of the same size, how many virtual and physical pages will such a system contain? __16 and 8 virtual and physical pages, respectively__

    > ### Virtual Space ###
    > 64Kb = 65536 Bytes (Binary) = 2^16 Bytes
    > 
    > ### Physical Memory ###
    > 32Kb = 332768 Bytes (Binary) = 2^15 Bytes
    > 
    > ### Page Size ###
    > 4Kb = 4096 Bytes = 2^12
    > 
    > 2^16/2^12 = 2^4 = __16 pages in virtual address space__
    >
    > 2^15/2^12 = 2^3 = __8 pages in virtual address space__
    >
3. One-level page mapping as employed by traditional OSs entails: __Virtual-to-physical address translation__
