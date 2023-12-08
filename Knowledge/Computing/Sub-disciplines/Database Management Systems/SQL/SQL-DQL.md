# Data Query Language (SQL)
**Data Query Language** (**DQL**) is part of the base grouping of [[Structured Query Language | SQL]] sub-languages.

DQL statements are used for performing queries on the data within schema objects. The purpose of DQL commands is to get the schema relation based on the query passed to it.

## `Select` retrieve or fetch data from database
^select

```SQL
SELECT Column1, COlumn2 FROM example_table; --specific columns

SELECT * FROM example_table; --entire table
```
- `Alias` allows to assign a column(s) and table(s) in the select list of a `SELECT` statement temporary name(s).
```SQL
SELECT column_name AS column_alias
FROM table_name AS table_alias;

SELECT column_name column_alias
FROM table_name table_alias; --can be executed without key words
```
