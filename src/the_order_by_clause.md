# DQL - The ORDER BY clause

You use the ORDER BY clause to sort the rows in the output for presentation purposes. In terms of logical query processing, ORDER BY is the very last clause to be processed.

```sql
SELECT empid, YEAR(orderdate) AS orderyear, COUNT(*) AS numorders
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate)
HAVING COUNT(*) > 1
ORDER BY empid, orderyear;
```

You can specify *DESC* or *ASC* order

```sql
SELECT empid, YEAR(orderdate) AS orderyear, COUNT(*) AS numorders
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate)
HAVING COUNT(*) > 1
ORDER BY empid DESC, orderyear ASC;
```

```sql
SELECT empid, YEAR(orderdate) AS orderyear, COUNT(*) AS numorders
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate)
HAVING COUNT(*) > 1
ORDER BY empid, orderyear DESC;
```

It is possible to write ORDER BY with positioning arguments not column names:

```sql
SELECT empid, YEAR(orderdate) AS orderyear, COUNT(*) AS numorders
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate)
HAVING COUNT(*) > 1
ORDER BY 1, 2;
```