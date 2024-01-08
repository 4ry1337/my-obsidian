# Transaction
Transaction is a single logical unit of work which accesses and possibly modifies the contents of a database. The essence of transaction is that it combines a sequence of actions into one operation.

## ACID Properties
**ACID** is a set of properties of database transactions intended to guarantee data validity despite errors, power failures, and other mishaps.

- **A = Atomicity**
   Atomicity guarantees that each transaction is treated as a single "unit", which either succeeds completely or fails completely
-  **C = Consistency**
  Consistency ensures that a transaction can only bring the database from one valid state to another, maintaining database invariants: any data written to the database must be valid according to all defined rules, including constraints, cascades, triggers, and any combination thereof.
-  **I = Isolation**
  Isolation ensures that concurrent execution of transactions leaves the database in the same state that would have been obtained if the transactions were executed sequentially.
-  **D = Durability**
  Durability guarantees that once a transaction has been committed, it will remain committed even in the case of a system failure (e.g., power outage or crash).

## Advantages of Transactions
- Event Chaining
- Flexibility
- Avoiding Data Loss
- Database Management

## PostgreSQl Transaction Commands
A transactions is defined by a set of [[Structured Query Language|SQL]] commands surrounded by `BEGIN` and `COMMIT`

```SQL
Begin;
[Some operations];
Commit;
```
Also called *Transaction Block*

> PostgreSQL processes each SQL statement as transaction.

### Transactional Control
Transactional Control commands only used with [[Data Manipulation Language|DML]] commands
`BEGIN TRANSACTION` - to initiate a transaction.
`COMMIT` - to save changes invoked by transaction, alternatively `END TRANSACTION`.
`ROLLBACK` - to undo the changes.

### Savepoints
Savepoints allow to selectively undo some parts of a transaction and commit all others.
After defining a `SAVEPOINT` , return to it by using `ROLLBACK TO` command. All changes in database that occurred after the savepoint and before the rollback are cancelled, but the changes made earlier are saved.
