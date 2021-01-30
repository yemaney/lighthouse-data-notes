# Collections

## Counter
- takes an iterable/ as arguement and returns a `dict` with element as `key`, and the num of times it appears as `val`
```python
from collections import Counter

cnt = Counter(iterable)
```
- elements(): return all elements 
```python
cnt.elements()
```
- most_common:  sort cnt according to num of counts in each elem
```python
cnt.most_common()
```
- subtract(): takes an list or dict as an arguement and deducts
```python
cnt.subtract(list/dic)
```
---
## Deque
- lsit optimized for inserting and removing items

```python
from collections import deque

deq = deque(list)
```
- appendleft()
- popleft()
- clear()
- count()
---
