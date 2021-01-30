# Lambda Functions 
- an anonymous functions since it is defined without a name, but rather the keyword `lambda`

General form: `lambda arguements: expression`
- exmaple: 
```python
        double = lambda x: x * 2
        print(double(h))
```

- use when a short function is required,as an argument for a higher order function, used along with built-in-functions 
```python
map(lambda x: x * 2, list)
```
---
# List Comprehsion
```python
[i for i in x]

[i for i in x if y]

[i for i if y else j for i in x]
```
---
# Dictionary Comprehsion
```python
{key:val for vars in iterable}

{k:v for k,v in x if y}

{k: (a if y else b) for k,v in iterable}
```
---
# DateTime
- Import date time for everything to do woth dates or time

```python
from datetime import datetime
```

- String handling
        - strptime(): to turn strings into datetimeobjects
        - strftime(): turn datetime object into string
        - has to be formatted eg `( %m/%d/%Y)`
        - [strftime](https://strftime.org/)
- many things like .day, .weekday, .hour
---

