 
2023/09/27 11:22
Status: #idea
Tags: [[Lecture 2]]

# Process Control Block

A Process Control Block (PCB) is a data structure maintained by the Operating System for every process. The PCB contains important information about the specific process it represents, facilitating the OS in managing and scheduling processes efficiently.

## Typically Includes

1. **Process Identifier (PID):**
    
    - A unique ID assigned to each process for identification.
2. **Process State:**
    
    - The current state of the process (e.g., ready, running, waiting, terminated).
3. **Program Counter:**
    
    - The address of the next instruction to be executed for this process.
4. **CPU Registers:**
    
    - The values of the CPU registers when the process is paused. This is necessary to continue the process execution correctly once it's resumed.
5. **CPU Scheduling Information:**
    
    - Priority of the process, scheduling queue pointers, and other scheduling parameters.
6. **Memory Management Information:**
    
    - Information about the process’s address space, page tables, segment tables, etc.
7. **Accounting Information:**
    
    - Usage of processing time, time limits, account numbers, etc.
8. **I/O Status Information:**
    
    - List of I/O devices allocated to the process, a list of open files, etc.

## Purpose

The primary purpose of the PCB is to hold the information needed to keep track of a process as it transitions between states, and to enable the OS to manage and schedule processes effectively. By maintaining a PCB for each process, the OS can quickly suspend active processes, resume paused ones, allocate and deallocate resources, and manage process execution, ensuring smooth and efficient system operation.



---
# References
