# NULL examples

```sql
SELECT custid, country, region, city
FROM Customers
WHERE region = NULL; -- will return empty
```

```sql
SELECT custid, country, region, city
FROM Customers
WHERE region IS NULL; -- will return 60 rows
```

If you want to get region that are not null

```sql
SELECT custid, country, region, city
FROM Customers
WHERE region IS NOT NULL; -- will return 31 rows
```
