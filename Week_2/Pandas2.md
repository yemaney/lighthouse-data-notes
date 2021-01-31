# Pandas

### Boolean Comparisons
- `eq ne lt gt le ge`
- `empty, any(), all(), bool()` to summarize a boolean result
---
### Object comparision
- convenient element wise comparison with scalar values and array objects of same length
```python
pd.Series([1,2,3]) == 2
pd.Series([1,2,3]) == pd.Index([1,2,2])
```
---
### Desciptive statistics 
- generally take axis as an arguement
- many mehtods available
- use `describe()` to get a simply stat summary
---
### Index of min/max 
- `indxmin()` and `idxmax`
---
### Iterations
- `items()` iterate over key,value pairs
- `iterrows`iter over rows of DF as idx,Series pairs
- `itertuples`iter over DF as namedtuples of the values, generally preferable than *iterrows*
---
### Filtering
| Operation                      | Syntax        | Result    |
|--------------------------------|---------------|-----------|
| Select Column                  | df[col]       | Series    |
| Select Row by label            | df.loc[label] | Series    |
| Select row by integer location | df.iloc[loc]  | Series    |
| Slice rows                     | df[5:10]      | DataFrame |
| Select rows by boolean vector  | df[bool_vec]  | DataFrame |


- df.iloc[`row,col`]
- `isin()` filter for values in the *()*

---
### Merge 

- Concatenating pandas objects with `concat()` 
- `.append()` to quickly add a coolumn
- `merge()` to join two data frames, equivalent to *JOIN* in SQL
```python
pd.merge(left, right, on='key')

pd.merge(left, right, on='key', how='outer')
```
---
### Grouping
- `.groupby(by='')`, followed by an aggregate function
- multi level index if a list is used an an arguement
---
# Reshaping

- `stack()` to compress the DataFrame, and creat a multi-level index
- `unstack()` does the reverse
- `.pivot_table()`

---
### Apply Functions
- tablewise `pipe()`
- row/col wise `apply()`
- can use custom funcitons as arguments for both