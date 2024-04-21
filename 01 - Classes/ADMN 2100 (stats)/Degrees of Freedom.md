2024/04/20 16:25
Status: #idea
Tags: [[Lesson 24 - t-tests]]


## Degrees of Freedom (df) Overview

### Introduction
- **Degrees of Freedom** typically represent the number of values in a calculation that are free to vary. They are crucial in statistical modeling to estimate certain parameters, and the concept plays a central role in tests like t-tests, where it helps determine the critical values from the t-distribution.

### General Concept
- The degrees of freedom in a statistical calculation are often equal to the number of observations minus the number of necessary constraints (such as the estimation of parameters like the mean).

### Degrees of Freedom in T-Tests

#### Independent Samples T-Test
- **Formula**:
$$
df = n_1 + n_2 - 2
$$
where:
- \(n_1\) and \(n_2\) are the sample sizes of the first and second groups, respectively.
- The subtraction of 2 represents removing one degree of freedom for each sample mean estimated.

- **Explanation**: For an independent samples t-test, the degrees of freedom are calculated by summing the sample sizes of the two groups and subtracting 2. This accounts for the estimation of two independent means from the two samples.

#### Dependent Samples T-Test
- **Formula**:
$$
df = n - 1
$$
where:
- \(n\) is the number of pairs in the sample.

- **Explanation**: In a dependent samples t-test, also known as a paired samples t-test, the degrees of freedom are calculated by subtracting one from the number of paired observations. This subtraction accounts for the estimation of one mean difference, not two separate means as in the independent samples t-test.

### Importance of Degrees of Freedom
- **Statistical Testing**: Degrees of freedom are used to determine the critical values from statistical distributions like the t-distribution, which are necessary for hypothesis testing.
- **Correct Estimation**: Proper calculation of degrees of freedom ensures accurate estimation of test statistics and p-values, leading to valid conclusions in hypothesis testing.

### Conclusion
Understanding degrees of freedom is essential for properly conducting statistical tests and interpreting their results. It helps in ensuring that the statistical parameters are estimated correctly and that the conclusions drawn from statistical tests are valid.









---
# References
