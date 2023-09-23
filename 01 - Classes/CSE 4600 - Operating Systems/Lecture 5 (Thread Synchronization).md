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

## Producer Consumer Problem

Famous real-world problem

### Professor's Example (I think)

Camera/frame grabber is constantly taking a picture of a region of interest and puts it into memory (Producer). (Consumer) takes memory contents and puts it through computer vision model to find shapes and such that are in the image.

![[producer consumer example.png]]

Frames are placed into a circular array in the memory block. Circular array is a normal array, with the difference being when you reach the end of the array the index is set to 0 instead of the next highest number.

*Constraints/Critical Section*

Array is the shared resource between producer and consumer

- Producer 
	- Grab image
	- Store in buffer if not full

- Consumer
	- Take image from buffer if not empty

![[producer consumer example2.png]]

#### Producer and Consumer Semaphore Solution 1

*Producer Function*

```
sem_init(&empty, 0, BufferSize);
sem_init(&full, 0, 0);


void* frameGrabber(void *pno){  
	int item;  
	while(1) {  
		item = rand(); // Random frame data  
		sem_wait(&empty); // If there is any empty slot  
		
		/*Critical Section*/
		
		pthread_mutex_lock(&mutex);  
		buffer[in] = item;  
		// Insert new frame (item) by grabber at position “in”  
		in = (in+1)%BufferSize;  
		BufferAvailable=BufferAvailable-1;  
		
		/*Critical Section*/
	
		pthread_mutex_unlock(&mutex);  
		sem_post(&full);  
	}  
}
```

*Consumer Function*

```
void* imageProcessor(void *cno){  
	while(1) {  
		sem_wait(&full);  
		pthread_mutex_lock(&mutex);  
		
		/*Critical Section*/
		
		int item = buffer[out];  
		// Remove frame (item) from “out”  
		out = (out+1)%BufferSize;  
		BufferAvailable=BufferAvailable+1;

		/*Critical Section*/
	
		pthread_mutex_unlock(&mutex);  
		sem_post(&empty);
	}
}	
```

*Limitations*

Only allows for one producer and one consumer to exist at one time because of the wait/post necessity

#### Producer and Consumer Semaphore Solution 2 Condition Variable

*Producer Function*

```
void* frameGrabber(void *pno){  
int item;  
	while(1) {  
		item = rand(); // Random frame data  
		pthread_mutex_lock(&mutex);  
		while(BufferAvailable == 0 )  
			pthread_cond_wait(&not_full, &mutex);  
		pthread_mutex_unlock(&mutex);  
		buffer[in] = item;  
		// Print Frame grabber (pno): inserted new frame (item) at “in” 
		
		in = (in+1)%MaxItems;  
		pthread_mutex_lock(&mutex);  
		BufferAvailable = BufferAvailable - 1;  
		pthread_cond_signal(&not_empty);  
		pthread_mutex_unlock(&mutex);
	}
}
```

*Consumer Function*

```
void* imageProcessor(void *cno){  
	while(1) {  
		pthread_mutex_lock(&mutex);  
		while( BufferAvailable == MaxItems )  
			pthread_cond_wait(& not_empty, &mutex);  
		pthread_mutex_unlock(&mutex);  
		int item = buffer[out];  
		//Image processor removed frame (item) from “out”  
		out = (out+1)%MaxItems;  
		pthread_mutex_lock(&mutex);  
		BufferAvailable = BufferAvailable+1;  
		pthread_cond_signal(& not_full);  
		pthread_mutex_unlock(&mutex);
	}
}
```

## Reader Writer Problem

A data set is shared among several concurrent processes.

  
*Readers* – only read the data set; they do not perform any updates  

*Writers* – can both read and write

*Problem* - allow multiple readers to read at the same time, but only one writer can access the data at the same time.

*Resource counter* - variable used to find out whether or not the resource is occupied (by either the reader or writer) 
### Conditions
 
If resource counter > 0 (reading), then it is still OK to allow read operation  

If resource counter = 0 (free), allow read or write operation 

If resource counter = -1 (writing), no other read or write operation allowed

### Reader and Writer Functions

*Writer Function*

```
void *writer(void *writer_num)  
{  
	while(1){  
	
	/*If any reader/writer occupying resource*/
	
		pthread_mutex_lock(&mutex);  
		while(resource_counter != 0)  
			pthread_cond_wait(&write_phase, &mutex);  
		resource_counter = -1;  
		pthread_mutex_unlock(&mutex); 

	/*If any reader/writer occupying resource*/
   
		shared_resource = shared_resource + 5;  
		//printf("Writer %d is modifying shared resource to %d\n",  
		(*((int *)writer_num)),shared_resource);
		  
	/*Let all readers and next writer know*/
		
		pthread_mutex_lock(&mutex);  
		resource_counter = 0;  
		pthread_cond_broadcast(&read_phase);  
		pthread_cond_signal(&write_phase);  
		pthread_mutex_unlock(&mutex);

	 /*Let all readers and next writer know*/
	
	}
}
```

*Reader Function*

```
void *reader(void *reader_num)  
{  
	while(1){  
	
	/*If a writer is occupying resource*/
	
		pthread_mutex_lock(&mutex);  
		while(resource_counter == -1)  
			pthread_cond_wait(&read_phase, &mutex);  
		resource_counter++;  
		pthread_mutex_unlock(&mutex);  
	
	/*If a writer is occupying resource*/
	
		printf("Reader %d: reading shared resource as %d\n",*((int  
		*)reader_num),shared_resource);  
		
	/*If no reader, let the waiting writer know*/

		pthread_mutex_lock(&mutex);  
		resource_counter--;  
		if(resource_counter == 0)  
			pthread_cond_signal(&write_phase);  
		pthread_mutex_unlock(&mutex);
	
	/*If no reader, let the waiting writer know*/
		
	}
}
```

## Multi-threaded Application

OS designers build software tools to solve critical section  
problem  

- Simplest is `mutex` lock  
- Boolean variable indicating if lock is available or not  
- Protect a critical section by  
- First `acquire()` a lock  
- Then `release()` the lock  
- Calls to `acquire()` and `release()` must be atomic  
- Usually implemented via hardware atomic instructions.

---
# See Also

- [[Starvation]]
- [[Linux]]
- [[POSIX API]]
- [[Mutex Lock]]
- [[Semaphores]]
- [[Condition Variable]]