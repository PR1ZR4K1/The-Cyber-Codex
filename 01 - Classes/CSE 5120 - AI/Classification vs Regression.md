2024/03/25 13:27
Status: #idea
Tags:

# Classification vs Regression

- **Classification** predicts discrete labels, meaning it categorizes data into predefined classes or groups. The outcome is a category, such as "spam" or "not spam" for an email filtering system.
    
- **Regression** predicts continuous outcomes, which means it estimates a numeric value based on input data. The outcome is a real number, like the price of a house or the temperature tomorrow.
    

In simple terms, classification is about answering "what class?" and regression is about answering "how much?" or "how many?".

### Supervised Learning

**Clasify friends by names, categorize tweets**

Imagine you have a very large dataset of different tweets that are all labeled with the different classifications already assigned to them. Now using the data that you provided to it the model can make assumptions about new tweets with about 90% accuracy which for this use case is really good.
*In the context of health 98-99% accuracy is absolutely necessary*

### Unsupervised Learning

**Percent graduation per county**

Imagine trying to determine what each beam of light is supposed to represent when looking from a hubble telescope. This also means that the output variable is not discrete or specifically categorized.

### Reinforcement Learning

Robot climbing without falling

## Machine Learning Development Pipeline

#### Problem Definition

- Understanding what you are trying to solve.
- Defining the objectives and criteria for success.
- Assessing whether ML is the right solution.

#### Data Collection

- Gathering the raw data that will be used to train the model.
- Ensuring the data is representative of the problem space.

#### Data Pre-Processing

- Handling missing values, outliers, and errors.
- Normalizing or standardizing features.
- Feature engineering to create new variables from existing ones.
- Splitting the data into training, validation, and test sets.

#### Exploratory Data Analysis

- Analyzing the data to find patterns, trends, and anomalies.
- Using statistical tools and visualizations to understand data distributions. 

#### Model Development


#### Model Evaluation 

- Assessing model performance with validation sets using appropriate metrics (accuracy, precision, recall, F1 score for classification; MSE, RMSE, MAE for regression).
- Comparing different models and selecting the best performer.

#### Hyper-Parameter Tuning

- Refining the model by tuning hyperparameters.
- Using techniques like cross-validation to ensure generalizability.
- Employing ensemble methods or boosting techniques if necessary.



---
# References
