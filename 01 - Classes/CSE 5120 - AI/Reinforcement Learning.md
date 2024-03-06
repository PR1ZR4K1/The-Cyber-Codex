2024/02/26 13:09
Status: #idea
Tags: [[Markov Decision Processes]]

# Reinforcement Learning

*Simplest Example of Reinforcement Learning*

![[Pasted image 20240226131535.png]]

- Receive feedback (i.e., rewards)
- Agent's utility $->$ reward function
- Must (learn to) act so as to maximize expected rewards
- Learning is based on observed samples of outcomes!

## Basics

### MDP vs. Reinforcement Learning

Assume MDP is:

- A set of states s $\in$ S
- A set of actions (per state) A
- A model T(s,a,s') | Transition Matrix
- A reward function R(s, a, s')

Reinforcement:

T and R are unknown

- No knowledge of good states and what the actions do
- Try out actions and states to learn

## Building on the concept of Markov Decision Processes (MDP)

## Model Based Learning

- Learn an approximate model based on experiences
- Solve for values as if the learned model were correct

#### Step 1: Learn Empirical MDP model

- Count outcomes s' for each s, a
- Normalize to give an estimate of $\hat{T}$(s,a, s')
- Discover each $\hat{R}$(s, a, s') when we experience (s, a, s')
#### Step 2: Solve the Learned MDP
- Use value iteration

### Example: Expected Age

![[Pasted image 20240226134507.png]]

## Model-Free Learning

### Passive Reinforcement Learning

Simplified Task: Policy Evaluation

- input: a fixed policy $\pi(s)$
- You don't know the transitions $T(s,a,s')$
- You don't know the rewards $R(s,a,s')$
- Goal: learn the state values

In this case:

- Learner is "along for the ride"
- No choice about what actions to take
- Just execute the policy and learn from experience 
- This is NOT offline planning! You actually take actions in the world

#### Direct Evaluation

Goal: compute values for each state under $\pi$
Idea: Average together observed sample values

- Act according to $\pi$
- Every time you visit a state write down what the sum of discounted rewards turned out to be 
- Average those samples

![[Pasted image 20240226135223.png]]

**Pros**: 

- easy to understand
- Does not require any knowledge of T, R
- Eventually computes the correct average values, using just sample transitions

**Cons**:

- Wastes information about state connections
- Each state must be learned separately
- Takes a long time to learn

## Q-Learning, Temporal Difference Learning and SARSA


### Temporal Difference Learning

*Big Idea*: Learning from every experience!

- Update V(s) each time we experience a transition (s, a, s', r)
- Likely outcomes s' will contribute updates more often

Temporal Difference larning of values

- Policy still fixed, still doing evalutaion!
- Move values toward value of whatever successor occurs: running average

$$Sample\ of\ V(s): sample=R(s,\pi(s),s') + \gamma{V}^\pi(s')$$
$$Update\ to\ V(s): V^{\pi(s)}<- (1-\alpha)V^{\pi(s)} +(\alpha)sample$$
$$Same\ Update: V^{\pi(s)} <- V^\pi(s)+\alpha(sample-V^\pi(s))$$

## Active Reinforcement Learning

- Full reinforcement learning: optimal policies (like value iteration)
	- Don't know the transitions $T(s, a, s')$
	- Don't know the rewards $R(s, a, s')$
	- Choose the actions now
	- Goal: learn the optimal policy / values
- In this case:
	- Learner makes choices!
	- Fundamental tradeoff: exploration vs. exploitation




---
# References
