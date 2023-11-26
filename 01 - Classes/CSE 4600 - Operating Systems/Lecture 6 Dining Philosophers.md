2023/09/27 10:47
Status: #idea
Tags:

# Lecture 6 Dining Philosophers

![[Dining Philosophers.png]]

## Constants

Philosophers are either thinking or eating. There are 5 philosophers and 5 forks. In order to eat a philosopher would need 2 forks.

## Order of Operations

- Pick up left fork 
- Pick up left fork 
- Eat 
- Put left fork down 
- Put right fork down  

## Mutual Exclusion and no Preemption

When one philosopher picks up a fork another philosopher can not pick up that fork until the initial philosopher is done eating.

## Representative Function

*Worst solution - No mutual exclusion potential for starvation*

```
Philosopher(void* phiNum)
{
	while (true) {
	
		sleep(1); // think for 1 second
		
		// take left then right fork.
		take_left_fork();
		take_right_fork();
		
		eat();
		
		// done eating. put fork down.
		put_right(*i*);
		put_left(*i*);
	}
}

```


*Still a bad solution since every philosopher will take a fork and then put it down still leading to starvation*

```
Philosopher(void* phiNum)
{
	while (true) {
	
		sleep(1); // think for 1 second
		
		// take left then right fork.
		take_left_fork();
		
		if(right_available == TRUE){
			take_right_fork();
			eat();
		
			// done eating. put fork down.
			put_right(*i*);
			put_left(*i*);
		} else {
			put_left(*i*);
			sleep(1);
		}
	}
}
```

*close to the best, but only one philosopher can eat in this solution. we want at least two to be able to eat*

```
Philosopher(void* phiNum)
{
	while (true) {
		
		pthread_mutex_lock(&mutex);
		sleep(1); // think for 1 second
		
		// take left then right fork.
		take_left_fork();
		take_right_fork();
		
		eat();
		
		// done eating. put fork down.
		put_right(*i*);
		put_left(*i*);
		pthread_mutex_unlock(&mutex);
	}
}
```



---
# References
