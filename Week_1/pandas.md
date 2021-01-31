# Pandas

## Series
One dimensional lalbel array capable of holding many differnet data types
```python
s = pd.Series(data, idnex=index)
```
- index is  a list of axis labels

- data can be
    - list
    - dic
    - scaler values
- can slice and index like a numpy array
- has a dtype
    - ```python
        s.dtype
        s.to_numpy
      ```  
- can get and set values like a dic
    - ```python
        s['a']
        s['e'] = 21
        ```
- Vectorized operation like numpy arrays
- can have a name attribute
    - ```python
        s = pd.Series(data, name='something')
         ```
---
## DataFrame
Two dimensional labeled data structure with columns of potentially different data types. Like a table.

- Can be from a dict of Series or dicts
    - ```python
        d = {'a': pd.Series([1,2,3], index=['a','b','c']), 
                'b': pd.Series([1,2,3,4],index=['a','b','c','d'])}
        df= pd.DataFrame(d)    

        d= {'one':[1,2,3], 'two':[3,5,6]}
        df = pd.DataFrame(d)

        pd.DataFrame(pd.Series(np.random.randn(5), name='something'))
        ```
- column deletion
    - ```python
        del df['one']
        ```
- `dtypes`
    - dtype attribute returns a Series with datatypes of each column
        - ```python
            df.dtypes
           ```
    - Series has the same attribute
- `astype()` method explicitly convert dtypes, will return a copy, pass `copy=False` to change this
    - ```python
        df1 = df.astype('float64')
        ```
---
## Pandas basics

- [Series attributes](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html)
- [DataFrame attributes](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)

- `value_counts()` for series, returns histogram of values
- `describe()` gives basics statistical drescription of series
- `reindex()` changes the order of the index, and realigns data accordingly
    - can take the `axis` key word 
- `drop()` to remove a set of labels from an axis and the respective data
    - can take the `axis` keyword, `0=rows,1=columns`
- `rename()` to relabe an axis
    - ```python
        df.rename(columns={'a':'apple'}, index={'one':'first'})

        df.rename({'a':'apple'}, axis = 'columns')
        ```
- `.dt` accessor, return datetime-like properties of series 
    - ```python
        s.dt.hour
         ```
- `.str` to apply all tring funtcions 
    - ```python
        s.str.lower()
        ```
---
## Sorting
1. By index labels
    - `sort_index()`
    - `takes axis argument`

2. By column values
    - ```python
        df.sort_values(by='columns')
        
        s.sort_values(na_position='first')
         ```
    
3. By a combo of both
    - `MultiIndex`
    - ```python
         idx = pd.MultiIndex.from_tuples([('a', 1), ('a', 2), ('a', 2),('b', 2), ('b', 1), ('b', 1)])
    
        df_multi = pd.DataFrame({'A': np.arange(6, 0, -1)},
                            index=idx)
        ```
