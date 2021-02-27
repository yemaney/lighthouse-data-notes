# Pipelines

### The idea:
- Building a model is a process that involves many steps, such as:
    - preprocessing data
    - choosing an algorithm 
    - cross-validation
### A pipeline: 
- is  a way to streamline these steps into one process 
- chains together multiple steps
    - each steps output becomes, the next steps input
```python
### super basic pipeline
# pipeline specific imports
from sklearn.compose import ColumnTransformer
from sklearn.pipeline import Pipeline
from sklearn.impute import SimpleImputer

# pipeline for numeric data
numeric_transformer = Pipeline(steps=[
    ('imputer', SimpleImputer(strategy='median')),
    ('scaler', StandardScaler())])

# piepline for categorical data, can also have a simple imputer
categorical_transformer = OneHotEncoder(handle_unknown='ignore')

# combine to make preprocessing pipeline
preprocessor = ColumnTransformer(
    transformers=[
        ('num', numeric_transformer, numeric_features),
        ('cat', categorical_transformer, categorical_features)])

# master pipeline includes preprocessing and classifier/regressor
pipe = Pipeline(steps=[('preprocessor', preprocessor),
                      ('classifier', LogisticRegression())]) 
```
## HTML representation of Pipeline
```python
from sklearn import set_config

set_config(display='diagram')
pipe
```
## Use ColumnTransformer by selecting column by data types
```python
from sklearn.compose import make_column_selector as selector

preprocessor = ColumnTransformer(transformers=[
    ('num', numeric_transformer, selector(dtype_exclude="category")),
    ('cat', categorical_transformer, selector(dtype_include="category"))
])
pipe = Pipeline(steps=[('preprocessor', preprocessor),
                      ('classifier', LogisticRegression())])
```
## Using the prediction pipeline in a grid search
Grid search can be performed on:
- the preprocessing steps defined in ColumnTransformer 
- the classifier ( or regressor) hyperparameters in the pipeline
- in each case the indexing is done with two underscores `__`
```python
param_grid = {
    'preprocessor__num__imputer__strategy': ['mean', 'median'],
    'classifier__C': [0.1, 1.0, 10, 100],
}

grid_search = GridSearchCV(clf, param_grid, cv=10)

grid_search.fit(X_train, y_train)

grid_search.best_params_
grid_search.best_score_
```