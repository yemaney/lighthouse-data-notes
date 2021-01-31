# Plotly

```python
import plotly.graph_objs as go

data = go.<type>(
    x = data_x,
    y= data_y,
    mode=''
)

layout = go.Layout(
    title = '',
    xaxis = dict(title=''),
    yaxis= dict(title=''),
    hovermode = 'closest'
)

fig = go.Figure(data=data, layout=layout)

fig.show()
```

| type      | plotly name            |
|-----------|------------------------|
| Scatter   | Scatter                |
| Line      | Scatter (mode='lines') |
| Bar       | Bar                    |
| Histogram | Histogram              |


---
# Interactive Charts
```python
import  ipywidgets as widgets

from ipywidgets.widgets import interact, interact_manual

import plotly.graph_objs as go
```

### Slider
```python
slider = widgets.IntSlider(
    min=0,
    max=10,
    step=1,
    description='',
    value=5
)
```

### Filter DataFrame with widgets

```python
# filter function
def filter_df(column, threshold):
    return df[df[column] <= threshold>]


filter_widget = widgets.interact(filter_df, column=['a','b'],
threshold=[min, max, step])
```

### Interactive Plots with Widgets

```python
@interact_manual
def scatter_plot(x=[columns],
y=[columns]):

    trace = go.Scatter(x=df[x], y=df[y], mode='markers')

    layout = go.Layout (
        title = '',
        xaxis = dict(title = x.title()),
        yaxis = dict(title = y.title()),
        hovermode = 'closest'
    )

        fig = go.Figure(trace, layout)
        fig.show()
```