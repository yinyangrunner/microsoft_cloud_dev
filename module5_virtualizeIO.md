# I/O basics #

## Check Your Knowledge ##

1. The CPU and I/O devices can communicate via:  __System I/O instructions documented in ISAs; memory-mapped I/O.__
2. Which of the following sequences of calls would a traditional system use to carry out an I/O operation?  
__Call the system call interface, then the device driver interface, then the operation-level interface.__
4. Memory-mapped I/O:  
__Uses a specific physical memory address space for accessing I/O devices. The memory addresses that belong to this space are recognized by the memory controller as commands to I/O devices.__

# Virtualize I/O devices # 

## Check Your Knowledge ##

1. In a native virtualized system, how many device drivers should be supported for each physical device? __2__

2. In a dual-mode hosted virtualized system, how many device drivers can be supported for each physical device?  __1__

_Correct! Dual-mode hosted virtualized systems collocate the hypervisor with a traditional OS on the same physical machine. 
Thus, the device drivers provided by the host OS can be simply borrowed to handle I/O requests. Guest OSs can delegate I/O requests to the hypervisor, which, in return, can delegate them to the host OS for fulfillment._

3. I/O requests must be intercepted by the hypervisor because they are converted to: __Privileged instructions.__

4. The hypervisor can intercept I/O requests: __At any system interface__

5. Assume two VMs, VM1 and VM2, are running on the same physical machine. If VM1 sends messages to VM2, 
would the hypervisor transmit those messages through the NIC of the physical machine?  __No__

# How Xen does I/O virtualization # 

## Check your knowledge ##

1. How does Xen Project avoid having device drivers for the hypervisor and the guest operating systems?  __By adopting a dual-mode hosted virtualized system and using only the device drivers defined at the host OS__
2. In Xen, would every domain be vacant of virtual I/O devices and relevant drivers, including domain 0?  __Yes__
