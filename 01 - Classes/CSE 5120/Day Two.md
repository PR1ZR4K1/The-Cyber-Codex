2024/01/24 13:07
Status: #idea
Tags:

# Outline

## Reflex agents (agents that plan)

![[Reflex Agent.png]]

Reflex agent literally reacts to its environment

Ex: A fly is flying near your eye. Reflex agent would close the eye without considering the consequences. Consequences could have been that the fly gets in your eye so maybe a better option is to swat the fly or kill it.

## Model Based Reflex Agents

![[model based reflex agent.png]]

are a type of intelligent agent that make decisions by not only considering the current percept (the agent's current state or input) but also using an internal model of the world.

## Planning (Problem Solving) Agents

Consider a sequence of actions that form a path to a goal state.
Distinction between optimal and complete planning:

- Complete Planning - if there are one or more solutions to a problem the agent will always find a solution

- Optimal Planning - if there are one or more solutions to a problem the agent will find the best solution which would be the lowest cost or maximum utility

- Replanning (unknown environments) - Scenario or problem needs to be recreated once you maximize the utility for a certain solution. 

## Search Problems

A search problem can be defined as follows:
- a state space (a set of possible states)
- initial and goal states
- A successor function (set of action-state pairs)
- Path cost (additive: e.g., sum of distances etc.)

<mark style="background: #FFF3A3A6;">Solution</mark>: A sequence of actions leading from the initial state to the goal state.

![[Pasted image 20240129133525.png]]

![[Pasted image 20240129133539.png]]

![[Pasted image 20240129134400.png]]
## Search Algorithms

- Tree search Algorithm
	**Basic Ideas:**
		- Fringe 
		- Simulated exploration of state space
		- Expanding states (generating successors of already explored states.)

- Breadth First Uses Queue
	Finds the shallowest possible solution.
	![[Pasted image 20240129135901.png]]

- Depth First uses Stack
	Finds the deepest possible solution
	![[Pasted image 20240129140110.png]]	

- Iterative Deepening
	Combination of Depth-First Search and Breadth-First Search.
	Implementation: DFS's space advantages with BFS's time/shallow-solution advantages

- Cost-Sensitive Search
	Shortest path in terms of number of 

- Uniform Cost Search uses priority queue
	if the cost is the same then the performance of this algorithm is the same as breadth for search
	Pros: complete and optimal!
	Cons: Explores options in every direction
	no information about the goal location
	Expand a cheapest node
	additive cost
	![[Pasted image 20240129140903.png]]


# Algorithm Summary

![[Pasted image 20240129141324.png]]

## Search Strategies

Strategies are evaluated along the following dimensions:

- completeness: does it always find a  solution if one exists?
- time complexity: number of nodes generated/expanded
- Space complexity: maximum number of nodes in memory
- optimality: does it always find a least cost solution

### Time and space complexity are measure in terms of

b: maximum branching factor of the search tree
d: depth of the least-cost solution  
m: maximum depth of the state space (may be infinity)







---
# References
