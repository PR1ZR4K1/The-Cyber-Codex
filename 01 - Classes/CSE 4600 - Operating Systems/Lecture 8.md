2023/10/16 10:48
Status: #idea
Tags:

# Inter-process Communication (IPC)

*Is a set of methods by which different processes running on a computer communicate with each other to coordinate tasks and share resources.*

## IPC Methods

1. **Pipes**:
    
    - **Ordinary Pipes (Anonymous Pipes)**: Allow one-way communication between a parent and child process.
    - **Named Pipes**: Provide one-way or duplex communication (bidirectional)between two processes, even if they are not related.
2. **Message Queuing**:
    
    - Systems like Message Queue Interface (MQI) allow processes to communicate by sending and receiving messages without being directly connected.
3. **Shared Memory**:
    
    - A segment of memory is made accessible to multiple processes, allowing them to communicate by reading from and writing to that memory segment.
4. **Sockets**:
    
    - Sockets provide bidirectional communication between processes, possibly running on different machines over a network. They're the basis for much of internet communication.
5. **Semaphores**:
    
    - A synchronization mechanism used to control access to shared resources by multiple processes.
6. **Signals**:
    
    - A way to notify a process that a specific event has occurred.
7. **Files**:
    
    - Processes can communicate by reading from and writing to files, though it's less direct and often slower than other methods.
8. **Remote Procedure Calls (RPC)**:
    
    - Allows a program to cause a procedure to run in another address space, which could be on another computer.
9. **Memory-mapped Files**:
    
    - Allows multiple processes to interact with the same file content in memory, facilitating data sharing between them.
10. **Synchronization Primitives (like Mutexes, Condition Variables)**:
    

- Used to coordinate the operation of multiple processes based on the availability of resources.



## Micro-kernel System Structure

![[Pasted image 20231016105053.png]]




---
# References
