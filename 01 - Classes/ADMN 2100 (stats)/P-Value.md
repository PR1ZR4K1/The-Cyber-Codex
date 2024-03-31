2024/03/30 17:42
Status: #idea
Tags: [[Lesson 24 - t-tests]]

# P-Value

### Understanding the P-Value

The p-value is defined as the probability of obtaining test results at least as extreme as the ones observed during the test, assuming that the null hypothesis $H_0$ is true.

$$
p\text{-value} = P(T \geq t | H_0 \text{ is true})
$$

where $T$ is the test statistic and $t$ is the observed value of the test statistic.

- A **small p-value** (typically $\leq 0.05$) indicates strong evidence against the null hypothesis, leading us to reject $H_0$.
- A **large p-value** ($> 0.05$) suggests weak evidence against the null hypothesis, and therefore, we do not reject $H_0$.

When the p-value is less than the chosen significance level $\alpha$ (commonly set at 0.05, 0.01, or 0.001), the result is considered statistically significant, and it is unlikely that the observed effect is due to chance.

### P-Value in One-Tailed and Two-Tailed Tests

The p-value helps determine the significance of our test results. The interpretation of the p-value can differ based on whether we're conducting a one-tailed test or a two-tailed test.

![[Pasted image 20240330175507.png]]

#### One-Tailed Test

In a one-tailed test, we are interested in determining whether there is evidence to support that the population parameter is either greater than or less than a specified value.

$$
\text{For a right-tailed test (greater than): } p\text{-value} = P(T > t | H_0 \text{ is true})
$$
$$
\text{For a left-tailed test (less than): } p\text{-value} = P(T < t | H_0 \text{ is true})
$$

- If the p-value is less than or equal to the significance level $\alpha$, we reject the null hypothesis in favor of the alternative hypothesis.

#### Two-Tailed Test

In a two-tailed test, we check for the possibility of an effect in two directions, both greater than and less than.

$$
p\text{-value} = 2 \times P(T > |t| | H_0 \text{ is true})
$$

- The factor of 2 accounts for both tails of the distribution. Here, if the p-value is less than or equal to $\alpha$, we reject the null hypothesis, suggesting that the sample mean is significantly different from the hypothesized mean, in either direction.

#### Significance Level ($\alpha$)

The significance level $\alpha$ is a threshold chosen by the researcher to determine whether to reject $H_0$. Common values for $\alpha$ are 0.05, 0.01, and 0.001.

- **In a one-tailed test**, the entire alpha level is placed in one tail of the distribution.
- **In a two-tailed test**, the alpha level is split between the two tails, allocating $\alpha/2$ to each tail.






---
# References

- [[P-Value Example]]