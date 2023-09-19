2023/09/11 10:39
Status: #idea
Tags:

# Lecture 3


## Learning Objectives

- Identify the separate components of a process and illustrate how they are represented and scheduled in an operating system.
- Describe what process address space is and how processes are scheduled in the memory
- Design programs that uses pipes and POSIX shared memory to  perform inter-process communication
- Describe how processes are created and terminated in an operating system, including developing programs using the appropriate   system calls that perform these operations.unication.

## Process Lifecycle - Process States

![[Process Lifecycle.png]]

## Process Termination

- When a process is complete it asks the OS to kill it using the <mark style="background: #FFF3A3A6;">exit()</mark> system call.
- Parent process may terminate the execution of child processes by using <mark style="background: #FFF3A3A6;">abort()</mark> system call

## Multi-process Architecture - Chrome Browser

Chrome runs with 3 different types of processes:

- <mark style="background: #ABF7F7A6;">Browser</mark> process manages user interface, disk, and network I/O
- <mark style="background: #ABF7F7A6;">Renderer</mark> process renders web pages, deals with HTML, Javascript.
	- A new renderer is created for each website opened
	- runs in sandbox restricting disk and network I/O, minimizing effect of security exploits.
 - <mark style="background: #ABF7F7A6;">Plug-in</mark> process for each type of plug-in.

## CPU Scheduler

Determines which one of the currently ready processes will be dispatched to the CPU to start running.

### Queues and Goal

- Goal -- Maximize CPU use, quickly switch processes onto CPU core.
- Ready Queue - set of all processes residing in main memory, ready and waiting to execute
- Wait Queue - set of processes waiting for an event (I/O)
- Processes will migrate between the various queues repeatedly.

![[CPU Scheduler?.png]]

### How long should the process run?

Depends on a few factors:

- Time Slice - $T_p$
- Scheduling Time - $T_{sched}$

$$CPU \ Utilization = \frac{total \ processing \ time} {total \ time}$$
or
$$ \frac{2 *T_p}{2*T_p+2*T_{sched}}$$

1. $T_{sched}$ = $T_p$  | 50% CPU utilization
2. $T_{sched}$ >> $T_p$ | ~90% CPU utilization

- Timeslice: Amount of time given to a process to run
- Scheduling time: Amount of time given between

### Non-Preemptive Scheduling

- In a non-preemptive scheduling system, once a process has grabbed the CPU, it keeps it until it has completed its task or relinquishes it voluntarily. 
- That is, no other process can "cut in line" and take over the CPU until the currently executing process is done.

![[NonPreemptive Scheduling.png]]
### Preemptive Scheduling

- Allows the operating system to forcibly remove the currently running process from the CPU to give another, often higher-priority, process a chance to execute.

![[Preemptive Scheduling.png]]

### Inter-Process Communication (IPC)

Allows two processes to communicate with one another.

Cooperating process can affect or be affected by other processes, including sharing data.

#### Two methods of Communication

- Messaging Channel:
	- Operating creates messaging channel for processes to read and write to.
	- Lets both parties know that the secure channel has been created

![[IPC Messaging Channel.png]]

- Shared Memory Channel
	- OS establishes the memory channel and maps it into the address of the processes.
	- OS is out of the way of process communication
	- OS no longer support APIs for communication.

![[Pasted image 20230911114121.png]]



---
# References
