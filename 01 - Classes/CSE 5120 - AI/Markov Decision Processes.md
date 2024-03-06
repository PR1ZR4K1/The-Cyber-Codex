2024/02/14 13:06
Status: #idea
Tags: [[Constraint Satisfaction]]

# Non-Deterministic Search

*Algorithm that uses randomness or probabilistic decisions to explore solutions, allowing for different outcomes on each run even with the same initial conditions.*

## Grid World Example

![[Pasted image 20240214131731.png]]

# Markov Processes 

## Markov Decision Processes (MDP)

*Formally describe an environment for reinforcement learning*

- The environment if fully observable 
- The current state completely characterizes the processs
- Almost all reinforcement learning problems can be formalized as MDPs
	- Optimal controls -> deals with continuous MDPs
	- Partially observeable problems can be converted to MDPs
	- *Bandits* are MDPs with one state

### MDP Definition

- A set of world states  ${s \in S}$
- a set of feasible actions ${a \in A}$
- A transition matrix $T(s, a, s')$
	- Probability that a from s leads to $s'$ 
		- $P(s'| s, a)$
	- Also called the model or the dynamics
- A reward function $R(s, a ,s')$
	- Sometimes just $R(s)$ or $R(s')$
	- Simply the weighted average found by expectimax
- A start state
- Discounting factor:
	$$G_t = R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \dots = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}
$$
- Terminal (goal state)

**MDPs are non-deterministic search problems**

*One way to solve them is with expectimax search*

## Markov Property 

The future is independent of the past given the present
Only current state and action matters for taking a decision

![[Pasted image 20240214133020.png]]

## Example - Class Dynamics

![[Pasted image 20240214133603.png]]

Each link has a probability associated with it. You can use expectimax to make use of these values

### Transition matrix for example:

![[Pasted image 20240214133624.png]]

### Rewards

Reward function is the final piece for the *MDP*. The value is in red in the original image.

## Example: Racing

![[Pasted image 20240214134942.png]]

### Expectimax Tree

![[Pasted image 20240214135200.png]]

### MDP Search Tree

![[Pasted image 20240214135341.png]]

state: $s$
action: $a$
q-state: $Q(s,a)$ before the action gets taken
$s'$ is the state that actually happens after the transition

## Markov Reward Processes (MRP)

*Is a Markov chain with values*

An MRP is a tuple (S,P):

- A set of world states $s \in S$
- A set of feasible actions $a \in A$
- A transition matrix $T(s, a, s')$
	- Probability that a from s leads to $s'$ 
		- $P(s'| s, a)$
	- Also called the model or the dynamics
- A reward function $R(s, a ,s')$
	- Sometimes just $R(s)$ or $R(s')$
	- Simply the weighted average found by expectimax
- A start state
- Discounting factor: $\gamma \in S$
- Total reward (Return):
	$$G_t = R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \dots = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}
$$
- Terminal (goal state)

### Calculate different states

![[Pasted image 20240214140536.png]]

Definitions:

- Value $$V^*(s) = \max_a Q^*(s, a)
$$
- Q-State $$Q^*(s, a) = \sum_{s'} T(s, a, s') [R(s, a, s') + \gamma V^*(s')]
$$
- The alternative form of the value function using the transition probability and reward function $$V^*(s) = \max_a \sum_{s'} T(s, a, s') [R(s, a, s') + \gamma V^*(s')]
$$
- In English, basically we have a tuple: $(s, a, R(), T, \gamma)$
- (state, action, reward function, Transition matrix, and gamma)

# Optimal Policies

An optimal plan or sequence of actions, from start to a goal

**For MDPs we want an optimal policy: $\pi^{*}:S \rightarrow A$**

- A policy ($\pi$) gives an action for each state
- An optimal policy is one that maximizes expected utility if followed
- An explicit policy defines a reflex agent
- When a policy is applied you no longer have to calculate the max over a set of actions to get s so the time complexity is O($s^2$) instead of O($s^2$a)

# Expected Utility 

## Fixed Policy

$$V^{\pi}(s) = \sum_{s'} T(s, \pi(s), s') \left[ R(s, \pi(s), s') + \gamma V^{\pi}(s') \right]
$$
argmax gets the associated action from the highest value in an array

### Policy Extraction

Uses the same equation that would get you the all of the action values for a particular state and then you would grab the index of the highest value out of the actions which is basically the direction in our example

## Bellman Equation

# Value Iteration






---
# References
