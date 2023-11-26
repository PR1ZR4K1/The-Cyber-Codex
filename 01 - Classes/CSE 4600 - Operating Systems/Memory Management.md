2023/10/23 10:35
Status: #idea
Tags:

# Memory Management

## Background Key Points

- Program Must be brought (from disk) into memory and placed within a process for it to be run.
- Main memory and registers are only storage CPU can access directly
- Memory unit only sees a stream of:
	- addresses + read requests, or
	- address + data and write requests
- Register access is done in one CPU clock (or less)
- Main memory can take many cycles, causing a stall
- Cache sits between main memory and CPU registers
- Protection of memory is required to ensure correct operation

## Memory Hierarchy

![[memory hierarchy.png]]

## Memory Management Goals

### Allocation
- Allocation, replacement

### Arbitration
- Address translation and validation
- Maps physical memory addresses to virtual address which is what is given to the process. This is called swapping
- ![[memory abstraction.png]]

## Memory Management Unit (MMU)

Hardware device that at run time maps virtual to physical address. Reports faults: illegal access, permission, not present in MM.

*Registers:*
- Pointers to page table
- Base and limit size, number of segments

*Cache - Translation Lookaside Buffer (TLB)*
- Virtual address to physical address translation

*Translation:*
- Physical Address generation done in hardware

![[Pasted image 20231023111751.png]]

Using a base and limit registers you can compute the actual memory space that a process is allowed to operate in. If the process goes beyond this boundary either above or below you will reach a fault, process will be killed, etc.

Simple diagram demonstrating the logic behind limit and base registers:
![[Pasted image 20231023112026.png]]

## Binding of Instructions and Data to Memory

Address binding of instructions and data to memory addresses can happen at three different stages

  
*Compile time (Typical of Old OS):* 
- If memory location is known prior, absolute code can be  generated; must recompile code if starting location changes

*Load time (Typical of Modern OS):* 
- Must generate relocatable code if memory location is not  known at compile time

*Execution time (Used when necessary):* 
- Binding delayed until run time if the process can be moved during its execution from one memory segment to another  
- Need hardware support for address maps (e.g., base and limit registers

## Variable Partition

- Degree of multi-programming limited by number of partitions Variable-partition sizes for efficiency (sized to a given process’ needs)

- Hole – block of available memory; holes of various size are scattered throughout memory

- When a process arrives, it is allocated memory from a hole large enough to accommodate it

- Process exiting frees its partition, adjacent free partitions combined

- Operating system maintains information about:
a) allocated partitions b) free partitions (hole)

## Dynamic Storage-Allocation Problem

How to satisfy a request of size *n* from a list of free holes?

**First-Fit:** Allocate the *first* hole that is big enough

**Best-Fit:** Allocate the *smallest* hole that is big enough; must search entire list, unless ordered by size

**Worst-Fit:** Allocate the *largest* hole; must also search entire list

*First and best-fit are better than worst-fit in terms of speed and storage utilization*

## Fragmentation

Segmentation causes external fragmentation and Paging can cause internal fragmentation

**External Fragmentation:** 
- total memory space exists to satisfy a request, but it is  not contiguous  

**Internal Fragmentation:** 
- allocated memory may be slightly larger than requested  memory; this size difference is memory internal to a partition, but not being use

#### Compaction

Reduce external fragmentation by compaction

- Shuffle memory contents to place all free memory together in one large block
- Compaction is possible *only* is relocation is dynamic, and is done at execution time
- I/O problem

Not the best approach since it takes many CPU cycles to do this for each process which means it would occur in microseconds.

## Paging

Physical address space of a process can be non-contiguous; process is allocated physical memory whenever the latter is available. Avoids External Fragmentation and problem of varying sized memory chunks

### Address Translation Scheme

**Page Number (p):** 
- used as an index into a page table which contains base address of each page in physical memory  
**Page Offset (d):**
- combined with base address to define the physical memory address that is sent to the memory unit  
- For given logical address space $2^m$ and page size $2^n$

### Paging Hardware

Page number tells us which frame this page corresponds to. The offset tells us  [P | D] 
- P - typically referred to as <mark style="background: #FFF3A3A6;">virtual page number</mark> (VPN) and is used to tell us which frame the page is mapped to
- D - Tells us which instruction from that page we are on. AKA the <mark style="background: #FFF3A3A6;">offset</mark>. Which when combined with the VPN tells us which instruction that page is on.

![[Pasted image 20231023114258.png]]

## Key Points on Paging

Equal size pages on the virtual address space (<mark style="background: #FFF3A3A6;">virtual pages</mark>)
At the physical memory size they are of equal size and they are called <mark style="background: #FFF3A3A6;">frames</mark>

*Page Table:*
Translates logical to physical addresses
Corresponds pages to frames :)

### Swapping

Reclaims unused pages so that its space can be taken up by a page that is or will be in use. Each virtual page has a valid bit which is either 0 or 1 and corresponds to whether or not the frame exists in the memory or not. If it is not in use then OS will create a fault to clear that process/

### How to calculate page table size

![[Pasted image 20231025110204.png]]

`(VPN / Page Size) * Page Table Entry`

Essentially this would be impossible to keep up with

## Hierarchical Page Tables

Two level page table. This is actually gross.

Chat GPT Explanation:

1. **Top-Level Directory**: This is like the main folder on your computer. It doesn't contain the files you need, but it points you to sub-folders.
    
2. **Sub-Folders**: These are the next level down. They further categorize where things are stored, and they can point you to more specific folders or the actual files.
    
3. **Files**: These are the actual pieces of data you're looking for.
    

By using this multi-level approach, the system can quickly find the exact piece of data it needs without having to search through everything. It's a way to keep things organized and speed up access times.

![[Pasted image 20231025110725.png]]

 


---
# References
