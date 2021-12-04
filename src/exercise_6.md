# Exercise 6

Explain the difference between the following two queries:

```sql
-- Query 1
SELECT empid, COUNT(*) AS numorders
FROM Orders
WHERE orderdate < '20160501'
GROUP BY empid;

-- Query 2
SELECT empid, COUNT(*) AS numorders
FROM Orders
GROUP BY empid
HAVING MAX(orderdate) < '20160501';
```

Tables involved: *lessons* database and the *Orders* table