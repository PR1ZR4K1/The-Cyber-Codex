2023/09/20 10:42
Status: #idea
Tags: [[Lecture 5 (Thread Synchronization)]]

# Mutex Lock

Mutual Exclusion Locks

## Creating and Using Mutex Locks in C++

*Creating the Lock*

```
#include <pthread.h>

pthread_mutex_t mutex;

pthread_mutex_init(&mutex, NULL);
```

*Using the Lock*

```
/*acquire lock*/
pthread_mutex_lock(&mutex);

/*Do something here*/

/*release lock*/
pthread_mutex_unlock(&mutex);
```





---
# References
