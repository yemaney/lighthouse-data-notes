# Regression and Error

### Generalization Error
- The generalization error is a `measure of how accurately` an algorithm is able to predict outcome values of data.
- To maximize accuracy is to minimize error
---

### Type of errors
- Approximation Error
    - if our `functions are to simple,` the accuracy of the model will be affected by `approximation error`
- Estimation Error
    - When we don't feed the model with `enough data`

- Optimization Error
    - To many observations or `Loss function is too complex` 
---
### Linear Regression
- optimized by `sum of squared errors`
- We are looking for a vector w which `minimizes our loss`. We know that we can do that by setting the `Gradient = 0`.
    - w = inv(X<sup>T</sup>X)X<sup>T</sup>y

---
### Statsmodels

```python
import statsmodels.api as sm

X = sm.add_constant(X) # adding a constant

lin_reg = sm.OLS(y,X)

model = lin_reg.fit()
print_model = model.summary()
print(print_model)
```
---
### Sklearn
```python
from sklearn.linear_model import LinearRegression

regressor = LinearRegression()

regressor.fit(X, y)

print(regressor.coef_)

regressor.score(X,y)

```
---
