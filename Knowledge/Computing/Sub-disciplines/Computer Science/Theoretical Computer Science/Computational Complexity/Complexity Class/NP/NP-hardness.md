# NP-hardness
In [[Computational Complexity Theory|computational complexity theory]], **NP-hardness** (non-deterministic polynomial-time hardness) is the defining property of a class of problems that are informally "at least as hard as the hardest problems in NP.

## Definition
A [[Decision Problem|decision problem]] *H* is NP-hard when for every problem *L* in NP, there is a polynomial-time many-one reduction from *L* to *H*. An equivalent definition is to require that every problem *L* in NP can be solved in polynomial time by an oracle machine with an oracle for *H*. Informally, an algorithm can be thought of that calls such an oracle machine as a subroutine for solving *H* and solves *L* in polynomial time if the subroutine call takes only one step to compute.

## Consequences
If P ≠ NP, then NP-hard problems could not be solved in polynomial time.