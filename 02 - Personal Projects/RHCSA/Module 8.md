2024/01/31 19:19
Status: #idea
Tags:

# Monitor and Manage Linux Processes

## What is a process?

A *process* is a running instance of a launched, executable program. It contains:

- An address space of allocated memory
- Security properties, including ownership credentials and privileges
- One of more execution threads of program code
- A process state

The *environment* of a process is a list of information that includes the following items:

- Local and global variables
- A current scheduling context
- Allocated system resources, such as file descriptors and network ports.

#### All processes are descendants of the first system process, systemd* on a Red Hat system.

## Forks

Through the *fork* routine, a child process inherits security identities, previous and current file descriptors, port and resource privileges, environment variables, and program code.

- Child process can exec its own code
- Parent process sleeps and awaits completion of child process
- Upon completion child process leaves a *zombie* resource in process table.
- Parent process wakes, cleans the process table, and frees the last resource of the child process
- Parent process continues with its own code.

![[Pasted image 20240201204551.png]]
## Process States

| **Name** | **Flag** | **Kernel-defined state name and description** |
| :--: | ---- | ---- |
| Running | *R* | **TASK_RUNNING**: The process is either executing on a CPU or waiting to run. The process can be executing user routines or kernel routines (system calls), or be queued and ready when in the *Running* (or *Runnable*) state. |
| Sleeping | *S* | **TASK_INTERRUPTIBLE**: The process is waiting for some condition: a hardware request, system resource access. or a signal. When an event or signal satisfies the condition, the process returns to *Running*. |
|  | *D* | **TASK_UNINTERRUPTIBLE**: This process is also sleeping, but unlike *S* state, does not respond to signals. It is used only when process interruption might cause an unpredictable device state. |
|  | *K* | **TASK_KILLABLE**: Similar to *D* state, but allows a waiting task to respond to the signal to kill it. <br>*\*Utilities often display Killable processes as the 'D' state\* * |
|  | *I* | **TASK_REPORT_IDLE**: A subset of state *D*. The kernel does not count these processes when calculating the load average. It is used for kernel threads. |
| Stopped | *T* | **TASK_STOPPED**: The process is stopped or suspended by a user or another process, but can be resumed. |
|  | *T* | **TASK_TRACED**: A process that is being debugged is also temporarily stopped and shares the *T* state |
| Zombie | *Z* | **EXIT_ZOMBIE**: A child process signals to its parent as it exits. All resources except for the process identity (PID) are released. |
|  | *X* | **EXIT_DEAD**: When the parent cleans up the remaining child process structure, the process is now released completely. This state cannot be observed in process-listing utilities. |




---
# References
