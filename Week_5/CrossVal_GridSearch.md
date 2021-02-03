# Cross Validation

This process of deciding whether the numerical results quantifying hypothesized relationships between variables, are `acceptable as descriptions of the data`, is known as `validation`.

---
### The idea:
- We split the data, after shuffling, into a `training set` and `testing set`. But due to randomeness, we can still have `sampling bias` affecting the distribution of these two groups.
- Split the data into `K` groups, train on `K-1` of the folds, and test on the last.
    - Iterate until every group has been used as a test set once
- used to get an idea of how well the model works
---
### Spliting data into train and set sets
```python
import sklearn.model_selection as model_selection

X_train, X_test, y_train, y_test = model_selection.train_test_split(X,y,train_size=0.75,test_size=0.25, random_state=101)

#split data into test and train portions

```
### K_folds 
```python
from sklearn.model_selection import KFold

kf = KFold(n_splits=5, shuffle=True)
cv_r2 =[]
for train_index, test_index in kf.split(X):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]

    #Train model
    reg.fit(X_train, y_train)

    #evaluate the model on the test set
    y_pred = reg.predict(X_test)
    r2 = r2_score(y_test, y_pred)
    
    cv_r2.append(r2)
```
### Cross Val score
```python
from sklearn.model_selection import cross_val_score

cv_r2 = cross_val_score(reg,X,y,K=5,scoring='r2)
```
---
# Grid Search
- specify list of values to try for each `hyperparameter`
- train model using each combination of hyperparameters
- pick combo with lowest loss
```python
from sklearn.model_selection import GridSearchCV

param_grid = {'param1': [1,2,3],
            'param2': [2,4,6]}

grid = GridSearchCV(estimator=model, param_grid=param_grid, cv=K_folds, scoring='', verbose=1,n_jobs=-1)

grid_results = grid.fit(X_scaled, y)

best_r2 = grid_results.best_score_
best_param1 = grid_results.best_params_['param1']
```
---
- split data into `train` and `test` set
- perform `gridsearch with cross-val` on training set, each fold the training set will be split into a train/validation set
- using `hyperparameters with best score`, `retrain model` on entire training set
-`evaluate` model on test set