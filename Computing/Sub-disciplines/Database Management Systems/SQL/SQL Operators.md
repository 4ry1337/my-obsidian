| Operator                              | Description                                                                                            |
|:------------------------------------- |:------------------------------------------------------------------------------------------------------ |
| `=`                                   | Equal to                                                                                               |
| `<>` *or* `!=`                        | Not equal to                                                                                           |
| `>`                                   | Greater than                                                                                           |
| `<`                                   | Less than                                                                                              |
| `>=`                                  | Greater than or equal                                                                                  |
| `<=`                                  | Less than or equal                                                                                     |
| `[NOT] Between [SYMMETRIC]`           | Between an inclusive range. SYMMETRIC inverts the range bounds if the first is higher than the second. |
| `[NOT] LIKE [ESCAPE]`                 | Begins with character pattern / Contains a character pattern                                           |
| `[NOT] IN`                            | Equal to one of multiple possible values                                                               |
| `IS [NOT] NULL`                       | Compare to null (missing data)                                                                         |
| `IS [NOT] TRUE` *or* `IS [NOT] FALSE` | Boolean truth value test                                                                               |
| `IS NOT DISTINCT FROM`                | Is equal to value or both are nulls (missing data)                                                     |
| `AS`                                  | Used to change a column name when viewing results                                                      |

## `EXISTS`
The `EXISTS` operator is used to test for the existence of any record in a [[Structured Query Language#^Subquery | subquery]].

```SQL
SELECT column_name(s)
FROM table_name
WHERE EXISTS (SELECT column_name FROM table_name WHERE condition);
```

## `ANY` and `ALL`
### `ANY`
The `ANY` operator:
- returns a boolean value as a result
- returns TRUE if ANY of the subquery values meet the condition
```SQL
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY (SELECT column_name  FROM table_name  WHERE condition);
```
**Note:** The _operator_ must be a standard comparison operator (=, <>, !=, >, >=, <, or <=).
### `ALL`
The `ALL` operator:
- returns a boolean value as a result
- returns TRUE if ALL of the subquery values meet the condition
- is used with `SELECT`, `WHERE` and `HAVING` statements

# `UNION`, `INTERSECT` and `EXCEPT`
## `UNION`
The `UNION` operator is used to combine the result-set of two or more `SELECT` statements.
- Every `SELECT` statement within `UNION` must have the same number of columns
- The columns must also have similar data types
- The columns in every `SELECT` statement must also be in the same order

The basic syntax of a **UNION** clause is as follows −
```sql
SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]

UNION

SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]
```

## `UNION ALL`
The `UNION ALL` operator is used to combine the results of two SELECT statements including duplicate rows.

The same rules that apply to the UNION clause will apply to the UNION ALL operator.

The basic syntax of the **UNION ALL** is as follows.
```sql
SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]

UNION ALL

SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]
```

## `INTERSECT`
The `INTERSECT` clause/operator is used to combine two SELECT statements, but returns rows only from the first SELECT statement that are identical to a row in the second SELECT statement.

The basic syntax of **INTERSECT** is as follows.
```sql
SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]

INTERSECT

SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]
```

## `EXCEPT`
The **EXCEPT** clause/operator is used to combine two SELECT statements and returns rows from the first SELECT statement that are not returned by the second SELECT statement.

The basic syntax of **EXCEPT** is as follows.
```sql
SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]

EXCEPT

SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]
```
