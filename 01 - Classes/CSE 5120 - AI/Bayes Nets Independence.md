2024/03/18 13:04
Status: #idea
Tags:

# Probabilities in Bayes Nets (BNs)

### Local Semantics 

Each node is conditionally independent of its nondescendants  given its parents.

### Markov Blanket 

Each node is conditionally independent of all others given its Markov blanket: parents + children + children's parents.

#### Example: Traffic

![[Pasted image 20240318132301.png]]

$$P(+r, -t) = P(+r)P(-t|+r) = \frac{1}{4}*\frac{1}{4}$$
## Probability Recap

Conditional Probability: $$P(x|y) = \frac{P(x, y)}{P(y)} $$
Product Rule: $$P(x, y) = P(x|y)P(y)$$
Chain Rule:$$P(x_{1,}x_{2}, ..., x_{n)}= \prod^n_{i=1} P(x_1|x_{i-1})$$
## D-Separation

**A condition/algorithm for answering such queries**

- Study the independence properties for triples
- Analyze the complex cases in terms of member triples 

### Active/Inactive Paths

![[Pasted image 20240318135655.png]]

![[Pasted image 20240318135900.png]]  

---
# References
