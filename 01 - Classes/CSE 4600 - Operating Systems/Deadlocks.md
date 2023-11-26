2023/09/25 10:48
Status: #idea
Tags:

# Deadlocks in Multi-Threaded Applications

## Deadlock Characterization

__Mutual Exclusion__ - only one process at a time can use a resource

__Hold and Wait__ - A process holding at least one resource is waiting to acquire additional resources held by other processes.

__No Preemption__ - A resource can be released only voluntarily by the process holding it, after that process has completed its task.

__Circular Wait__ - There exists a set {$P_0$, $P_1$,..., $P_n$} of waiting processes such that $P_0$ is waiting for a resource that is held by $P_1$, $P_1$ is waiting for a resource that is held by $P_2$, ... $P_{n-1}$ is waiting for a resource that is held by $P_{n^1}$ and $P_n$ is waiting for a resource that is held by $P_0$.

### Learning Objectives

- *Illustrate how deadlock can occur when `mutex` locks  
are used 

- *Define the four necessary conditions that characterize  
deadlock  

- *Identify a deadlock situation in a resource allocation  
graph  

- *Apply resource allocation graph and banker’s algorithm  
for deadlock avoidance

## System Model

There are many different resource types *($R_i$):
 - CPU cycles
 - Memory space
 - I/O devices
 - etc.

Each resource type $R_i$ has $W_i$ instances

Each process utilizes a resource as follows:
- request resource (lock resource)
- use resource 
- release resource (unlock resource)

## Handling Deadlocks

### Deadlock - Semaphores

Data:
 - Semaphore ($S_1$)
 - Semaphore ($S_2$)

Two Processes:
			![[semaphore-ex.png]]****
 - Process ($P_1$)
	 - $wait(S_1)$
	 - $wait(S_2)$

 - Process ($P_2$)
	 - $wait(S_1)$
	 - $wait(S_2)$

### Methods to Handle Deadlocks

Ensure that the system will __never__ enter a deadlock state:
 - Deadlock Prevention
 - Deadlock Avoidance

Allow the system to enter a deadlock state and then recover.

Ignore the problem and pretend that deadlocks never occur in system (lol)

## Resource Allocation Graphs

![[Resource Graph Deadlock Cycle.canvas|Resource Graph Deadlock Cycle]]

## Avoidance Algorithms

### Single instance of a resource type

	Use a resource-allocation graph

### Multiple instances of a resource type

	Use the Banker's Algorithm


## Banker's Algorithm

- Multiple instances of resources 

- Each process must a priori claim maximum use  

- When a process requests a resource it may have to wait  

- When a process gets all its resources it must return them in a finite  amount of time

Let n = number of processes, and m = number of resources types.

Available: Vector of length m. If available [j] = k, there are k instances of resource type  
Rj available  
Max: n x m matrix. If Max [i,j] = k, then process Pi may request at most k instances of  
resource type Rj  
Allocation: n x m matrix. If Allocation[i,j] = k then Pi is currently allocated k instances  
of Rj  
Need: n x m matrix. If Need[i,j] = k, then Pi may need k more instances of Rj to  
complete its task  
• Need [i,j] = Max[i,j] – Allocation [i,j]  
Let n = number of processes, and m = number of resources types.

### Example of Banker's Algorithm

5 Processes $P_0$ - $P_4$
	3 Resource Types:
		A (10 instances), B (7 instances), C (7 instances)

Snapshot at time $T_0$

![[Pasted image 20230925114308.png]]

The content of the matrix __Need__ is defined to be __Max - Allocation__

![[Pasted image 20230925114342.png]]

The system is in a safe state since the sequence 
< $P_1$, $P_3$, $P_4$, $P_2$, $P_0$, >

---
# See Also

- [[Mutex Lock]]
- [[Semaphores]]
- [[Resource Graph Scheme]]

