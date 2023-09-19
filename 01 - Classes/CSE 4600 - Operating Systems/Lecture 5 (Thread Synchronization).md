2023/09/18 11:07
Status: #idea
Tags:

# Lecture 5 (Thread Synchronization)

## Why Threads?

Instead of having to load parts of a website sequentially, you can do all of those things concurrently.

Here's an example:

![[thread-ex1.png]]

### Thread Models

- Dispatcher Model
	- ![[dispatcher-model.png]]
	Boss Thread is responsible for handling scheduling for worker threads.
	hands out jobs to other threads
	Issues:
		- partial execution
		- boss thread gets terminated, big point of failuer
		- synchronization complexity or limitations

- Pipeline Models
	- ![[pipeline-model.png]]


## Cautions with Threads

- Processes can execute concurrently
	- may be interrupted at any time, partially completing execution

- Concurrent access to shared data may result in data inconsistency
 
- Maintaining data consistency requires mechanisms, to ensure the orderly execution of cooperating processes

### Race Condition Example

Processes $P_0$ and $P_1$ are creating child processes using the 
`fork()` system call.

Race condition on kernel variable `next_available_pid` which represents the next  
available process identifier (`pid`)

![[race-condition ex1.png]]

Unless there is a mechanism to prevent $P_0$ and $P_1$ from accessing the variable `next_available_pid` the same `pid` could be assigned to two different processes!

## Multi-Threaded Application Synchronization

POSIX API provides:

- mutex locks

- semaphores

- condition variable

It is widely used on UNIX, Linux, and MacOS



---
# See Also

- [[Starvation]]
- [[Linux]]
- [[POSIX API]]