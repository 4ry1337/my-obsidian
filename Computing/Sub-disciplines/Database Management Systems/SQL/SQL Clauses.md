# [[Structured Query Language | SQL]] Clauses
## `FROM` 
A `FROM` clause is a mandatory part of a [[SQL-DQL#^select | Select]] that specifies table from which other clauses of the query can access columns for use in expression

## `WHERE`
A `WHERE` clause is an optional part of a [[SQL-DQL#^select | Select]], [[SQL-DML#^delete| DELETE statement]], or [[SQL-DML#^update| UPDATE statement]]. The WHERE clause lets you select rows based on a boolean expression (condition).

## `GROUP BY`
A `GROUP BY` clause, part of [[SQL-DQL#^select | Select]], groups a result into subsets that have matching values for one or more columns. In each group, no two rows have the same value for the grouping column or columns. NULLs are considered equivalent for grouping purposes.
```SQL
GROUP BY column_name;
```

### `GROUPING SETS`
The `GROUPING SETS` allows to define multiple grouping sets in the same query. The `GROUPING SETS` clause is the subclause of the `GROUP BY` clause.

The general syntax of the `GROUPING SETS` is as follows:

```SQL
SELECT
    aggregate_function(column_1)
    column_2,
    column_3,
FROM table_name
GROUP BY
    GROUPING SETS (
	    (column_2, column_3),
	    (column_2),
        (column_3),
        ()
);
```
### `CUBE`
`CUBE` is an extension of the `GROUP BY` clause. It allows to generate subtotals for all combinations of the grouping columns specified in the `GROUP BY` clause.
```sql
SELECT c1, c2, c3, aggregate(c4)
FROM t1
GROUP BY CUBE (c1, c2, c3);
```
same as
```sql
GROUPING SET(
	(c1, c2, c3),
	(c1, c2),
	(c1, c3),
	(c2, c3),
	(c1),
	(c2),
	(c3),
	()
);
```
### `ROLLUP`
The `ROLLUP` option in a single query to generate multiple grouping sets. `ROLLUP` assumes a hierarchy among the input columns.
```sql
GROUP BY ROLLUP(c1, c2, c3)
```
the hierarchy for this is `c1 > c2 > c3`, and `ROLLUP` generates the following grouping sets:
```sql
GROUPING SET (
	(c1, c2, c3),
	(c1, c2),
	(c1),
	(),
);
```

### `HAVING`
A `HAVING` clause restricts the result of a `GROUP BY` in a [[SQL-DQL#^select | Select Statement]]. 
```SQL
GROUP BY column_1
HAVING some_condition;
```

## `ORDER BY`
A `ORDER BY` clause is optional part of [[SQL-DQL#^select | Select Statement]] returns a result set with the rows being sorted by the values of one or more columns.
```SQL
ORDER BY column_1
```

- `ASC | DESC` specifies either ascending or descending order sort the data
```SQL
ORDER BY column_1 ASC | DESC;
```
By default, sort is ascending.
- `NULL FIRST | NULL LAST`
```SQL
ORDER BY column_1 NULL FIRST | NULL LAST;
```
By default, null values are last.

## `DISTINCT`
A `DISTINCT` clause is optional part of [[SQL-DQL#^select | Select Statement]], used to retrieve only distinct or unique data.
```SQL
SELECT DISTINCT * FROM table_example;
```

## `LIMIT`
A `LIMIT` clause is optional part of [[SQL-DQL#^select | Select Statement]] that constraints the number of records returned be the query.
```SQL
SELECT * FROM table_example
LIMIT row_count;
```
- if `row_count` is 0, returns empty
- if `row_count` is NULL, returns same result as without `LIMIT` clause

### `OFFSET`
`OFFSET` clause skips a number of records
```SQL
SELECT *
FROM table_example
LIMIT row_count OFFSET rows_to_skip;
```

## `JOINS`
A `JOIN` clause is used to combine rows from two or more tables, based on a related column between them.

### `INNER JOIN`
An `INNER JOIN` keyword selects all rows from both tables as long as there is a match between the columns in both tables.
```SQl
SELECT column_name(s)
FROM table1
JOIN table2 --In some databases `JOIN` is called `INNER JOIN`.
ON table1.column_name = table2.column_name
WHERE condition;
```  
![SQL INNER JOIN](https://www.w3schools.com/sql/img_innerjoin.gif)

### `LEFT JOIN`
A `LEFT JOIN` keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.
```SQL
SELECT column_name(s)
FROM table1
LEFT JOIN table2 --In some databases `LEFT JOIN` is called `LEFT OUTER JOIN`.
ON table1.column_name = table2.column_name
WHERE condition;
```
![SQL LEFT JOIN](https://www.w3schools.com/sql/img_leftjoin.gif)

### `RIGHT JOIN`
A `RIGHT JOIN`  keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.
```SQL
SELECT column_name(s)
FROM table1
RIGHT JOIN table2 --In some databases `RIGHT JOIN` is called `RIGHT OUTER JOIN`.
ON table1.column_name = table2.column_name
WHERE condition;
```
![SQL RIGHT JOIN](https://www.w3schools.com/sql/img_rightjoin.gif)

### `FULL JOIN`
A `FULL JOIN` keyword returns all records when there is a match in left (table1) or right (table2) table records.
```SQL
SELECT column_name(s)
FROM table1
FULL JOIN table2 --In some databases `RIGHT JOIN` is called `RIGHT OUTER JOIN`.
ON table1.column_name = table2.column_name
WHERE condition;
```
![SQL FULL OUTER JOIN](https://www.w3schools.com/sql/img_fulljoin.gif)

### `CROSS JOIN`
A `CROSS JOIN` keyword returns a Cartesian Product of rows in two or more tables
```SQL
SELECT column_name(s)
FROM table1 CROSS JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

### `NATURAL JOIN`
A `NATURAL JOIN` keyword returns an implicit join by combining tables based on columns with the same name and data type.
```SQL
SELECT column_name(s)
FROM table1 CROSS NATURAL JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

### `SELF JOIN`
A self join is a regular join, but the table is joined with itself.	
```SQL
SELECT column_name(s)  
FROM table1 T1 JOIN table1 T2
WHERE condition;
```