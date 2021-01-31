# Dimensionality Reduction
- To `avoid overfitting` when many feautures are available in data
- To make `Visualization` possible by reducing dimensions into 2-3 components
- `Reduction` of time and space complexity
- Increase interpretability by `reducing noise`
- `Feature extraction` by plotting `PCA space`

---

## PCA
- coordinate system to describe data is arbitrary, so we can change them
- PCA is the idea of remapping the data to the dimensions that describe the most amount of variance

### Basic work flow
```python
from sklearn.decomposition import PCA

from sklearn.preprocessing import StandardScaler


x = StandardScaler().fit_transform(x)

pca = PCA()

components = pca.fit(n_components=3)

pca.fit(data)

pca.components_

```
---

### PCA Space
```python
import matplotlib.pyplot as plt
%matplotlib inline

fig = plt.figure()
ax = fig.add_subplot(111)
plt.scatter(pca.components_[0], pca.components_[1])
plt.xlim(-1,1)
plt.ylim(-1,1)

ind = 0
for i,j in zip(pca.components_[0],
               pca.components_[1]):
    ax.annotate(weather_feats[ind], xy=(i,j), xytext=(8,0), textcoords='offset points')
    ind += 1
plt.show()
```
---
### Cumulative Explained Variance

```Python
python
from sklearn.decomposition import PCA

from sklearn.preprocessing import StandardScaler


x = StandardScaler().fit_transform(x)

pca = PCA()
pca.fit(x)

cum_var_explained = np.cumsum(pca.explained_variance_ratio_)


import plotly.express as px
%matplotlib inline

px.area(
    x=range(1, exp_var_cumul.shape[0] + 1),
    y=exp_var_cumul,
    labels={"x": "# Components", "y": "Explained Variance"}
)
```
---

### Forward Regression: Select K best features

```python
from sklearn.feature_selection import f_regression, SelectKBest

skb = SelectKBest(f_regression, k=10)

X = skb.fit_transform(df_transformed, y)

selected_columns = df_transformed.columns[skb.get_support()]

df_transformed = pd.DataFrame(X, columns = selected_columns)
```
---
### Variance filter function

```python
def var_filt(df, x):
    from sklarn.feature_selection import VarianceThreshold
    vt = VarianceThreshold(x)
    df_var_fil = vt.fit_transform(dd)
    return df_var_fil
```
---
### Missing values % filter function
```python
def missing_filt(df, pct):
    total = df_train.isnull().sum().sort_values(ascending=False)
    percent = (df_train.isnull().sum()/df_train.isnull().count()).sort_values(ascending=False)
    missing_data = pd.concat([total, percent], axis=1, keys=['Total', 'Percent'])
    x = missing_data[(missing_data.Percent).lt(0.8)]
    
    df_miss_fil = df[x.index]
    
    return df_missing_fil
```
---
### Correlated feature filter function

```python
def corr_fil(df, corr):
    # step 1
    df_corr = df_transformed.corr().abs()

    # step 2
    indices = np.where(df_corr > corr) 
    indices = [(df_corr.index[x], df_corr.columns[y]) for x, y in zip(*indices)
                                    if x != y and x < y]

    # step 3
    for idx in indices: #each pair
        try:
            df_transformed.drop(idx[1], axis = 1, inplace=True)
        except KeyError:
            pass
```