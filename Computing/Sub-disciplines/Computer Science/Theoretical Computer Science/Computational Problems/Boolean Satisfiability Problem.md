# Boolean satisfiability problem
In [[Computer Science | computer science]], the **Boolean satisfiability problem** (sometimes called **propositional satisfiability problem** and abbreviated **SATISFIABILITY**, **SAT** or **B-SAT**) is the problem of determining if there exists an interpretation that satisfies a given Boolean formula.

SAT is the first problem that was proved to be [[NP-completeness|NP-complete]]; see Cook–Levin theorem. This means that all problems in the complexity class [[NP]], which includes a wide range of natural decision and optimization problems, are at most as difficult to solve as SAT.

## Definitions
A *propositional logic formula*, also called *Boolean expression*, is built from *variables*, operators:
- *AND* (*conjunction*, also denoted by ∧)
- *OR* (*disjunction*, ∨)
- *NOT* (*negation*, ¬)
and *parentheses*.

A formula is said to be *satisfiable* if it can be made TRUE by assigning appropriate logical values (i.e. TRUE, FALSE) to its variables.

The _Boolean satisfiability problem_ (SAT) is, given a formula, to check whether it is satisfiable. This [[Decision Problem | decision problem]] is of central importance in many areas of [[Computer Science | computer science]], including [[Theoretical Computer Science | theoretical computer science]], [[Computational Complexity Theory|complexity theory]], algorithmics, cryptography and artificial intelligence.

### Conjunctive normal form

^ce1a9d

A *literal* is either a variable (in which case it is called a *positive literal*) or the negation of a variable (called a *negative literal*). A *clause* is a disjunction of literals (or a single literal). A clause is called a Horn clause if it contains at most one positive literal. A formula is in *conjunctive normal form* (CNF) if it is a conjunction of clauses (or a single clause).

Using the laws of Boolean algebra, every propositional logic formula can be transformed into an equivalent conjunctive normal form, which may, however, be exponentially longer. For example, transforming the formula (${x_1 \land y_1) \lor (x_2 \land y_2) \lor ... \lor (x_n \land y_n}$) into conjunctive normal form yields

$${(x_1 \land x_2 \land \cdots \land x_n) \lor
(y_1 \land x_2 \land \cdots \land x_n) \lor
(x_1 \land y_2 \land \cdots \land x_n) \lor
(y_1 \land y_2 \land \cdots \land x_n) \lor
\cdots \lor
(x_1 \land x_2 \land \cdots \land y_n) \lor
(y_1 \land x_2 \land \cdots \land y_n) \lor
(x_1 \land y_2 \land \cdots \land y_n) \lor
(y_1 \land y_2 \land \cdots \land y_n)}$$

while the former is a disjunction of ${n}$ conjunctions of 2 variables, the latter consists of ${2^n}$ clauses of ${n}$ variables.

