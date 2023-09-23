2023/09/20 10:52
Status: #idea
Tags: [[Lecture 5 (Thread Synchronization)]]

# Condition Variable

Since POSIX is typically used in C/C++ and these languages do not provide a monitor, POSIX  
condition variables are associated with a POSIX mutex lock to provide mutual exclusion:  

*Creating and initializing the condition variable:*

```
pthread_mutex_t mutex;
pthread_cond_t cond_var;

pthread_mutex_init(&mutex, NULL);
pthread_cond_init(&cond_var, NULL);
```





---
# References
