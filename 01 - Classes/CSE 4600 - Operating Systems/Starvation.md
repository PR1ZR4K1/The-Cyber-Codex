2023/09/20 11:42
Status: #idea
Tags: [[Lecture 5 (Thread Synchronization)]]

# Starvation

Starvation refers to a situation where one or more threads are prevented from making progress because resources are continuously being allocated to other threads

Starvation is often a result of unfair or suboptimal scheduling and resource allocation. While starvation doesn't lead to program termination or deadlock, it is undesirable because it degrades performance and could lead to unresponsiveness.

## Causes of Starvation:

1. **Priority Inversion**: When low-priority threads hold resources needed by a high-priority thread, the latter might starve if the scheduler favors other threads.
    
2. **Unfair Scheduling**: Some scheduling algorithms may favor some threads over others, leading to starvation.
    
3. **Resource Hoarding**: If some threads hold onto resources for a long time without releasing them, other threads needing those resources may starve.
    
4. **Improper Use of Locks**: If locks are not used judiciously, they can become bottlenecks, causing some threads to starve.

### Example:

Consider the following C++ code snippet, which uses the `<thread>` and `<mutex>` headers to create a simple example. Suppose there are two threads, `thread1` and `thread2`, and `thread1` has a much higher chance of acquiring the lock compared to `thread2`.

```
#include <iostream>
#include <thread>
#include <mutex>
#include <chrono>

std::mutex myMutex;

void threadFunctionHighPriority()
{
    while (true)
    {
        std::lock_guard<std::mutex> lock(myMutex);
        std::cout << "High-priority thread executing..." << std::endl;
        std::this_thread::sleep_for(std::chrono::milliseconds(10));
    }
}

void threadFunctionLowPriority()
{
    while (true)
    {
        if (myMutex.try_lock())
        {
            std::cout << "Low-priority thread executing..." << std::endl;
            myMutex.unlock();
            std::this_thread::sleep_for(std::chrono::milliseconds(100));
        }
    }
}

int main()
{
    std::thread thread1(threadFunctionHighPriority);
    std::thread thread2(threadFunctionLowPriority);
    thread1.join();
    thread2.join();
    return 0;
}

```

In this example, `threadFunctionHighPriority()` has a much higher chance of acquiring `myMutex` because it attempts to lock the mutex at much shorter intervals. As a result, `threadFunctionLowPriority()` may rarely get a chance to acquire the mutex, leading to starvation of the low-priority thread.

### Prevention/Solutions

1. **Fair Scheduling**: Use algorithms that ensure all threads get a fair chance to execute.
    
2. **Time Quanta**: Allocate fixed time slots to each thread so that it does not monopolize the CPU or resources.
    
3. **Resource Preemption**: Preempt resources from threads that have been using them for too long.
    
4. **Priority Inheritance**: Temporarily elevate the priority of low-priority threads that are holding resources needed by high-priority threads.

---
# References
