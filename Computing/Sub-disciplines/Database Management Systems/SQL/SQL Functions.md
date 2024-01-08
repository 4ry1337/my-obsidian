# SQL Functions
[[Structured Query Language | SQL]] has many built-in functions for performing calculations on data.

## Aggregate Functions
[[Aggregate functions]] compute a single result from a set of input values.

A number of built-in aggregate functions exist:  
- COUNT,  
- SUM,  
- MAX,  
- MIN,  
- and AVG

**Grouping** is used to create subgroups of tuples before summarization.

In many cases we want to apply the aggregate functions to subgroups of tuples in a relation, where the subgroups are based on some attribute values. Each group (partition) will consist of the tuples that have the same value of some attribute(s), called the *grouping attribute(s)*. We can then apply the function to each such group independently to produce summary information about each group. SQL has a `GROUP BY` clause for this purpose.

The `GROUP BY` clause specifies the grouping attributes, which should also appear in the SELECT clause, so that the value resulting from applying each aggregate function to a group of tuples appears along with the value of the grouping attribute(s).


## Window Functions
In [[Structured Query Language | SQL]], a **window function** or **analytic function** is a function which uses values from one or multiple rows to return a value for each row. Window functions have an OVER clause; any function without an OVER clause is not a window function, but rather an aggregate or single-row (scalar) function.

The `PARTITION BY` clause groups rows into partitions, and the function is applied to each partition separately. If the `PARTITION BY` clause is omitted (such as if we have an empty `OVER()` clause), then the entire result set treated as a single partition.  Window functions are evaluated after aggregation.

![[Window Functions.png]]
