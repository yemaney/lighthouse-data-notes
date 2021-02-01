# Regularization and Bias


## Bias
- When the model `doesn't fit the training data` well, it has `high bias`
- When the model `doesn't fit the test data` well, it was `high variance`
- Ways to avoid bias
    1. Choose right learning model, unsupervised learning models can learn `bias from data`, while supervised learning can introudce `human bias`
    2. Choose  a diverse `representative training set` reflective of the real data
    3. Monitor performance using real data, look for equality of `outcome` and equality of `opportunity`

---
## Regularization

### Ridge Regression

- Goal is to find a new line that does't fit the training data to well, that is we want to `intoduce a small amount of bias` into how the new line is fit to the data, which will end up `lowering the variance`, for better predictions

---

| equation         | constraints                                         |
|------------------|-----------------------------------------------------|
| Least squares    | Min ( Sum of squared residuals                      |
| Ridge Regression | Min ( Sum of squared residuals + \lambda x slope2 ) | 

---
- \lambda as a penality
- An increase in \lambda, `reduces the sensitivity` of the line to variables, (reduces the slope)
- The ridge reggression penality `contains all of the parameters` except for the y-intercept
- `num of data points` should equal `num of paramaters`

---

### Lasso Regression

| equation      | constraints                                           |
|---------------|-------------------------------------------------------|
| Least squares | Min ( Sum of squared residuals )                        |
| Lasso         | Min ( Sum of squared residuals + \lambda x \|slope\| ) |

---

- similar to ridge regression
- `Lasso` regression can `reduce a slope to 0`, unlike ridge
- As `\lambda increases` terms with small slopes will go away was their wights go to zero
---
1. `Lasso Regression` is better at reducing the `Variance` in models that contain a lot of useless variables
2. `Ridge Regression` tends to do better when most varibales are useful

