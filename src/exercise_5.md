# Exercise 5

To check the validity of the data, write a query against the *Employees* table that returns employees with a last name that starts with a lowercase English letter in the range a through z.

Note: You can use `REGEXP` with `BINARY`, e.g. REGEXP BINARY. Database is case insensitive that's why you need to use REGEXP BINARY.

* Tables involved: *lessons* database and the *Employees* table
* Desired output is an empty set:

```
empid       lastname
----------- --------------------

(0 row(s) affected))
```