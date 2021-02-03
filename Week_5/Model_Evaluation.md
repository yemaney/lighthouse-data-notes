# Model Evaluation
### Mean squared error

- MSE = 1/n sum(error<sup>2</sup>)
- commonly used
- large outliers have an effect

### Root Mean squared error
- units are inutitive

### Mean absolute error
- MAE = 1/n|error|
- outliers have less impact

### Coefficent of Determination R<sup>2</sup>
- R<sup>2</sup> = 1 - Unexplained Var / Explained Var = 1 - MSE<sub>2model</sub>/ MSE<sub>baseline</sub>
- Proportion of variation in dependant variable being explained by the independant variable
- can be adjusted for more columns in model

## Classification 
- Goal: prediect between two or more discrete classes



## Confusion Matrx
matrix of true positve, false positive, etc...
- accuracy
    - num of correct / num of predictions
- recall
    - Num of true positive / all true positive
    - `TP / TP + FN`
- false negative
    - num of false neg / all positive
- precision
    - num of true pos / num of pred pos
    - `TP / TP + FP`
- F1 score
    - 2 * (precision * recall) / (precision + recall)
---
## Metrics
``` python
from sklearn.metrics import mean_squared_error

RMSE = mean_squared_error(y_true,y_pred,squared=False)

from sklearn.metrics import accuracy_score

from sklearn.metrics import f1_score

from sklearn.metrics import roc_auc_score

```
---
## Confusion matrix plot
```python
from sklearn import metrics
cnf_matrix = metrics.confusion_matrix(y_test, y_pred)
cnf_matrix

import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline

class_names=[0,1] # name  of classes
fig, ax = plt.subplots()
tick_marks = np.arange(len(class_names))
plt.xticks(tick_marks, class_names)
plt.yticks(tick_marks, class_names)
# create heatmap
sns.heatmap(pd.DataFrame(cnf_matrix), annot=True, cmap="YlGnBu" ,fmt='g')
ax.xaxis.set_label_position("top")
plt.tight_layout()
plt.title('Confusion matrix', y=1.1)
plt.ylabel('Actual label')
plt.xlabel('Predicted label')
```
---
## ROC Curve 

plot of the true positive rate against the false positive rate. It shows the tradeoff between sensitivity and specificity.

```python
y_pred_proba = logreg.predict_proba(X_test)[::,1]
fpr, tpr, _ = metrics.roc_curve(y_test,  y_pred_proba)
auc = metrics.roc_auc_score(y_test, y_pred_proba)
plt.plot(fpr,tpr,label="data 1, auc="+str(auc))
plt.legend(loc=4)
plt.show()
```
