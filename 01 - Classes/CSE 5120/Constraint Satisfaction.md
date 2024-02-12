2024/02/12 13:05
Status: #idea
Tags:

# Constraint Satisfaction

### Standard vs. Constraint Satisfaction Problems

- Standard search problem:
	- state is a "black box": arbitrary data structure
	- Any old data structure that can support goal test, eval and successor function
- Constraint Satisfaction Problems (CSPs)
	- A special subset of search problems
	- State is defined by variables, $X_i$, with values from a domain <mark style="background: #FF5582A6;">D</mark> (sometimes <mark style="background: #FF5582A6;">D</mark> depends on <mark style="background: #FF5582A6;">I</mark>)
	- Goal test is a set of constraints specifying allowable combinations of values for subsets of variables.
	- Types of Solutions

		- One Solution
		- Multiple Solutions
		- No Solution

- Simple example of a formal representation language
- Allows useful general purpose algorithms with more power than standard search algorithms.

## Constraint Graph

*Binary CSP* - each constraint relates at more two variables
*Constraint graph* - nodes are variables, arcs show constraints
*General-purpose CSP algorithms* - use the graph structure to speed up search ex: Tasmania is an independent subproblem 

## Cryptarithmetic


$$\begin{align*}
  &\phantom{+}S\ E\ N\ D\\
+ &\phantom{+}M\ O\ R\ E\\\\

  &M\ O\ N\ E\ Y
\end{align*}
$$

In this puzzle, each letter represents a unique number from 0 to 9. The goal is to figure out which letter corresponds to which number, such that the sum is correct when the letters are replaced with their corresponding numbers.

The solution must also satisfy certain constraints:

1. The same letter must represent the same digit wherever it appears.
2. Different letters must represent different digits.
3. The leading digit of a multi-digit number must not be zero.

To solve a cryptarithmetic puzzle, you would generally start with the column on the far right (the "ones" place) and work your way to the left, carrying over when necessary, just like in normal addition. You also need to keep track of which letters correspond to which numbers, often through a process of trial and error, while ensuring that you do not violate any of the constraints mentioned above.


here is the solution:
$$
\begin{align*}
  &\phantom{+}9\ 5\ 6\ 7\\
+ &\phantom{+}1\ 0\ 8\ 5\\\\
  &1\ 0\ 6\ 5\ 2
\end{align*}
$$

### Forward Checking

Keep track of domains for unassigned variables and cross off bad options (values that violate a constraint when added to the existing assignment)

### Constrain Propagation

- Forward checking propagates information from assigned to unassigned variables, but doesn't provide early detection for all failures:

## Single Arc Consistency

- An arc X -> Y is *consistent* iff (if and only if) for *every* x in the tail there is some y in the head which could be assigned without violating a constraint

![[Pasted image 20240212140335.png]]

For the left most arc:

NT is the tail
WA is the head

Check every variable in the tail and check if we can use it without violating a constraint. In this case the only value that violates a constraint is red for NT. Because of this we ALWAYS remove from the tail so we will get rid of variable red from NT.

### Minimum Remaining Values:

Choose the variable with the fewest legal values left in its domain

### Least Constraining Value

Given a variable, choose the least constraining value:

- Choose the one that rules out the fewest values in the remaining variables

![[Pasted image 20240212141404.png]]

## Tree-Structured CSPs

- Algorithm for tree-structured CSPs:
	- Order: Choose a root variable, order variables so that parents precede children
	- Remove Backward: For i = n : 2, apply RemoveInconsistent(Parant($X_i$), $X_i$)
	- Assign forward: For i = 1 : n, assign $X_i$ consistently with Parent($X_i$)
- Runtime: O($n*d^2$)

---
# References
