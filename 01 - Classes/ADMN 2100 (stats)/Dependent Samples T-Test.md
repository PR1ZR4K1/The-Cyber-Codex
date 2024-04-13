2024/04/12 18:08
Status: #idea
Tags: [[Lesson 24 - t-tests]]

## Dependent Samples t-test Overview

### Introduction
- **Dependent Samples t-test** (or Paired Samples t-test) is used to compare the means from two related groups to determine if there are statistically significant differences between these means.
- Commonly used when the same subjects are tested under two different conditions, such as testing the same group with two different keyboard layouts.

### Calculation
- **Formula**:
$$
t = \frac{\bar{d}}{s_{\bar{d}} / \sqrt{n}}
$$
where:
- $(\bar{d})$ is the mean of the differences between all paired observations.
- $(s_{\bar{d}})$ is the standard deviation of these differences.
- $(n)$ is the number of pairs (or sample size).

### Example Calculation
Imagine a study with 25 participants who are asked to type on two different keyboard layouts, and the number of errors made with each layout is recorded. Suppose the mean difference in the number of errors (Layout 1 - Layout 2) is $-3$ (indicating fewer errors with Layout 2), and the standard deviation of these differences is $4$.

- Calculate the t-value:
$$
t = \frac{-3}{4 / \sqrt{25}} = \frac{-3}{0.8} = -3.75
$$

### Interpretation
- A t-value of $-3.75$ suggests a significant difference in the number of errors between the two keyboard layouts, assuming an appropriate critical t-value from the t-distribution table based on the desired confidence level and degrees of freedom $(df = n-1 = 24)$.

### Uses
- **Usability Testing**: Evaluate the effectiveness of different interfaces or tools.
- **Medical Research**: Compare treatment effects where patients receive both treatments in succession.

### Advantages
- **Sensitive to Small Changes**: Can detect differences between means when the same participants are involved in both conditions, reducing variability.
- **Efficient Use of Data**: By pairing the data, each pair acts as its own control, enhancing the efficiency of the analysis.

### Limitations
- **Assumption of Normality**: Assumes that the differences between paired observations are normally distributed.
- **Not Suitable for Independent Samples**: Cannot be used if the samples do not consist of the same subjects or matched pairs.


---
# References

- [[Types of Dependent Sample T-Test Designs]]
- [[Confidence Interval]]
- [[Standard Error]]
- [[Margin of Error]]
- [[Standard Deviation]]
- [[T-Statistic]]