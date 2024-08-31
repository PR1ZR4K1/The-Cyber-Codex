2024/06/25 11:01
Status: #idea
Tags: [[Machine Learning]], [[Classification vs Regression]]

## Logistic Regression Overview

### Introduction
- **Logistic Regression** is a statistical method for predicting binary outcomes from data. Examples of binary outcomes include yes/no, true/false, or any scenario where there are two distinct categories. Despite its name, logistic regression is used in classification tasks, not regression.

### Core Principle
- The goal of logistic regression is to find the best-fitting model to describe the relationship between the dichotomous characteristic of interest (dependent variable) and a set of independent variables.

### How It Works
- Logistic regression predicts the probability of the outcome using a logistic function, which is an S-shaped curve that maps any real-valued number into the range 0 to 1, making it suitable for modeling probability.

### Mathematical Formulation
- The logistic function, also called the sigmoid function, is defined as:
$$
P(Y=1|X) = \frac{1}{1 + e^{-(\beta_0 + \beta_1X)}}
$$
where:
  - $P(Y=1|X)$ is the probability of the dependent variable equaling a 'success' or '1' given the independent variables.
  - $X$ represents the independent variables.
  - $\beta_0$ and $\beta_1$ are the parameters of the model.
  - $e$ is the base of the natural logarithm.

### Key Concepts

1. **Odds and Log Odds**
   - **Odds**: The ratio of the probability of the event occurring to the probability of the event not occurring.
   - **Log Odds (Logit)**: The natural logarithm of the odds. The logistic regression model actually models the log odds as a linear relationship with the predictors.

2. **Estimation**
   - Parameters are typically estimated using maximum likelihood estimation (MLE), which seeks to maximize the likelihood function, making the observed values of the dependent variable as probable as possible.

### Model Fitting
- The fit of the logistic regression model is assessed using tests like the likelihood ratio test, Wald test, and score test. These tests evaluate the significance of individual predictors or the model as a whole.

### Applications
- **Medical Fields**: Predicting the presence or absence of a disease (e.g., diabetes, cancer based on patient characteristics).
- **Financial Services**: Credit scoring to predict if a borrower will default on a loan.
- **Marketing**: Predicting customer retention, purchasing decisions, and brand switching.

### Advantages
- **Probabilistic Approach**: Provides probabilities for outcomes, which can be more informative than simple binary predictions.
- **Interpretability**: Each coefficient in the model explains the relative impact of a corresponding feature.

### Challenges
- **Assumption of Linearity**: Assumes a linear relationship between the log odds of the outcome and each predictor.
- **Sensitive to Outliers**: Extreme values can distort the outcome and explanatory variables.
- **Multicollinearity**: High correlation among predictor variables can make the model estimation less precise.

### Conclusion
Logistic regression is a robust and widely used statistical method for binary classification. It offers clear interpretability and the ability to assess the influence of several predictor variables simultaneously. Understanding its assumptions and limitations is crucial for effective application in real-world scenarios.









---
# References
