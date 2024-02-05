2024/02/03 16:41
Status: #idea
Tags:

# Intelligent Agents

An ***agent*** is anything that can be viewed as perceiving its environment through sensors and acting upon that environment through **actuators**.

<mark style="background: #FFF3A3A6;">Percept</mark> - refers to the content an agent's sensors are perceiving.

<mark style="background: #FFF3A3A6;">Percept Sequence</mark> - is the complete history of everything the agent has ever perceived.

*\*In general an agent's choice of action at any given instant can depend on its built-in knowledge and on the entire percept sequence observed to date, but not on anything it hasn't perceived\**

<mark style="background: #FFF3A3A6;">Agent Function</mark> - described an agents behavior by mapping any given *percept sequence* to an action. (abstract mathematical description)

<mark style="background: #FFF3A3A6;">Agent Program</mark> - concrete implementation, running within some physical system.

#### Agent Function vs. Program

Imagine creating a table for an agent where we try every possible percept sequence and record the action the agent does in response. This would be an *external characterization* of the agent. *Internally* the *agent function* for an artificial agent will be implemented by an *agent program*. 

<mark style="background: #FFF3A3A6;">Rational Agent</mark> - is one that does the right thing

## The Concept of Rationality

What is rational at any given time depends on four things:

- The performance measure that defines the criterion of success
- The agent's prior knowledge of the environment
- The actions that the agent can perform
- The agent'a percept sequence to date

Definition of a rational agent:

*\*For each possible percept sequence, a rational agent should select an action that is expected to maximize its performance measure, given the evidence provided by the percept sequence and whatever built-in knowledge the agent has\**

**A rational agent should be autonomous**

<mark style="background: #FFF3A3A6;">Autonomy</mark> - learning what it can do to compensate for partial or incorrect prior konwledge.


---
# References
