# The *OFFSET functions

## The DATE_ADD function

DATE_ADD(date, INTERVAL expr unit)

```sql
SELECT DATE_ADD('20160212', INTERVAL 1 YEAR);
```

## The DATEDIFF Functions

```sql
SELECT DATEDIFF('20150212', '20160212');
```

## The EXTRACT function

```sql
SELECT EXTRACT(MONTH FROM '20160212');
```

## The YEAR, MONTH, and DAY functions

YEAR(dt_val)
MONTH(dt_val)
DAY(dt_val)

```sql
SELECT
  DAY('20160212') AS theday,
  MONTH('20160212') AS themonth,
  YEAR('20160212') AS theyear;
```

## The DATENAME function

DATENAME(dt_val, part)

```sql
SELECT DATENAME(month, '20160212');
```

## The STR_TO_DATE function

STR_TO_DATE(string, format)

```sql
SELECT STR_TO_DATE('01,5,2013','%d,%m,%Y');
```

## The LAST_DAY function

LAST_DAY(input [, months_to_add])

```sql
SELECT orderid, orderdate, custid, empid
FROM Orders
WHERE orderdate = LAST_DAY(orderdate);
```