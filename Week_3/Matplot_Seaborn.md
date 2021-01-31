# Matplotlib

```python
import matplotlib.pyplot as plt

plt.plot(x,y,color='',linewidth='', label='') # line plot

plt.xlabel('')
plt.ylabel('')
plt.title('')
plt.tight_layout()

plt.show()
```
| Type      | Matplot name |
|-----------|--------------|
| Line      | plot()       |
| Histogram | hist()       |
| Bar       | bar()        |
| Pie       | pie()        |
| Scatter   | scatter()    |


- can `annotate` indiviidual points on graph

```python
ax.annotate('text', xy =(0,0), xytext = (0,0), arrowprops={'color':'red'})
```
---
### Subplots

- `figure` is the container that holds th eplots
- `axis` the actual plots

---

# Seaborn

```python 
import seaborn as sns

sns.<type of plot>(x='',y='', data = data)

plt.show()
```
| type                | seaborn name  |
|---------------------|---------------|
| regression          | lmplot        |
| residual            | residplot     |
| Boxplot             | boxplot       |
| Correlation Heatmap | heatmap(corr) |

- Seaborn plots can take extra arguements to enhance the visualization
    - `hue` to vary color based on a column data
    - `col` to  plot several graphs with respect to data in column  
