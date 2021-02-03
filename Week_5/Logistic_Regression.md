# Logistic Regrssion

- used for various classification problems 

- Binary Logistic Regression:
    - only two possible outcomes
- Multinomial Logistic Regression:
    - three or more nominal categories
- Ordinal Logistic Regression:
    - three or more ordinal categories
---
- sigmoid, l`ogistic function` gives an ‘S’ shaped curve that can take any real-valued number and `map it into a value between 0 and 1`
- If the output of the sigmoid function is `more than 0.5`, we can classify the outcome as `1 or YES`, and if it is `less than 0.5`, we can classify it as `0 or NO.`
---

### Model
```python
# import the class
from sklearn.linear_model import LogisticRegression

# instantiate the model (using the default parameters)
logreg = LogisticRegression()

# fit the model with data
logreg.fit(X_train,y_train)

#
y_pred=logreg.predict(X_test)
Model Evaluation using Confusion Matrix
```
### Evaluate on confusion matrix
```python
# import the metrics class
from sklearn import metrics
cnf_matrix = metrics.confusion_matrix(y_test, y_pred)
cnf_matrix


print("Accuracy:",metrics.accuracy_score(y_test, y_pred))
print("Precision:",metrics.precision_score(y_test, y_pred))
print("Recall:",metrics.recall_score(y_test, y_pred))
```
---
# Generalized Linear Models
Sometimes linear models are not good enough but can be modified to fit the data distribution better
1. Linear predictor
2. Link function
3. Probability distributino

```python
# Poisson regression code
import statsmodels.api as sm
exog, endog = sm.add_constant(x), y
mod = sm.GLM(endog, exog,
             family=sm.families.Poisson(link=sm.families.links.log))
res = mod.fit()
```
- Normal distribution: identity function
- Poisson distribution: log function
- Binomial distribution: logit function