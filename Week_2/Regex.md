# Regex

```python
import re

regex = r"pattern"

with open(filename, encodeing='') as f:
    lines = f.readlines()

for line in lines:
    match = re.findall(regex, line)
    if match:
        print(line)
```

---
### Simple Regex Cheatsheet

| pattern| output                     |   | pattern    | Output                         |
|--------|----------------------------|---|------------|--------------------------------|
| abc... | Letters                    |   | 123...     | Digits                         |
| \d     | Any Digit                  |   | \D         | Any non-digit                  |
| .      | Any character              |   | \.         | period                         |
| [abc]  | only a or b or c           |   | [^abc]     | Not a,b, nor c                 |
| [a-z]  | characters a  to z         |   | 0-9        | Numbers 0 to 9                 |
| \w     | Any alphanumeric character |   | \W         | Any non-alphanumeric character |
| {m}    | m Repetitions              |   | {m,n}      | m to n Repetitions             |
| *      | Zero or more repetitions   |   | +          | One or more Repetitions        |
| ?      | Optional character         |   | \s         | Any whitespace                 |
| \S     | Any non-white space        |   | ^...$      | Starts and ends                |
| (...)  | Capture group              |   | (a(bc))    | Capture subgroup               |
| (.*)   | Capture all                |   | (abc\|def) | Match abc or def               |
|        |                            |   |            |                                |
|        |                            |   |            |                                |


---