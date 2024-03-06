2024/02/28 13:11
Status: #idea
Tags:

# Value Iteration / Policy Iteration

*Drop the max function and replace it with $\pi$ or the policy*

## Q-Learning

#### Algorithm

$$Q(s,a) \leftarrow Q(s,a) + \alpha (R+\gamma \left[ \max_{a'}Q(s',a')-Q(s,a)\right])$$
**Off-Policy Learning**

We move the max function from the outside of the equation to the inside to get the best action that you can take.

*This was a substantial breakthrough in reinforcement learning*

- Here is the equation:

$$Q_{k+1}(s, a) \leftarrow \sum_{s'} T(s, a, s') \left[ R(s, a, s') + \gamma \max_{a'} Q_k(s', a') \right]
$$
- This can not be computed without knowing T, R

So, we compute the average as we go

- Receive a sample transition $(s, a, r, s')$
- This sample equation:

$$Q(s, a) \approx r + \gamma \max_{a'} Q(s', a')
$$
But we want to average over results from $(s,a)$

- Keep a running average:

$$Q(s, a) \leftarrow (1 - \alpha)Q(s, a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') \right]
$$

In words, so you start at your current q state value (s, a). Then you will compute the difference between what you predicted the next q state to be $(q^*)$ and the actual value of $(q^*)$. Next you multiply the difference that you got by $\alpha$ which is the learning rate. Finally you add this value to the current q state value. In this way by iterating through this process over and over the machine will progressively get better and better at learning the right path.

### Q-Learning Properties

- Result: q-learning converges to optimal policy -- even if you're acting suboptimally!
- This is called off-policy learning
- Caveats:
	- You have to explore a lot
	- Learning rate has to be small enough
		- but cannot be decreased too quickly
	- Basically, in the limit, it doesn't matter how you select actions (!)

### How should you explore?

**There are several methods for forcing exploration**

Simplest: random actions epsilon greedy $(\epsilon-greedy)$

- Every step, flip a coin
- With (small) probability $\epsilon$, act randomly
- With (large) probability $(1-\epsilon)$ act on current policy

Problems with random actions?

- You eventually explore the space, but keep going around until learning is done

How to make it better? Solutions:

- lower $\epsilon$ over time
	- subtract a very small number from $\epsilon$ after a certain number of explorations
- exploration functions

## Deep Q-Learning (Deep Q Networks)

*Chat-GPT Summary*

Deep Q-Learning is an advanced machine learning technique that combines Q-learning, a form of reinforcement learning (RL), with deep neural networks. In reinforcement learning, an agent learns to make decisions by taking actions in an environment to maximize some notion of cumulative reward. Q-learning specifically aims to learn the value of an action in a particular state, known as the Q-value, which represents the expected future rewards that can be obtained by taking that action in that state.

Example Drawing in class:

![[Pasted image 20240304133048.png]]

Basically consists of two networks which are the actor and critic (behavior and target policy). Input starts at the actor or behavior network which is where the agent is learning then eventually it will move to the critic network which will determine the q-values and apply the max function to choose the best action. 

## Temporal Difference (TD) Learning

**On-Policy Learning**

### SARSA Algorithm

*State, Action, Reward, State', Action'*

$$Q(S,A) \leftarrow\ Q(S,A)\ +\ \alpha(R\ +\gamma Q(S', A')\ -\ Q(S,A))$$
				![[Pasted image 20240228134720.png]]





---
# References
