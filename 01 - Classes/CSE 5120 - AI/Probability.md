 2024/03/06 13:08
Status: #MOC
Tags:

# Uncertainty and Probability

***The majority of real-world problems have to deal with uncertainty***

**General Situation:**

- **Observed Variables (evidence):** Agent knows certain things about the state of the world (eg. symptoms that a patient has observed that they tell a doctor.)
- **Unobserved Variables:** Agent needs to reason about other aspects (eg. where an object is or what disease is present)
- **Model:** Agent knows something about how the known variables relate to the unknown variables.

### Random Variables and Instantiations/Assignments

- Random variables will be denoted with a capital letter.
- When you assign a value to this variable you will have it lower case.

#### Variable Types

Example Binary Variable:

R = is it raining only available assignments are t or f.
r in {true, false} often write as {+r, -r}

Example Discrete Variable:

T = is it hot or cold?
t in {hot, cold}

Example continuous Variables:

D = How long will it take to drive to work?
d in \[0, $\infty$]

### Probability Distribution

Table of probabilities of values:

![[Pasted image 20240306133616.png]]

#### Laws of Probability

$$P(W=rain) =0.1$$
$$\forall x \quad P(X = x) \geq 0$$
$$\sum_{x} P(X=x) = 1$$
#### Types of Distribution

- <mark style="background: #FFF3A3A6;">Joint  Distribution</mark> - Describes the probability of different outcomes occurring simultaneously with two or more random variables.
	- Example: 
	![[Pasted image 20240306134035.png]]
	- Size of distribution if 'n' variables with domain sizes 'd': $(d^n)$
	- Working directly with joint distributions is often not possible because of the size.

- <mark style="background: #FFF3A3A6;">Marginal Distribution</mark> - is the probability distribution of a random variable ignoring the presence or effects of any other variables. Are sub-tables which eliminate variables
	- Example
	![[Pasted image 20240306135134.png]]
 

- <mark style="background: #FFF3A3A6;">Conditional Distribution</mark> - Describes the probability distribution of one variable given that another variable has a specific value
	- Equation:
		$$P(a|b) = \frac{P(a, b)}{P(b)}$$
	- Example:
	![[Pasted image 20240306140247.png]]

## Normalization

Example 1: 

![[Pasted image 20240306140848.png]]

Example 2:

![[Pasted image 20240306140919.png]]

**Select**

+x | 0.3
-x | 0.1

Z = 0.3 + 0.1 = 0.4

**Normalize**

+x | $(\frac{0.3}{Z})$ = 0.749
-x | $(\frac{0.1}{Z})$ = 0.25

### Inference by Enumeration

Class example:



### Probabilistic Models

**Is a joint distribution over a set of random variables**

![[Pasted image 20240306134418.png]]

The P column is referred to as the *outcome* 

#### Event

**Is a set (E) of outcomes**

$$P(E)= \sum_{(x_{1\ldots}x_{n)}\ \in\ E} P(x_{1}\ldots x_n)$$

## Chain Rule 

Chain rule says that we can always write the joint distribution as an incremental product of conditional distributions

$$ P(x_1, x_2, x_3) = P(x_1)P(x_2|x_1)P(x_3|x_1, x_2)$$
$$P(x_1, x_2, \ldots, x_n) = \prod_{i} P(x_i|x_1, \ldots, x_{i-1})$$
## Bayes' Rule

Two ways to factor a joint distribution over two variables:

	P(x,y) = P(x|y)P(y) = P(y|x)P(x)

Dividing we get:

	$P(x|y) = \frac{P(y|x)}{P(y)}P(x)$

This is helpful because sometimes one conditional is tricky but the other one is simple.

**VERY IMPORTANT**

It is the foundation of many systems eg. Automatic Speech Recognition, Machine Translation

![[Pasted image 20240311132428.png]]

### Exercise: Baye's Rule

Given P(w):
![[Pasted image 20240311132515.png]]

Given P(D|W)
![[Pasted image 20240311132533.png]]

What is P(W|dry)?

## Global Semantics

$$P(d \wedge t \wedge a \wedge \neg b \wedge \neg e)$$



---
