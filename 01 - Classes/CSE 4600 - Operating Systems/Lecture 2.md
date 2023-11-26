*What is a Process?*
A program in execution. process execution must progress in  
sequential fashion. No parallel execution of instructions of a single process

*Which process is the Mother of All Processes (MOAP)?*
<mark style="background: #ABF7F7A6;">MOAP = init()</mark>

*Process Creation fork()*
- Each time you use fork on a process the parent process is copied to a child process.
- Every time you use fork the number of processes doubles.

**1. Process Concept**: 
![[C Memory Layout.png]]
	There are multiple parts to a process
	
	- Text Section; the program code
	- [[Program Counter (PC)]]; Current activity or process registers
	- Stack; containing temporary data, function parameters, return addresses
	- Data Section; containing global data
	- Heap; containing memory that is dynamically allocated during run time

- Hardware is managed on behalf of the processes (being executed)
- Applications are static entities that are located somewhere on the storage drive. 
- When the application is launched it gets loaded into memory and becomes a process since it is a program in execution.

**2. Process Address Space and Memory Management**:

- Page table: mapping of virtual address to physical address which are two different addresses. It is not mapped one to one.
- ![[Process Address Space.png]]
	- OS does this in order to maintain security. The OS is never directly interacting with the physical address space of the memory.
- 

**3. Process Control Block (PCB)**: Allocates portion of memory from a low to high range for a process to run in.

- *How is PCB used?*
	- User Applications
	- System Processes
	- Used to switch the context from one application to another
	- The OS will save the PCB of the former and all of the states of the system processes for that application and will restore the PCBs of the other process.
	- This process happens in nano-seconds.
	- ![[PCBs.png]]

**4. Process Scheduling**:
**5. Operations on Processes**:

---

# See Also

- *[[Process Control Block]]*
