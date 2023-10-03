# Mysql code snippets


#### 1. Find duplicate values in one column:
---
The find duplicate values in on one column of a table, you use follow these steps:

1. First, use the `GROUP BY` clause to group all rows by the target column, which is the column that you want to check duplicate.
2. Then, use the `COUNT()` function in the `HAVING` clause to check if any group have more than 1 element. These groups are duplicate.

The following query illustrates the idea:

```sql
SELECT col, COUNT(col) FROM table_name GROUP BY col HAVING COUNT(col) > 1;
```

By using this query template, you can to find rows that have duplicate emails in the `contacts` table as follows:
*Example:-*
-------------
```sql
SELECT email, COUNT(email) FROM contacts GROUP BY email HAVING COUNT(email) > 1;
```
