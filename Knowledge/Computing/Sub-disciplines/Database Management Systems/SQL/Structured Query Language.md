# Structured Query Language
**SQL** or **Structured Query Language** is a [[Domain-Specific Language]] used in programming and designed for managing data held in a [[Database Management Systems#^RDBMS | relational database management system]]. It is particularly useful in handling [[structured data]], i.e. data incorporating relations among entities and variables.

> ==Edit==
SQL offers two main advantages over older read–write [[APIs]] such as [[ISAM]] or [[VSAM]]. Firstly, it introduced the concept of accessing many records with one single command. Secondly, it eliminates the need to specify _how_ to reach a record, e.g. with or without an [index](https://en.wikipedia.org/wiki/Database_index "Database index").

Originally based upon relational algebra and tuple relational calculus, SQL consists of many types of statements, which may be informally classed as sublanguages:
- [[Data Query Lnguage]] (DQL)
- [[Data Definition Language]] (DDL)
- [[Data Control Language]] (DCL)
- [[Data Manipulation Language]] (DML)

## Syntax
### Language elements
The SQL language is subdivided into several language elements, including:
- *Keywords* are words that are defined in the SQL language. They are either reserved (e.g. `SELECT`, `COUNT` and `YEAR`), or non-reserved (e.g. `ASC`, `DOMAIN` and `KEY`). List of [[SQL reserved words]].
- *Identifiers* are names on database objects, like tables, columns and schemas. An identifier may not be equal to a reserved keyword, unless it is a delimited identifier. Delimited identifiers means identifiers enclosed in double quotation marks. They can contain characters normally not supported in SQL identifiers, and they can be identical to a reserved word, e.g. a column named `YEAR` is specified as `"YEAR"`.
- *[[SQL Clauses| Clauses]]*, which are constituent components of statements and queries. (In some cases, these are optional.)
- *[[SQL Expressions | Expressions]]*, which can produce either scalar values, or tables consisting of columns and rows of data.
- *Predicates*, which specify conditions that can be evaluated to SQL [[three-valued logic (3VL)]] (true/false/unknown) or [[Boolean]] truth values and are used to limit the effects of statements and queries, or to change program flow.
- *Queries*, which retrieve the data based on specific criteria. This is an important element of *SQL*.
- *Statements*, which may have a persistent effect on schemata and data, or may control transactions, program flow, connections, sessions, or diagnostics.
    -   SQL statements also include the semicolon (";") statement terminator. Though not required on every platform, it is defined as a standard part of the SQL grammar.
- *Insignificant whitespace* is generally ignored in SQL statements and queries, making it easier to format SQL code for readability.


### [[SQL Operators | Operators]]
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

### Comments
Standard SQL allows two formats for comments: `-- comment`, which is ended by the first newline, and `/* comment */`, which can span multiple lines.

### Queries
A query in a database is **a request for information from a database management system** (DBMS), which is the software program that maintains data.

#### Subqueries

^Subquery

Queries can be nested so that the results of one query can be used in another query via a [[relational operator]] or aggregation function. A 
nested query is also known as a _subquery_. While joins and other table operations provide computationally superior (i.e. faster) alternatives in many cases, the use of subqueries introduces a hierarchy in execution that can be useful or necessary.

#### Derived table
A *derived table* is the use of referencing an SQL subquery in a FROM clause. Essentially, the derived table is a subquery that can be selected from or joined to. The derived table functionality allows the user to reference the subquery as a table. The inline view is also referred to as an *inline view* or a *subselect*.

## Data types
The SQL standard defines three kinds of [[Data Type | data types]]
-   predefined data types
-   constructed types
-   user-defined types.

*Constructed types* are one of ARRAY, MULTISET, REF(erence), or ROW.
*User-defined types* are comparable to classes in object-oriented language with their own constructors, observers, mutators, methods, inheritance, overloading, overwriting, interfaces, and so on. 

Predefined data types:
- Character types
	- Character(n) (or `CHAR(n)`): fixed-width n-character string, padded with spaces as needed.
	- Character varying(n) (or `VARCHAR(n)`): variable-width string with a maximum size of n characters.
	- Character large object(n \[ K | M | G | T\]) (or `CLOB(n \[ K | M | G | T\])`): character large object with a maximum size of n \[ K | M | G | T\] characters.
- National character types
	- National character(n) (or `NCHAR(n)`): fixed width string supporting an international character set.
	- National character varying(n) (or `NCHAR VARYING(n)`): variable-width `NCHAR` string
	- National character large object(n \[ K | M | G | T\]) (or `NCLOB(n \[ K | M | G | T\])`): national character large object with a maximum size of n \[ K | M | G | T \] characters
- Binary types
	- Binary(n) (or `BINARY(n)`): Fixed length binary string, maximum length n.
	- Binary varying(n) (or `VARBINARY(n)`): Variable length binary string, maximum length n.
	- Binary large object(n \[ K | M | G | T \]) (or `BLOB(n \[ K | M | G | T \])`): binary large object with a maximum length n \[ K | M | G | T \].
- Boolean (or `BOOLEAN`) data type can store the values `TRUE` and `FALSE`.
- Numeric types
	- Exact numeric types
		- NUMERIC 
		- DECIMAL
		- SMALLINT
		- INTEGER
		- BIGINT)
	- Approximate numeric types
		- FLOAT
		- REAL
		- DOUBLE PRECISION
	- Decimal floating-point type (DECFLOAT)
- Datetime types (DATE, TIME, TIMESTAMP)
- Interval type (INTERVAL)
- XML
- JSON