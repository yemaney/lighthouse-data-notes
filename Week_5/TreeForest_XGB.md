# Decision Trees

The idea:
- builds `classification or regression` models in the form of a tree structure
- breaks down a dataset into smaller and smaller subsets while
- tree splits based on features
    - in order of the features that `seperate the data the best` 
    - to a specified depth
    - can be `pruned` to reduce overfitting, but bias can still exist
---
```python
from sklearn.tree import DecisionTreeClassifier # Import Decision Tree Classifier

from sklearn import metrics #Import scikit-learn metrics module for accuracy calculation

# Create Decision Tree classifer object
clf = DecisionTreeClassifier()

# Train Decision Tree Classifer
clf = clf.fit(X_train,y_train)

#Predict the response for test dataset
y_pred = clf.predict(X_test)
print("Accuracy:",metrics.accuracy_score(y_test, y_pred))
```
---
# Random Forrest
- Bagging
    - Bootstrap dataset:
        - `randomly sample data` with replacement
        - create decision tree for each sample, `randomly selecting features` for each
    - Aggregate:
        - use each bootstrap tree to make a prediction, and `agreggate them into one prediction`
    - Iterate with different number of variables, to `find the most accurate forrest`
---
```python
# Random Forest Classifier

from sklearn.ensemble import RandomForestClassifier

clf=RandomForestClassifier(n_estimators=100)

feature_imp = pd.Series(clf.feature_importances_,index=df.feature_names).sort_values(ascending=False)
```
     
```python
#Import Random Forest Regressor

from sklearn.ensemble import RandomForestRegressor

#Create a Gaussian Classifier
clf=RandomForestRegressor()
```
---
# XGBoost
Intended for large complicated datasets
- regression:
    1. pick where to divide tree by similarity/gain score:
        - similarity score: `(sum of res)`<sup>2</sup>` / num of res + lambda`
        - `Gain = left`<sub>`sim`</sub> `+ right`<sub>`sim`</sub> `- root`<sub>`sim`</sub>  
    2. pruning:
        - if gain - gamma > 0 don't prune
        - if gain - gamma < 0 prune the branch
    3. Output:
        - sum of res / num of res + lambd
    4. prediction:
        - `initial pred + learning rate * output`
- classification
    1. pick where to divide tree by similarity/gain score:
        - similarity score: `(sum of res)`<sup>2</sup> `/ sum( prev_prob * (1 - prev_prob)) + lambda`
        - if the denominator (cover) is less than the limit, then the tress is pruned
        - Gain = left<sub>sim</sub> + right<sub>sim</sub> i root<sub>sim</sub>  
    2. pruning:
        - if gain - gamma > 0 don't prune
        - if gain - gamma < 0 prune the branch
    3. Output:
        - sum of res /  sum( prev_prob * (1 - prev_prob)) + lambda
    4. prediction:
        - `logodds(initial pred) + learning rate * output`
        - `plug into logistic function to get new odds`
---
```python
import xgboost as xgb
from sklearn.metrics import mean_squared_error

data_dmatrix = xgb.DMatrix(data=X,label=y)

xg_reg = xgb.XGBRegressor(objective ='reg:linear', colsample_bytree = 0.3, learning_rate = 0.1,
                max_depth = 5, alpha = 10, n_estimators = 10)
xg_reg.fit(X_train,y_train)

preds = xg_reg.predict(X_test)

rmse = np.sqrt(mean_squared_error(y_test, preds))
print("RMSE: %f" % (rmse))


xg_reg = xgb.train(params=params, dtrain=data_dmatrix, num_boost_round=10)

# Plot xgb feature importance
import matplotlib.pyplot as plt
xgb.plot_importance(xg_reg)
plt.rcParams['figure.figsize'] = [5, 5]
plt.show()
```
---
- `bagging`, that often considers homogeneous weak learners, `learns them independently` from each other in parallel and combines them following some kind of `deterministic averaging process`
- `boosting`, that often considers homogeneous weak learners, learns them `sequentially` in a very adaptative way (a base model depends on the previous ones) and `combines them following a deterministic strategy`
- `stacking`, that often considers `heterogeneous` weak learners, `learns them in parallel` and combines them by training a meta-model to output a prediction based on the different weak models predictions
    - `differnt models outputs become the new inputs`