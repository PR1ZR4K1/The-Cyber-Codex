2024/04/26 18:36
Status: #idea
Tags: 

## Correlation Overview

### Introduction
- **Correlation** is a statistical measure that expresses the extent to which two variables are linearly related. It is a useful statistic that can indicate whether and how strongly pairs of variables are associated.

### Types of Correlation
- **Positive Correlation**: If one variable increases, the other variable tends to also increase.
- **Negative Correlation**: If one variable increases, the other variable tends to decrease.
- **No Correlation**: There is no linear relationship between the variables.

### Measurement
- Correlation is typically measured by the **Pearson Correlation Coefficient**, denoted as \( r \). The coefficient ranges from -1 to 1, where:
  - \( r = 1 \) indicates a perfect positive linear relationship,
  - \( r = -1 \) indicates a perfect negative linear relationship,
  - \( r = 0 \) indicates no linear relationship.
- The formula to calculate Pearson's \( r \) is:
$$
r = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum (x_i - \bar{x})^2 \sum (y_i - \bar{y})^2}}
$$
where:
  - \( x_i \) and \( y_i \) are the individual sample points indexed with \( i \),
  - \( \bar{x} \) and \( \bar{y} \) are the means of the \( x \) and \( y \) datasets, respectively.

### Example
Suppose we have a dataset of two variables, \( X \) and \( Y \), representing the hours studied and the scores on a test, respectively. Let's calculate the correlation coefficient for the following data:
- \( X: 1, 2, 3, 4, 5 \)
- \( Y: 2, 4, 5, 4, 5 \)

1. Calculate the means of \( X \) and \( Y \):
   - \( \bar{x} = 3 \),
   - \( \bar{y} = 4 \).

2. Apply the Pearson correlation formula:
   - Numerator: \( (1-3)(2-4) + (2-3)(4-4) + (3-3)(5-4) + (4-3)(4-4) + (5-3)(5-4) = 4 \)
   - Denominator: \( \sqrt{(10)(2)} = \sqrt{20} \)
   - \( r = \frac{4}{\sqrt{20}} \approx 0.894 \)

### Conclusion
The correlation coefficient of approximately \( 0.894 \) suggests a strong positive linear relationship between hours studied and test scores. This example shows how statistical methods can be used to quantify the degree of linear correlation between two variables.







---
# References

- [[Coefficient of Determination]]
- [[Independent and Dependent Variables]]
- [[Correlation vs Causation]]