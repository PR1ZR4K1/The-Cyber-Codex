2024/04/12 17:45
Status: #idea
Tags: [[Lesson 24 - t-tests]], [[Margin of Error]]

## Confidence Interval Overview

### Introduction
- **Confidence Interval (CI)** is a type of interval estimate of a population parameter.
- It's used to indicate the reliability of an estimate.
- A confidence interval provides a range of values that likely include the unknown population parameter.

### Calculation
- **Formula**:
$$
CI = (\bar{x} \pm z \times \frac{\sigma}{\sqrt{n}})
$$
where:
- $(\bar{x})$ is the sample mean.
- $(z)$ is the z-score corresponding to the desired confidence level (e.g., 1.96 for 95% confidence).
- $(\sigma)$ is the standard deviation of the population. If unknown, the sample standard deviation $(s)$ is used as an estimate.
- $(n)$ is the sample size.

### Example Calculation
Assume you want to calculate a 95% confidence interval for a sample mean $(\bar{x} = 50)$, with a sample standard deviation $(s = 10)$ and a sample size $(n = 100)$.

- Calculate the Confidence Interval:
$$
CI = (50 \pm 1.96 \times \frac{10}{\sqrt{100}}) = (50 \pm 1.96 \times 1) = (48.04, 51.96)
$$

### Interpretation
- The Confidence Interval tells us that we are 95% confident that the true population mean lies between $48.04$ and $51.96$.

### Uses
- **Research**: Commonly used in scientific research to report the reliability of estimate studies.
- **Data Analysis**: Essential in data analysis for understanding the accuracy of statistical estimates.

### Advantages
- **Reliability Indicator**: Provides a method to assess the reliability and variability of the sample estimates.
- **Decision Making**: Helps in making decisions based on the interval estimate.

### Limitations
- **Assumes Normal Distribution**: Most effective when the sample data is normally distributed or the sample size is large.
- **Misinterpretations**: Confidence intervals can be misunderstood. The interval itself does not imply that all values within the interval are equally probable.









---
# References

- [[Standard Deviation]]
- [[Standard Error]]