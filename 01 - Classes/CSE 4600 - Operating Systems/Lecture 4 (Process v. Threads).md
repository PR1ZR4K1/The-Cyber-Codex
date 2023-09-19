2023/09/13 11:00
Status: #idea
Tags:

# Lecture 4

Processes vs. Threads

Instead of PCBs, TCBs are created which are smaller and less computationally expensive
## Why Threads?

Here are some capabilities of threads.

- Web server - can receive multiple requests or perform multiple operations at the same time.

- Web client – Load images "img src=... in a web page concurrently"

- Microsoft Word – The user types the words while MS words performs spell check

## Thread Overview

- Active entity
- Executing unit of a process
- Simultaneous execution
- Many threads executing concurrently
- No need to allocate separate address spaces for each thread
- Hotter cache if some threads are repeatedly execute a small portionof the code

## Thread Benefits

- Responsiveness - may allow continued execution if part of process is blocked, especially important for user interfaces

- Resource Sharing - threads share resources of process, easier than shared memory or message passing

- Economy - cheaper than process creation, thread switching lower overhead than context switching

- Scalability - process can take advantage of multi-core architectures

## Process vs. Threads

### Process 

Processes will run instructions sequentially
Single core processor

### Threads

Threads can run tasks concurrently
Multi-core processor
Threads will use the same address space
Threads can receive any type of data as a parameter:

```C++
void* function_name(void* arg)
```

## Multi-core Programming


### Challenges

- Dividing activities
- Balance
- Data splitting
- Data dependency
- Testing and debugging
- Race Conditions

### Parallelism vs. Concurrency

![[concurrency v parallelism.png]]

#### Parallelism

Implies a system can perform more than one task simultaneously

*Types of Parallelism*

- <mark style="background: #FFF3A3A6;">Data parallelism</mark> - distributes subsets of the same data across multiple cores, same operation on each

![[data-parallelism.png]]

- <mark style="background: #FFF3A3A6;">Task parallelism</mark> - distributing threads across cores, each thread performing unique operation.

#### Concurrency

Supports more than one task making progress

## Multi-threading Models

### Many-to-One

- Many user-level threads mapped to single kernel thread

- One thread blocking causes all to block

- Multiple threads may not run in parallel on multi-core system because only one may be in kernel at a time

*Examples:*

	- Solaris Green Threads
	- GNU Portable Threads

![[many-one model.png]]

### One-to-One

- Each user-level thread maps to kernel thread

- Creating a user-level thread creates a kernel thread

- More concurrency than many-to-one

- Number of threads per process sometimes restricted due to overhead

*Examples:*

	- Windows
	- Linux

![[one-one model.png]]

### Many-to-Many

- Allows many user level threads to be mapped to many kernel threads

- Allows the operating system to create a sufficient number of kernel threads

*Examples:*

	- Windows with the ThreadFiber package

	- Otherwise not very common

![[many-many model.png]]

### Two-level Model

- Similar to many-many, except that it allows a user thread to be bound to kernel thread.

![[two-level model.png]]

## Thread Libraries

Provides programmer with API 


---
# See Also

- **[[Race Conditions]]**
- **[[]]**
