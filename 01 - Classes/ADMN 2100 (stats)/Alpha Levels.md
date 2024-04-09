2024/03/30 18:45
Status: #idea
Tags: [[Lesson 24 - t-tests]]

### Alpha Level (Significance Level)

The alpha level, denoted as $\alpha$, is the threshold value used in hypothesis testing to determine whether to reject the null hypothesis $H_0$. It represents the maximum probability of committing a Type I error — rejecting the null hypothesis when it is actually true.

#### Definition

$$
\alpha = P(\text{Reject } H_0 | H_0 \text{ is true})
$$

- The alpha level is the probability of incorrectly detecting an effect or difference (false positive).
- Common alpha levels are 0.05, 0.01, and 0.001.

#### Context of Probability

- When the p-value is less than $\alpha$, we reject $H_0$ because the evidence suggests that the observed result is statistically significant and not likely due to random chance.
- The choice of $\alpha$ affects the sensitivity of the hypothesis test. A smaller $\alpha$ means a more stringent criterion for rejecting $H_0$, reducing the risk of a Type I error but increasing the risk of a Type II error (failing to reject $H_0$ when it is false).

#### In Hypothesis Testing

- The alpha level sets the standard for how extreme the data must be to reject $H_0$.
- It is used as a benchmark against the p-value: if $p \leq \alpha$, the results are deemed significant, and we have sufficient evidence to reject $H_0$ in favor of the alternative hypothesis $H_a$.


---
# References

- [[Null and Alternative Hypothesis]]