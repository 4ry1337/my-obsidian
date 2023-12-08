# Data Manipulation Language (SQL)
The [[Data Manipulation Language]] (DML) is the subset of [[Structured Query Language | SQL]] used to add, update and delete data:

## `INSERT` insert rows into a table:
``` SQL
INSERT INTO example VALUES (Value1, Value2, Value3, ...); --value1 will be inserted into column1, and etc.

INSERT INTO example (Column1, Column2, Column3, ...)
VALUES (Value1, Value2, Value3, ...); --specifies both column and value

--insert multiple rows
INSERT INTO example (Column1, Column2, Column3, ...)
VALUES (Value1, Value2, Value3, ...),
	   (Value1, Value2, Value3, ...),
	   (Value1, Value2, Value3, ...),
	   ...;

--select can be used to insert data from one table to another
INSERT INTO first_table SELECT * FROM second_table;
INSERT INTO first_table(Column1, Column2, ...)
SELECT * FROM second_table
WHERE some_condition;
```

## `UPDATE` update existing data in table
^update

``` SQL
UPDATE example
SET column1 = value1, column2 = value2, ...
WHERE some_condition;
```

## `DELETE` delete rows from a database table
^delete

``` SQL
DELETE FROM table_example
WHERE sone_condition; --delete specific records

DELETE FROM table_example; --delete all records
```

> ==Update later==`MERGE`  is used to combine the data of multiple tables. It combines the `INSERT` and `UPDATE` elements. It is defined in the SQL:2003 standard; prior to that, some databases provided similar functionality via different syntax, sometimes called "upsert".
``` SQL
MERGE INTO table_name USING table_reference ON (condition)
WHEN MATCHED THEN
UPDATE SET column1 = value1 [, column2 = value2 ...]
WHEN NOT MATCHED THEN
INSERT (column1 [, column2 ...]) VALUES (value1 [, value2 ...])
```
