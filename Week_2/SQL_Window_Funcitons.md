# SQL Windows Functions

- Aggregate 
    - `COUNT    `
    - `SUM`
    - `AVG`
    - `MIN`
    - `MAX`
- Value
    - `FIRST_VALUE`
    - `LAST_VALUE`
    - `LEAD`
    - `LAG`
- Ranking
    - `PERCCENT_RANK`
    - `CUME_DIST`
    - `PERCENTILE_CONT`

- Frames
    - `Rows`
    - `Range`
---

Can get `aggregate functions values` into a column of their own.
- use `OVER ()` clause to identify how new row will be organized


`SELECT a,b, AGGFUN(C)
OVER (ORDER BY a ...) as new_name
FROM table ` 

```SQL
SELECT 
    month,
    amount,
    AVG(amount) OVER (
        ORDER BY month
        ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING
    ) SalesMovingAverage
FROM
    SalesInfo;
```