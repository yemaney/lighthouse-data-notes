# API

* API's are how computers or applications can comunicate with eacher
* Can be used to call data from source
---
### General workflow
* make relevant imports
```python 
import requests as re
from config import key, secret
import json
```
* organize url to use in request
```python
specfic = 'abc'
url = 'https://url'+specific
```
* use `re` to get data as repsonse
```python
res = re.get(url)
res.json()
```
* work with data
    - can use `url, timeout=n` to give timelimit on request
---