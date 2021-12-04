# The CAST, CONVERT, and PARSE functions and their TRY_ counterparts

* CAST(value AS datatype)
* TRY_CAST(value AS datatype)
* CONVERT (datatype, value [, style_number])
* TRY_CONVERT (datatype, value [, style_number])
* PARSE (value AS datatype [USING culture])
* TRY_PARSE (value AS datatype [USING culture])

```sql
SELECT CAST('20160212' AS DATE);
SELECT CONVERT(150, CHAR);
-- Silently fails
SELECT CAST('Banana' AS UNSIGNED INTEGER) AS 'CAST1';
SELECT CAST('0' AS UNSIGNED INTEGER) AS 'CAST2';
```
