# One-Level Page Mapping #

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

# Two-Level Page Mapping #

## Check Your Knowledge ##

1. Two-level page mapping, as employed by system memory virtualization, entails:  __Virtual-to-real and then real-to-physical address translations__
    
    _Correct! Page tables in guest OSs perform virtual-to-real address translations, and page tables in the hypervisor (called real page tables) perform real-to-physical address translations. Two-level page mapping assumes a native virtualized system._

# Memory Overcommitment #

## Check Your Knowledge ##

1. Memory overcommitment implies that: __The combined total size of the real memories is greater than the size of the physical memory.__

2. Assume a hypervisor does not employ memory overcommitment. Assume also a physical memory of 9 GB. What is the maximum number of virtual machines that can be provisioned on such a hypervisor if the real memory of each VM should be at least 3 GB?  __2VMs__

3. Assume a hypervisor employs memory overcommitment. To avoid information leaking among virtual machines during page reclamations, the hypervisor will: __Erase every reclaimed page irrespective of whether it's been used previously.__

# Reclaiming memory and memory issues #

## Check Your Knowledge ##

1. True or false? The hypervisor can automatically reclaim pages when deactivated by guest OSs.  __False__
2. Consider the following memory state as imposed by two VMs running on a single physical host: 

![Diagram showing the memory state of a hypervisor with blocks corresponding with two virtual machines, VM1 and VM2. From left to right, the hypervisor shows a pinned page from VM1, then a pinned page from VM2, then a pinned page from VM1, then two pinned pages from VM2, and lastly a pinned page from VM1. VM1 has a sub block with one pinned page and one unlinked pinned page. VM2 has a sub block with two unlinked pinned pages.](https://docs.microsoft.com/en-us/learn/cmu-cloud-developer/cmu-virtualize-memory/media/quiz-memory-state.png)

_Diagram showing the memory state of a hypervisor with blocks corresponding with two virtual machines, VM1 and VM2. From left to right, the hypervisor shows a pinned page from VM1, then a pinned page from VM2, then a pinned page from VM1, then two pinned pages from VM2, and lastly a pinned page from VM1. VM1 has a sub block with one pinned page and one unlinked pinned page. VM2 has a sub block with two unlinked pinned pages._

Assume that the shown hypervisor employs a ballooning process. How would the hypervisor recognize inactive pages to reclaim them?  
__By inflating the balloon at the hypervisor__

3. How many pages in total can the hypervisor reclaim when applying the ballooning process?  __6__
