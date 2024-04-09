2024/04/07 17:04
Status: #idea
Tags:

## Distributions 

*Assume that each variable in the network is Boolean. Please note that P(S|c) and P(R|c) indicate only the probabilities P(+s|c) and P(+r|c) in the above tables.*

2. Fill in the factor table for (Sprinkler + Rain) (be careful about above when calculating the probabilities.

![[Pasted image 20240407170837.png]]


#### Conditional Probability Tables

| C   | S   | P(S\|C) |
| --- | --- | ------- |
| +c  | +s  | 0.1     |
| -c  | +s  | 0.5     |
| +c  | -s  | 0.9     |
| -c  | -s  | 0.5     |

| C   | R   | P(R\|C) |
| --- | --- | ------- |
| +c  | +r  | 0.8     |
| -c  | +r  | 0.2     |
| +c  | -r  | 0.2     |
| -c  | -r  | 0.8     |

### Find P(S, R)

Formula 

$$P(S, R|C) = P(S|C)*P(R|C)$$
*Top half of joint distribution table of P(S,R)*

$P(+s, +r|+c) = P(+s|+c)*P(+r|+c)$
$P(+s, +r|+c) = 0.1*0.8$
$P(+s, +r|+c) = 0.08$

$P(+s, -r|+c) = P(+s|+c)*P(-r|+c)$
$P(+s, -r|+c) = 0.1*0.2$
$P(+s, -r|+c) = 0.02$

$P(-s, +r|+c) = P(-s|+c)*P(+r|+c)$
$P(-s, +r|+c) = 0.9*0.8$
$P(-s, +r|+c) = 0.72$

$P(-s, -r|+c) = P(-s|+c)*P(-r|+c)$
$P(-s, -r|+c) = 0.9*0.2$
$P(-s, -r|+c) = 0.18$

| C   | S   | R   | P(S,R\|c) |
| --- | --- | --- | --------- |
| +c  | +s  | +r  | 0.08      |
| +c  | +s  | -r  | 0.02      |
| +c  | -s  | +r  | 0.72      |
| +c  | -s  | -r  | 0.18      |
| -c  | +s  | +r  | 0.1       |
| -c  | +s  | -r  | 0.4       |
| -c  | -s  | +r  | 0.1       |
| -c  | -s  | -r  | 0.4       |

*Bottom Half of Joint Distribution of P(S,R)*

$P(+s, +r|-c) = P(+s|-c)*P(+r|-c)$
$P(+s, +r|-c) = 0.5*0.2$
$P(+s, +r|-c) = 0.1$

$P(+s, -r|-c) = P(+s|-c)*P(-r|-c)$
$P(+s, -r|-c) = 0.5*0.8$
$P(+s, -r|-c) = 0.4$

$P(-s, +r|-c) = P(-s|-c)*P(+r|-c)$
$P(-s, +r|-c) = 0.5*0.2$
$P(-s, +r|-c) = 0.1$

$P(-s, -r|-c) = P(-s|-c)*P(-r|-c)$
$P(-s, -r|-c) = 0.5*0.8$
$P(-s, -r|-c) = 0.4$


1. `Icy Weather`: No parents, 2 values (T, F), but only 1 probability value is needed because the probability of it being false is 1 minus the probability of it being true.
2. `Battery`: 1 parent (`Icy Weather`), 4 combinations of truth values, but only 2 independent probability values needed (since for each state of `Icy Weather`, the probabilities of `Battery` sum to 1).
3. `Starter Motor Working`: 1 parent (`Icy Weather`), 4 combinations, but only 2 independent probability values are needed.
4. `Radio`: 1 parent (`Battery`), 4 combinations, but only 2 independent probability values are needed.
5. `Ignition`: 1 parent (`Battery`), 4 combinations, but only 2 independent probability values are needed.
6. `Gas`: No parents, 1 independent probability value needed.
7. `Starts`: 3 parents (`Battery`, `Starter Motor Working`, `Ignition`), 23=823=8 combinations, but only 23−1=723−1=7 independent probability values needed for each state of the 3 parents.
8. `Moves`: 1 parent (`Starts`), 4 combinations, but only 2 independent probability values are needed.

Adding these up: 1+2+2+2+2+1+7+2=19 independent probability values for the CPTs of the entire network.


---
# References
