# Relational Model
The **relational model** (**RM**) is an approach to managing [[Data Type]] using a structure and language consistent with first-order predicate logic, first described in 1969 by English computer scientist Edgar F. Codd where all data is represented in terms one or more tables of columns and rows, with a unique key identifying each row.
- Rows are also called *records* or *tuples*.
- Columns are also called *attributes*.
A database organized in terms of the relational model is a [[Relational Database]].

## Concepts
**Tables** − relations are saved in the format of Tables. This format stores the relation among entities. A table has rows and columns, where rows represents records and columns represent the attributes.
**Tuple** − A single row of a table, which contains a single record for that relation is called a tuple.
**Relation instance** − A finite set of tuples in the relational database system represents relation instance. Relation instances do not have duplicate tuples.
**Relation schema** − A relation schema describes the relation name (table name), attributes, and their names.
**Relation key** − Each row has one or more attributes, known as relation key, which can identify the row in the relation (table) uniquely.
**Attribute domain** − Every attribute has some pre-defined value scope, known as attribute domain.

## Constraints
Every relation has some conditions that must hold for it to be a valid relation. These conditions are called **Relational Integrity Constraints**. There are three main integrity constraints −
-   Key constraints
-   Domain constraints
-   Referential integrity constraints

### Key Constraints
There must be at least one minimal subset of attributes in the relation, which can identify a tuple uniquely. This minimal subset of attributes is called **key** for that relation. If there are more than one such minimal subsets, these are called **_candidate keys_**.

Key constraints force that −
- in a relation with a key attribute, no two tuples can have identical values for key attributes.
- a key attribute can not have NULL values.

### Domain Constraints
Attributes have specific values in real-world scenario. The same constraints have been tried to employ on the attributes of a relation. Every attribute is bound to have a specific range of values.

### Referential integrity Constraints
Referential integrity constraints work on the concept of Foreign Keys. A foreign key is a key attribute of a relation that can be referred in other relation.

Referential integrity constraint states that if a relation refers to a key attribute of a different or same relation, then that key element must exist.