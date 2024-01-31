2023/12/04 11:02
Status: #idea
Tags:

# Final Review

### Interrupt:

let devices know something something

### Scheduler:
what are the goals of scheduling?

<mark style="background: #FFF3A3A6;">a.) responsiveness, utilization, turnaround time</mark>
b.) security, mechanisms

### CPU Utilization

Suppose you have this figure.
Two Tp processing time, two Tsched scheduling times
Assume that Tp and Tsched are both 2ms
Here is the formula for CPU Utilization
what is the CPU Utilization in % (80, 90, or 100)

CPU Utilization = 

$${\frac{2Tp}{2Tp+2Sched}}$$
Fill in values
$${\frac{2 * 2ms}{2*2ms + 2 * 2ms}}$$

= ${4/8}$ = 50% CPU utilization


### Fill in Blanks

_______ is when a process holding at least one resource is waiting to acquire additional resources held by other processes.

- Circular wait
- <mark style="background: #FFF3A3A6;">Hold and wait</mark>
- Mutual exclusion
- Semaphore

__ is converted to request edge when a process requests a resource

- <mark style="background: #FFF3A3A6;">Claim Edge</mark>
- Assignment Edge
- Allocate Edge

__ can lead to process starvation

- Round Robin
- <mark style="background: #FFF3A3A6;">Priority Scheduling</mark>
- First come first serve
- None of the above

In Round Robin algorithm, a time quantum q is associated with each process from a set of n processes, and the process after its time quantum, moves to the tail of the queue. This way, a process only wait at most __ units of time.

- q+(n-1)
- q(q-1)/2
- <mark style="background: #FFF3A3A6;">q(n-1)</mark>
- N(n-1)/2

__ module gives control of the CPU to the process selected by the short-term scheuduler.

- <mark style="background: #FFF3A3A6;">Dispatcher</mark>
- CPU Scheduler
- Kernel
- None of the above

### Dispatch Latency/Delay

The time is takes to switch the context from one process to another

### CPU Scheduling decisions may take place when a process:

- Switches from running to waiting state - Non-Preemptive Scheduling
- <mark style="background: #FFF3A3A6;">Switches from running to ready state - Preemptive Scheduling</mark>
- <mark style="background: #FFF3A3A6;">Switches from waiting to ready - Preemptive Scheduling</mark>
- Terminates - Non-Preemptive Scheduling

### Scheduling Criteria

CPU Utilization - keep the CPU as busy as possible
Throughput - # of process

### ___ can suffer from performance degradation due to unbalanced scheduling load.



---
# References
