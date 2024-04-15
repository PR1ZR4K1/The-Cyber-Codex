2024/04/12 17:39
Status: #idea
Tags: [[Lesson 24 - t-tests]]

## Margin of Error Overview

### Introduction
- **Margin of Error (MoE)** quantifies the uncertainty in estimates from sample surveys.
- It indicates the range within which the true population parameter is expected to fall with a certain level of confidence.

### Calculation
- **Formula**:
$$
MoE = z \times \frac{\sigma}{\sqrt{n}}
$$
where:
- $(z)$ is the z-score corresponding to the desired confidence level (e.g., 1.96 for 95% confidence).
- $(\sigma)$ is the standard deviation of the population. If unknown, the sample standard deviation $(s)$ is used as an estimate.
- $(n)$ is the sample size.

### Example Calculation
Assume a 95% confidence level (z-score = 1.96), a sample standard deviation $(s = 15)$, and a sample size $(n = 200)$.

- Calculate the Margin of Error:
$$
MoE = 1.96 \times \frac{15}{\sqrt{200}} \approx 2.07
$$

### Interpretation
- The Margin of Error tells us that the true population mean is likely within $\pm 2.07$ units of the sample mean for 95% of similar samples.

### Uses
- **Survey Results**: Widely used in reporting survey results to express the precision of sample estimates.
- **Election Polls**: Essential in interpreting the closeness of electoral races.
- **Market Research**: Helps businesses understand the variability in consumer preferences and behaviors.

### Advantages
- **Simplified Interpretation**: Provides a straightforward way to communicate the uncertainty in estimates.
- **Enhanced Decision Making**: Aids stakeholders in making decisions based on the reliability of the data provided.

### Limitations
- **Assumes Normal Distribution**: Most effective when the sample size is large or the population distribution is normal.
- **Sample Size Dependent**: Larger samples tend to have a smaller Margin of Error, implying more precise estimates.


---
# References

- [[Standard Error]]
- [[Sample Standard Deviation]]
- [[T-Statistic]]