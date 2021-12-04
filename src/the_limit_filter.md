# DQL - The LIMIT filter

The LIMIT filter is a proprietary MySQL feature you can use to limit the number of rows your query returns. It relies on two elements as part of its specification: one is the number or percent of rows to return, and the other is the ordering.

```sql
SELECT orderid, orderdate, custid, empid
FROM Orders
ORDER BY orderid DESC LIMIT 10;

SELECT orderid, orderdate, custid, empid
FROM Orders
ORDER BY orderid DESC LIMIT 5, 2;
```

Note: *ORDER BY* clause is evaluated after the *SELECT* clause, which includes the *DISTINCT* option. The same is true with the *LIMIT* filter, which relies on the *ORDER BY* specification to give it its filtering-related meaning. This means that if *DISTINCT* is specified in the *SELECT* clause, the *LIMIT* filter is evaluated after duplicate rows have been removed.
