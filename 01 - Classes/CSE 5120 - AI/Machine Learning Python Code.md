2024/03/27 13:18
Status: #idea
Tags:

# Python Code Flow

- import required libraries

``` python
import numpy
import pandas
import matplotlib.pyplot
import standardscaler
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
#%% Support Vector Classifier %%
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score, confusion_matrix
from sklearn import DecisionTreeClassifier
```

#### Load Dataset

```python

dataset = pd.read_csv('Social_Network_Ads.csv')

#%% all columns except the last one %%
x = dataset.iloc[:,:-1]

#%% only grab the final column %%
y = dataset.iloc[:, -1]


```
#### Training and Testing Split

Split the dataset into two pieces which is the training set and the testing set so that you can train your model and then test it. Typically 25% of the dataset will be used for the test set.

```python
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.25)
```

*This function will randomly shuffle your data. In order to have the exact same results for each run add 'random_state=value'*

```python
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.25, random_state=0)
```

#### Data Preprocessing

**Make sure to do train and test split before data preprocessing to avoid standardizing data with test set.**

```python
sc = StandardScaler()

x_train = sc.fit_transform(x_train)
x_test = sc.fit_transform(x_test)

```
#### Model Development

**It is really important to visualize the data to find out what your data distribution looks like before you create a model.**

Radial Basis Function (RBF) - is a popular kernel function used to split data that is not separated linearly

```python
#%% assume data set is linear %%
# with the data visualization you should be able to see that a linear SVC is not the most optimal instead you can use rbf for a non-linear dataset or gaussian curve

# classifier = SVC(kernel='rbf', random_state=0)

classifier = SVC(kernel='linear', random_state=0)

# classifier = DecisionTreeClassifier(criterion='entropy', random_state=0)
# classifier.fit(x_train, y_train)

classifier.fit(x_train, y_train)

print(classifier.predict(sc.transform([[30, 87000]])))
```

#### Accuracy Test

```python

y_pred = classifier.predict(x_test)
cm = confusion_matrix(y_test, y_pred)

print(cm)
print(accuracy_score(y_test, y_pred))
```












---
# References
