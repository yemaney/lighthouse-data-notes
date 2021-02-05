# Naive Bayes

```python
from sklearn.naive_bayes import GaussianNB 

gnb = GaussianNB() 

gnb.fit(X_train, y_train) 

y_pred = gnb.predict(X_test) 
```
---
# Support Vector Machines (SVM)
```python
from sklearn import svm

clf = svm.SVC(kernel='poly') # polynom Kernel

clf.fit(X_train, y_train)

y_pred =clf.predict(X_test)
```