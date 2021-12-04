# DQL - Group by clause and aggregation functions

The *GROUP BY* clause - You can use the *GROUP BY* phase to arrange the rows returned by the previous logical query processing phase in groups. The groups are determined by the elements you specify in the *GROUP BY* clause. For example, the *GROUP BY* clause in the query in Listing 2-1 has the elements *empid* and *YEAR(orderdate)*:

```sql
SELECT empid, YEAR(orderdate) FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate);
```

We can use variable alias `AS` to make alias for table column name:

```sql
SELECT empid, YEAR(orderdate) AS orderyear FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate);
```

The result is a number of goups of orders by year and employe id. It doesn't mean that we had 16 orders.

Let's use aggregation function *COUNT* to see how many orders was done in created groups by employe id and order year.

An aggregate function performs a calculation on multiple values and returns a single value:
* AVG - takes multiple numbers and returns the average value of the numbers,
* SUM - returns the summation of all values,
* MAX - returns the highest value,
* MIN - returns the lowest value,
* COUNT - returns the number of rows.

```sql
SELECT
  empid,
  YEAR(orderdate) AS orderyear,
  COUNT(*) AS numorders
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate);
```

Let's figure out total freigt for every group as well :)

```sql
SELECT
  empid,
  YEAR(orderdate) AS orderyear,
  SUM(freight) AS totalfreight,
  COUNT(*) AS numorders
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate);
```

If you try to refer to an attribute that does not participate in the GROUP BY clause (such as freight) and not as an input to an aggregate function in any clause that is processed after the GROUP BY clause, you get an error (this is only true for T-SQL, PLSQL, but not for MySQL :D)

```sql
SELECT empid, YEAR(orderdate) AS orderyear, freight
FROM Orders
WHERE custid = 71
GROUP BY empid, YEAR(orderdate);
```

Note that all aggregate functions ignore NULLs, with one exception — `COUNT(*)`. For example, consider a group of five rows with the values 30, 10, NULL, 10, 10 in a column called qty. The expression `COUNT(*)` returns 5 because there are five rows in the group, whereas COUNT(qty) returns 4 because there are four known values

```sql
CREATE TABLE t1(
    num INT
);

INSERT INTO t1 VALUES (1), (2), (NULL), (3);

SELECT COUNT(*) FROM t1;
SELECT COUNT(num) FROM t1;

DROP TABLE t1;
```

You can use DISTINCT to find unique values:

```sql
SELECT
    empid,
    YEAR(orderdate) AS orderyear,
    COUNT(custid) AS numcusts
FROM Orders
GROUP BY empid, YEAR(orderdate);
```

---

```sql
SELECT
    empid,
    YEAR(orderdate) AS orderyear,
    COUNT(DISTINCT custid) AS numcusts
FROM Orders
GROUP BY empid, YEAR(orderdate);
```

Let's analyse such example:

```sql
CREATE TABLE mytable (
        id INT UNSIGNED NOT NULL PRIMARY KEY,
        a VARCHAR(10),
        b INT
    );

INSERT INTO mytable
    VALUES (1, 'abc', 1000),
          (2, 'abc', 2000),
          (3, 'def', 4000);

SELECT a, SUM(b) FROM mytable WHERE a = 'abc';
SELECT a, SUM(b) FROM mytable GROUP BY a;
-- WTH ???
SELECT a, SUM(b) FROM mytable;
```

# GROUP BY with rollup

```sql
SELECT SUM(freight), YEAR(orderdate) FROM Orders group by YEAR(orderdate);

SELECT SUM(freight), YEAR(orderdate) FROM Orders group by YEAR(orderdate) WITH ROLLUP;
```

The *WITH ROLLUP* modifier adds extra rows to the resultset that represent super-aggregate summaries. The super-aggregated column is represented by a *NULL* value. Multiple aggregates over different columns will be added if there are multiple *GROUP BY* columns.
