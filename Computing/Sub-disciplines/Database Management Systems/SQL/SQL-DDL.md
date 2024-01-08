# Data Definition Language (SQL)
The [[Data Definition Language]] (DDL) is the subset of [[Structured Query Language| SQL]] that manages table and index structure. The most basic items of DDL are the `CREATE`, `ALTER`, `RENAME`, `DROP` and `TRUNCATE` statements:

## `CREATE` creates an object in the database
``` SQL
CREATE DATABASE database_name;
CREATE TABLE example_name(
	column1 data_type(size),
	column2 data_type(size),
	column3 data_type(size),
	...
);
```

## `ALTER` modifies the structure of an existing object in various ways
``` SQL
ALTER TABLE table_name ADD(Columnname_1 datatype(size),
						   Columnname_2 datatype(size),
						   Columnname_3 datatype(size),
						   ...
						  );
```
ALTER TABLE - DROP is used to drop column in a table. Deleting the unwanted columns from the table:
```SQL
ALTER TABLE table_name DROP COLUMN Columnname_1,
						   Columnname_2,
						   Columnname_3,
						   ...
						  );
```

## `TRUNCATE` deletes all data from a table but not the table itself.
``` SQL
TRUNCATE TABLE table_name;
```

## `DROP` deletes an object in the database, usually irretrievably
``` SQL
DROP OBJECT object_name;
```

## `RENAME`
```SQL
ALTER TABLE table_name
RENAME TO new_table_name;

ALTER TABLE table_name
RENAME COLUMN old_column_name TO new_column_name;
```

## Additional
### `COMMENT` used to store comment about database object
	Only one comment string is stored for each object, so to modify a comment, issue new COMMENT operation for the same object
```SQL
COMMENT ON object object_name IS `some comment`;
```
# Constraints Clauses
Constraints are used to specify rules for the data in a table.

Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.

Constraints can be column level or table level. Column level constraints apply to a column, and table level constraints apply to the whole table.

The following constraints are commonly used in SQL:
-   `NOT NULL` - Ensures that a column cannot have a NULL value
-   `UNIQUE` - Ensures that all values in a column are different
-   `PRIMARY KEY` - A combination of a `NOT NULL` and `UNIQUE`. Uniquely identifies each row in a table
-   `FOREIGN KEY` - Prevents actions that would destroy links between tables
-   `CHECK` - Ensures that the values in a column satisfies a specific condition
-   `DEFAULT` - Sets a default value for a column if no value is specified
-   `CREATE INDEX` - Used to create and retrieve data from the database very quickly