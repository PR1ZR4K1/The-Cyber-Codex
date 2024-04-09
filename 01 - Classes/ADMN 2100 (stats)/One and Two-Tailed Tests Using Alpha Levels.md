2024/03/30 19:43
Status: #idea
Tags: [[Lesson 24 - t-tests]]

### One and Two-Tailed Tests Using Alpha Levels

When performing hypothesis testing, the nature of your alternative hypothesis ($H_a$) dictates whether you use a one or two-tailed test. This choice affects how you use alpha levels ($\alpha$) and interpret the z-table.

#### One-Tailed Test

In a one-tailed test, you are testing for the probability of the effect in just one direction—either greater than or less than the hypothesized parameter value.

- **Right-tailed test**: You set the entire alpha level in the right tail of the distribution. If your test statistic z exceeds the z-score found in the z-table corresponding to $1-\alpha$, you reject $H_0$.

$$
P(Z > z) < \alpha
$$

- **Left-tailed test**: You place the entire alpha level in the left tail of the distribution. If your test statistic z is less than the negative of the z-score corresponding to $\alpha$, you reject $H_0$.

$$
P(Z < -z) < \alpha
$$

#### Two-Tailed Test

A two-tailed test assesses the probability of the effect in both directions, implying two possible extreme areas in the sampling distribution where the null hypothesis can be rejected.

- You split the alpha level across both tails of the distribution. This means you have $\alpha/2$ in each tail.
- To reject $H_0$, the absolute value of your test statistic z must exceed the z-score corresponding to $1-\alpha/2$ in the positive tail or be less than the z-score corresponding to $\alpha/2$ in the negative tail.

$$
P(|Z| > z) < \alpha
$$

#### Reference to Z-Table

The z-table provides cumulative probabilities for the standard normal distribution (z-distribution). For a given alpha level:

- **In a one-tailed test**, find the z-score that corresponds to $1-\alpha$ or $\alpha$.
- **In a two-tailed test**, look up the z-score corresponding to $1-\alpha/2$ for the upper tail and $\alpha/2$ for the lower tail.

When you compare your calculated z to the z-table values:

- If the calculated z is in the critical region (beyond the z-table value), you reject $H_0$.
- If the calculated z is not in the critical region, you do not reject $H_0$.

### Example Two-Tailed Probability for all alpha levels


![[Pasted image 20240330192923.png]]

#### Using the z-table find the z-critical value.

- **$\alpha = 0.05$ (5%)**


Find the box who's value equates to 2.5% or 0.025 and using the row and column it belongs to you will have the z-critical value.

z-critical = $\pm \ 1.96$


#### Using the z-table find the z-critical value.

- **$\alpha = 0.01$ (1%)**

Find the box who's value equates to 1% or 0.005 and using the row and column it belongs to you will have the z-critical value.

z-critical = $\pm \ 2.57$

#### Using the z-table find the z-critical value.

- **$\alpha = 0.001$ (0.1%)**

Find the box who's value equates to 0.1% or 0.0005 and using the row and column it belongs to you will have the z-critical value.

z-critical = $\pm \ 3.32$





---
# References

- [[Alpha Levels]]