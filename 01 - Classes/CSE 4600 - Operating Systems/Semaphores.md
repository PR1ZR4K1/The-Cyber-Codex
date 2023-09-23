2023/09/20 10:51
Status: #idea
Tags: [[Lecture 5 (Thread Synchronization)]]

# Semaphores

A semaphore is a synchronization primitive used to control access to a shared resource by multiple threads in a concurrent system such as a multitasking operating system. 

A useful way to think about a semaphore is as a set of permits; a thread must acquire a permit from the semaphore before it can access the shared resource, and it must release the permit back to the semaphore once it's done. If no permits are available, a thread will block until one becomes available or until it's interrupted.

## Named vs Unnamed

### Named 

1. **Scope**: Named semaphores have system-wide scope, meaning they can be used for synchronization between unrelated processes, not just threads within the same process.
    
2. **Persistence**: Once created, a named semaphore continues to exist until explicitly removed or the system is rebooted, even if the process that created it terminates.
    
3. **Naming**: A named semaphore is identified by a unique name, usually a string, which allows it to be accessed by different processes.
    
4. **Portability**: Named semaphores are often less portable because they rely on system-level features, which may differ between operating systems.
    
5. **API**: The API functions for named semaphores often include calls for creating, opening, closing, and unlinking the semaphore.
    
6. **Usage Scenario**: Named semaphores are more suitable when you need synchronization between different, unrelated processes.
    
7. **Overhead**: Generally, named semaphores have a bit more overhead due to the system-wide scope and persistence.

*Creating named semaphore*
```
#include <semaphore.h>
sem_t *sem;

/*Create Semaphore and initialize it to 1*/
sem = sem_open("SEM", O_CREAT, 0666, 1);

```

### Unnamed

1. **Scope**: Unnamed semaphores are usually limited to threads within the same process, although some systems allow them to be shared between processes that have a parent-child relationship.
    
2. **Persistence**: They are automatically destroyed when the last reference to them is gone (usually when the process terminates).
    
3. **Naming**: These semaphores do not have a name and therefore can't be accessed by unrelated processes.
    
4. **Portability**: Unnamed semaphores are generally more portable as they operate within the context of a single process, making them less dependent on system-specific features.
    
5. **API**: The API is often simpler because there's no need to manage names, and the semaphore lifecycle is typically tied to the lifecycle of the process or parent object.
    
6. **Usage Scenario**: Unnamed semaphores are suitable for thread-level synchronization within the same process.
    
7. **Overhead**: Generally, unnamed semaphores have lower overhead compared to named semaphores.

*Creating unnamed semaphore*
```
#include <semaphore.h>

sem_t sem;
sem_init(&sem, 0, 1);

```

## Problems with Semaphores

### Incorrect use of semaphore operations: 

```
 signal(mutex) .... wait(mutex)  
 wait(mutex) ... wait(mutex)  
``` 

- Omitting of wait (mutex) and/or signal (mutex)  
## Summary

Named semaphores would be used for inter-process synchronization and unnamed semaphores for intra-process (thread-level) synchronization

---
# See Also

- [[Lecture 5 (Thread Synchronization)]]
- [[Lecture 4 (Process v. Threads)]]

