# Working with characters

* For string concatenation, MySQL provides the *CONCAT* function. MSSQL provides + operatos as well. There are possibility to set up pipe operator || in MySQL:

```sql
SET SESSION sql_mode='PIPES_AS_CONCAT';
```

* For other operations on character strings, T-SQL provides several functions, including *SUBSTRING, LEFT, RIGHT, LEN, LENGTH, CHARINDEX, REPLACE, REPEAT, UPPER, LOWER, RTRIM, LTRIM, FORMAT, and more*.

```sql
SET SESSION sql_mode='PIPES_AS_CONCAT';

SELECT empid, firstname ||  N' ' || lastname AS fullname
FROM Employees;

SELECT custid, country, region, city,
  CONCAT(country, ', ', region, ', ',  city) AS location
FROM Customers;

SELECT custid, country, region, city,
  CONCAT_WS(', ', country, region, city) AS location
FROM Customers;

SELECT custid, country, region, city,
  COALESCE(region, '') AS region_empty_string
FROM Customers;

-- CONCAT also removes NULL and replace with empty char
```

SUBSTRING(string, start, length)

```sql
SELECT SUBSTRING('abcde', 1, 3);
```

LEFT(string, n), RIGHT(string, n)

```sql
SELECT RIGHT('abcde', 3);
```

LENGTH(string)

```sql
SELECT LENGTH(N'abcde');
```

POSITION(substr IN str)

```sql
SELECT POSTION(' ' IN 'Itzik Ben-Gan');
```

REPLACE(string, substring1, substring2)

```sql
SELECT REPLACE('1-a 2-b', '-', ':');
```
REPEAT(str,count)

```sql
SELECT REPEAT('MariaDB ', 4);
```

UPPER(string), LOWER(string)

```sql
SELECT UPPER('Itzik Ben-Gan');
SELECT LOWER('Itzik Ben-Gan');
```

RTRIM(string), LTRIM(string)

```sql
SELECT RTRIM(LTRIM('   abc   '));
```

FORMAT(num, decimal_position[, locale])

```sql
SELECT FORMAT(123456789,2,'lt_LT') AS 'Format';
```

IIF(string or null, replace)

```sql
SELECT IFNULL(NULL, 'z');
```

Wildcarts

* The % wildcart - LIKE 'somestring%'
* The _ (underscore) wildcard

```sql
SELECT empid, lastname
FROM Employees
WHERE lastname LIKE '_e%';
```

* The [<list of characters>] wildcard

```sql
SELECT empid, lastname
FROM Employees
WHERE lastname REGEXP '[ABC]';
```

* The `[<character>-<character>]` wildcard

```sql
SELECT empid, lastname
FROM Employees
WHERE lastname REGEXP '[A-E]';
```

* The `[^<character list or range>]` wildcard (^ not in char list)

```sql
SELECT empid, lastname
FROM Employees
WHERE lastname REGEXP '[^A-E]';
```

In MySQL you can escape characters in LIKE expression:

```sql
SELECT empid, lastname
FROM Employees
WHERE lastname LIKE '\_e%';
```

```sql
SELECT empid, lastname
FROM Employees
WHERE lastname LIKE '!_e%' ESCAPE '!';
```
