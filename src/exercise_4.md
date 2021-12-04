# Exercise 4

Write a query against the *OrderDetails* table that returns orders (grouped) with a total value (sum of) `quantity * unitprice` greater than 10 000 and sorted by total value:

* Tables involved: *lessons* database and the *OrderDetails* table
* Desired output:

```
orderid     totalvalue
----------- ---------------------
10865       17250.00
11030       16321.90
10981       15810.00
10372       12281.20
10424       11493.20
10817       11490.70
10889       11380.00
10417       11283.20
10897       10835.24
10353       10741.60
10515       10588.50
10479       10495.60
10540       10191.70
10691       10164.80

(14 row(s) affected)
```