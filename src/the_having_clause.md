# DQL - The HAVING clause

Whereas the WHERE clause is a row filter, the HAVING clause is a group filter. Only groups for which the HAVING predicate evaluates to TRUE are returned by the HAVING phase to the next logical query processing phase. Groups for which the predicate evaluates to FALSE or NULL (UNKNOWN) are discarded.

```sql
SELECT empid, YEAR(orderdate) AS orderyear
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate)
HAVING COUNT(*) > 1;
```

```sql
SELECT empid, YEAR(orderdate) AS orderyear
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate)
HAVING empid in (6, 7);
```
