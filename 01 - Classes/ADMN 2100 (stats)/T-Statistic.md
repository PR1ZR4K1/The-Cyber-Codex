2024/03/29 15:52
Status: #idea
Tags: [[Lesson 24 - t-tests]]

# T-Statistic

The t-statistic is a value calculated in a t-test that helps you determine whether to reject the null hypothesis. It measures the size of the difference between the sample mean and the hypothesized population mean $(\mu_0)$ relative to the variation in your sample data, taking into account the sample size. **Essentially, it's a standardized measure of how far the sample mean deviates from the hypothesized mean, expressed in terms of standard errors.**

#### Formula for T-Stat 
$$t =\frac{\bar{x}-\mu_0}{s/\sqrt{n}}$$

where:

- $\bar{x}$ is the sample mean,
- $\mu_0$ is the [[Hypothesized population mean]],
- $s$ is the [[Sample Standard Deviation]],
- $n$ is the sample size

## Graph example Udacity:

![[Pasted image 20240330160800.png]]

### One-Sample T-Test 

- the t-statistic is calculated by subtracting the population mean $(\mu_0)$ from the sample mean ($\bar{x}$), and then dividing the result by the standard error of the mean. The standard error of the mean is the standard deviation of the sample divided by the square root of the sample size.

## What does it do?

The **value of the t-statistic** tells you how many standard errors the sample mean is from the hypothesized mean. A large absolute value of the t-statistic indicates that the difference between the sample mean and the hypothesized population mean is large relative to the variability of the sample data. This can lead to rejecting the null hypothesis if the p-value (calculated from the t-statistic) is below a predetermined threshold (often 0.05 or 5%).




---
# References

- [[Sample Standard Deviation]],
- [[T-Table]], 
- [[Hypothesized population mean]],