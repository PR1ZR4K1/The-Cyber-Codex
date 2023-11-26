2023/09/25 11:24
Status: #idea
Tags: [[Deadlocks]]

# Resource Graph Scheme

- Claim edge $P_i$ -> $R_j$ indicated that process $P_j$ may request  
resource $R_j$; represented by a dashed line  

- Claim edge converts to request edge when a process requests a 
resource  

- Request edge converted to an assignment edge when the  
resource is allocated to the process  

- When a resource is released by a process, assignment edge  
reconverts to a claim edge  

- Resources must be claimed a `priori` in the system

## Resource Allocation Graph Limitations

They are not good for Multi-Resource instances idk why lol

## Resource Graphs Examples

***Example 1: 

Is a deadlock, is cycling resources

![[Pasted image 20230925112614.png]]

***Example 2: 

Cycle exists, possible deadlock

$T_1$ is requesting $R_1$, but $R_1$ is allocated to $T_2$, $T_2$ is requesting $R_3$, but $R_3$ is allocated to $T_3$, $T_3$ is requesting $R_2$, but $R_2$ is allocated to $T_1$ and $T_2$.

![[Pasted image 20230925112646.png]]

***Example 3: 

![[Pasted image 20230925112703.png]]

***Example 4 (Resource-Allocation Graph and Wait-for Graph):

![[Pasted image 20230925112748.png]]

***Example 4 Wait-For Graph:

![[Wait-For Graph.canvas|Wait-For Graph]]

---
# References
