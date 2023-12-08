# [[Structured Query Language|SQL]] INDEXES
Indexes are **special lookup tables** that the database search engine can use to speed up data retrieval. Simply put, an index is a pointer to data in a table. 

An index helps to speed up `SELECT` queries and `WHERE` clauses, but it slows down data input, with the `UPDATE` and the `INSERT` statements. Indexes can be created or dropped with no effect on the data.

Creating an index involves the `CREATE INDEX` statement to specify the table and which column or columns to index, and to indicate whether the index is in an ascending or descending order.

Indexes can also be unique, like the `UNIQUE` constraint, in that the index prevents duplicate entries in the column or combination of columns on which there is an index.