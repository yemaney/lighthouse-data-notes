


# Data Exploration
* Things to Check:
    * shape, type, 


* Duplicate check
    * ``check for dupes for Id
idsUnique = len(set(df_train.Id))
idsTotal = df_train.shape[0]
idsdupe = idsTotal - idsUnique
print(idsdupe)
#drop id col
df_train.drop(['Id'],axis =1,inplace=True)``


* Plot Histograms, `Numeric Data` Scatterplots to see pattern or outliers

* PLot Box plots for ``Categorical Data`

* Plot Correlation Matrix for MultiVarate Analysis

# Outliers
Detect with:
* Statisical tests
* Distance aproach
* Density approach
* Visual approach


# Null Vallues

* Check for missing values
    * ``total = df_train.isnull().sum().sort_values(ascending=False)
``
* Drop them with 
    * ``to_drop = missing_data.head(5).index.tolist()
df_train.drop(to_drop, axis=1, inplace=True)``

* fill with
    *``` df[cl] = df[cl].fillna(tuff)```

# Value Transformation
* Operation between columns to creat another column
* scale data with normalize, standardize
* log the data
* Reassign ordinal varriable to num, or nominal into similar bins with
    * ``df = df.column.replace {'old val': new val...}``

* Creat dummy var
    * ``cat_feats = df_train.dtypes[df_train.dtypes == 'object'].index.tolist()``   
    * ``df_dummy = pd.get_dummies(df_train[cat_feats])``

# Extra
* Use `.head()` for quick insight into data 