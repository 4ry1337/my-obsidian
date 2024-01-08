# Relational Database
A **relational database** is a [[Database]] based on the [[Relational Model]] of data, as proposed by E. F. Codd in 1970. A system used to maintain relational databases is a [[Relational Database Management System | relational database management system (RDBMS)]]. Many relational database systems are equipped with the option of using the [[Structured Query Language | SQL]] for querying and maintaining the database.

The relational database was first defined in June 1970 by Edgar Codd, of IBM's San Jose Research Laboratory. Codd's view of what qualifies as an RDBMS is summarized in [[Codd's 12 rules]].

## Relational Operations
- The *union operator (υ)* combines the tuples of two relations and removes all duplicate tuples from the result. 
- The *intersection operator (∩)* produces the set of tuples that two relations share in common.
- The *set difference operator (-)* acts on two relations and produces the set of tuples from the first relation that do not exist in the second relation.
- The *cartesian product (X)* of two relations is a join that is not restricted by any criteria, resulting in every tuple of the first relation being matched with every tuple of the second relation.

The remaining operators proposed by Codd involve special operations specific to relational databases:
- The *selection, or restriction, operation (σ)* retrieves tuples from a relation, limiting the results to only those that meet a specific criterion, i.e. a subset in terms of set theory. 
- The *projection operation* (π) extracts only the specified attributes from a tuple or set of tuples.
- The *join operation* defined for relational databases is often referred to as a natural join (⋈). In this type of join, two relations are connected by their common attributes.
- The *relational division (÷)* operation is a more complex operation and essentially involves using the tuples of one relation (the dividend) to partition a second relation (the divisor). The relational division operator is effectively the opposite of the cartesian product operator.