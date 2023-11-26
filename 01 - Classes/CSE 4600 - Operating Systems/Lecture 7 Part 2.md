2023/10/11 10:41
Status: #idea
Tags:

# Lecture 7 Part 2

## Circular Array:

A circular array is a linear data structure in which the end of the array is conceptually connected back to its beginning, forming a closed loop. This connection allows operations to wrap around seamlessly from the last element back to the first.

### *Use in Round Robin Programs*:

The circular array is especially useful in round-robin algorithms because of its inherent "wrap-around" feature. Here's why:

1. **Continuous Operation**: In a round-robin algorithm, tasks (or data elements) are handled in a cyclical manner. Once the algorithm reaches the end of the set, it needs to loop back to the beginning without interruption. A circular array facilitates this by providing a seamless transition from the last element to the first.
    
2. **Efficient**: Using a circular array, implementing a round-robin procedure becomes more efficient in terms of both time and space. No complex checks or operations are needed to reset to the start; the "wrap-around" is natural.
    
3. **Fixed Size**: Round-robin algorithms, particularly in scheduling or buffering contexts, often operate within a fixed number of tasks or a fixed buffer size. A circular array's size is set upon creation, making it a fitting choice.
    
4. **Constant Time Access**: Circular arrays allow constant time (O(1)) access to any element, given its index. This is beneficial when tasks or data elements need to be quickly referenced or updated.

## In Class Diagram

![[Pasted image 20231011111959.png]]


*Variable Names and Descriptions*

- TQ - Time Quantum seems to be the amount of time in ms each process will get before the context gets switched
- BT - Burst Time thought he said it was the array containing the amount of time each process should take
- WT - waiting time...
- TA - Turn around time is the actual amount of time that each process takes 
- rem-time - remaining time we use the BT to gather how much time each process needs to complete

![[Pasted image 20231011114509.png]]

In this example TQ is 4ms

$P_1$, $P_2$, $P_3$ are 3 processes and their BTs are 8, 5, 13

the bar is how time will be allocated to each of them with context switching

to calculate wt you gather the time it took for the process to complete and then subtract the BT from it for each process


---

# References
