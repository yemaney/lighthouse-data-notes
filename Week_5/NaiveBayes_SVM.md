# Naive Bayes
- used for classification 
- Tries to seperate observations using the probability rules of bayes theorom

<img src="https://miro.medium.com/max/1468/1*LB-G6WBuswEfpg20FMighA.png" alt="drawing" width="200" height="70"/>

- The general idea:
    1. Start off with an in initial or `prior probability` for each class
    2. Calculate the `odds of each attribute` for each class
    3. Use `bayes theorom` to calculate the odds of `each class with the given attributes`
    4. The class with the `highest odds is predicted` as the true by naive bayes 


```python
from sklearn.naive_bayes import GaussianNB 

gnb = GaussianNB() 

gnb.fit(X_train, y_train) 

y_pred = gnb.predict(X_test) 
```
---
# Support Vector Machines (SVM)
- used for classification
- tries to seperate observations by creating a theshold
    - shortest distance between observations and theshold is the `margin`
    - `maximum` margin classifiers use largest margin, but are sensitive to `outliers`
    - `soft` margin classifiers or support vector classifers allow for `misclassifications`
        - support vector classifiers can be a `point, line, plane, or hyperplane` depending on the dimensions involved
- The general idea:
    1. Start with data in a relatively `low` dimension
    2. Move the data into a `higher` dimension
    3. Find a `support vector classifiers` that seperates higher dimensional data into two groups
<img src="https://machine-learning-and-data-science-with-python.readthedocs.io/en/latest/_images/svm2.png" alt="drawing" width="200" height="70"/>
- Kernels:
    1. `polynomial` kernel: expands data into higher dimensions and cross validates to pick the optimal degree
    2. `radial` kernel: behaves like a weighted nearest neighbor model, where close observations have higher influence on how we classify new observations

```python
from sklearn import svm

clf = svm.SVC(kernel='poly') # polynom Kernel

clf.fit(X_train, y_train)

y_pred =clf.predict(X_test)
```