2024/03/30 20:08
Status: #idea
Tags: [[Lesson 21 - Hypothesis Testing]]

## Calculating Standard Deviation

Standard deviation is a measure of the amount of variation or dispersion in a set of values. It quantifies how much the values in the dataset deviate from the mean (average) of the dataset.

### Population Standard Deviation

Used when considering the entire population. The formula is:

$$
\sigma = \sqrt{\frac{\sum_{i=1}^{N} (x_i - \mu)^2}{N}}
$$

- $\sigma$ is the population standard deviation.
- $x_i$ represents each value in the population.
- $\mu$ is the population mean.
- $N$ is the total number of values in the population.
- The symbol $\sum$ denotes the summation of all values.

### Sample Standard Deviation

Used when working with a sample from the population. The formula is slightly different to correct for the bias in estimating a population parameter from a sample:

$$
s = \sqrt{\frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n-1}}
$$

- $s$ is the sample standard deviation.
- $x_i$ represents each value in the sample.
- $\bar{x}$ is the sample mean.
- $n$ is the total number of values in the sample.

### Steps to Calculate

1. **Find the Mean**: Sum all the data points and divide by the number of data points.
2. **Calculate Each Deviation**: For each data point, subtract the mean and square the result.
3. **Sum the Squared Deviations**: Add up all the squared deviations.
4. **Divide by $N$ (population) or $n-1$ (sample)**: This gives the variance.
5. **Take the Square Root**: This final step gives the standard deviation.

### Note on Notation

- The square root symbol $\sqrt{}$ denotes the square root.
- The summation symbol $\sum$ indicates the sum of all the squared deviations.

These steps apply whether you are calculating the standard deviation for a population or a sample, with the key difference being the divisor: use $N$ for population data and $n-1$ for sample data to correct for the bias in the estimation.








---
# References
