2024/01/31 13:08
Status: #idea
Tags:

# Uniform Cost Issues (UCS)

- UCS explores increasing cost contours
- UCS is complete, has a low time complexity, but has more space usage.

## Heuristic

- heuristic refers to an educated guess towards a goal state.
- Or domain-specific hints about the location of the goal
- estimate of cost from *n* to the closest goal

### Manhattan Distance 

*"taxicab distance, city block distance, or L1 norm"*

is a way of measuring distance in a grid-like path.
Named after the grid layout of the streets of Manhattan.

## Greedy Best-First Search

Expands the node that appears to be closest to the goal. Blindly trusts the heuristic, so if heuristic is flawed it will be flawed.

### Time and Space
- O(${B^m}$) in finite space

### Complete?

- No - can get stuck in loops
- complete in finite space with repeated state checking

### Optimal?

- No

## Combing UCS and Greedy

- <mark style="background: #ABF7F7A6;">Uniform-cost</mark> orders by path cost, or backward cost ${f(n) = g(n)}$
- <mark style="background: #FF5582A6;">Greedy</mark> orders by goal proximity, or forward cost ${f(n) = h(n)}$
- <mark style="background: #D2B3FFA6;">A*</mark> Search orders by the sum: ${f(n)=g(n)+h(n)}$

So <mark style="background: #D2B3FFA6;">A*</mark> is the combination of Uniform-cost and Greedy Search

**Only stop when you dequeue a goal** 

So end the program when you do something like fringe.pop() not fringe.push()

## Is A* Optimal?

![[Pasted image 20240131134545.png]]

Must make the heuristic value optimistic meaning the heuristic should be less than or equal to the actual cost

In this example the true cost for s-a-g is 4, but the heuristic says that the estimated cost is 6.

## Differences between Tree and Graph Search

### Tree Search Limitations
- Does not work if there are cycles or if there are repeated states
- Without those things it will not be complete
- *Complete* as in if there is a solution it will always be able to be found.
## Consistency of Heuristics

- Main Idea: estimated heuristic costs <= actual costs
	- Admissibility: heuristic cost<= actual cost to goal 
		h(A) <= actual cost from A to G
	- Consistency: heuristic "arc" cost <= actual cost for each arc
		${h(A) - h(B) <= cost(A to B)}$

If heuristic is consistent it implies that it is admissible, but the opposite is not always true.

---
# References
