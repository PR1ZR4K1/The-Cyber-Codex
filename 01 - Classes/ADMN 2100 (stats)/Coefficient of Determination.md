
2024/04/12 18:20
Status: #idea
Tags: [[Lesson 24 - t-tests]]

## Coefficient of Determination (R²) Overview

### Introduction
- **Coefficient of Determination (\( R^2 \))** quantifies the amount of variance in the dependent variable that is predictable from the independent variables.
- It is a key output of regression analysis.

### Calculation
- **Formula**:
$$
R^2 = 1 - \frac{SS_{res}}{SS_{tot}}
$$
where:
- \( SS_{res} \) is the sum of squares of residuals, which measures the variability left unexplained after performing the regression.
- \( SS_{tot} \) is the total sum of squares, which measures the total variance in the dependent variable.

### Interpretation
- \( R^2 \) values range from 0 to 1.
  - An \( R^2 \) of 0 means that the dependent variable cannot be predicted from the independent variable.
  - An \( R^2 \) of 1 means the dependent variable can be predicted without error from the independent variable.
- Higher values of \( R^2 \) indicate a better fit of the model to the data.

### Example Calculation
Suppose in a linear regression model, the total variance (\( SS_{tot} \)) of the response variable is 100 and the unexplained variance (\( SS_{res} \)) after the model is fitted is 40.

- Calculate \( R^2 \):
$$
R^2 = 1 - \frac{40}{100} = 0.60
$$

### Uses
- **Model Evaluation**: Commonly used to evaluate the effectiveness of a model in explaining the variation in the outcome.
- **Comparative Analysis**: Can be used to compare the explanatory power of regression models on the same data.

### Advantages
- **Intuitive Measure**: Provides an easy-to-understand measure of model predictive power.
- **Normalization**: Ranges between 0 and 1, facilitating easy comparisons between models.

### Limitations
- **Non-Discriminatory**: A high \( R^2 \) does not imply that the regression model is appropriate. Other statistical tests are needed to confirm model validity.
- **Sensitive to Overfitting**: Adding more predictors to a model can artificially increase \( R^2 \), regardless of whether the predictors are meaningful.






---
# References
