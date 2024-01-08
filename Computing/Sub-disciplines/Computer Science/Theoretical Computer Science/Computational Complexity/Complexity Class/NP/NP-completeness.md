# NP completeness
In [[Computational Complexity Theory | computational complexity theory]], a problem is **NP-complete**(Nondeterministic polynomial-time complete) when:
1. it is a problem for which the correctness of each solution can be verified quickly (namely, in polynomial time and a brute-force search algorithm can find a solution by trying all possible solutions.
2. the problem can be used to simulate every other problem for which we can verify quickly that a solution is correct. In this sense, NP-complete problems are the hardest of the problems to which solutions can be verified quickly. If we could find solutions of some NP-complete problem quickly, we could quickly find the solutions of every other problem to which a given solution can be easily verified.

## Formal definition

A decision problem ${\displaystyle \scriptstyle C}$ is NP-complete if:
1.  ${\displaystyle \scriptstyle C}$ is in NP, and
2.  Every problem in NP is [[Complexity Class#^17869a|reducible]] to ${\displaystyle \scriptstyle C}$ in polynomial time.

${\displaystyle \scriptstyle C}$ can be shown to be in NP by demonstrating that a candidate solution to ${\displaystyle \scriptstyle C}$ can be verified in polynomial time.

Note that a problem satisfying condition 2 is said to be [[NP-hardness|NP-hard]], whether or not it satisfies condition 1.

A consequence of this definition is that if we had a polynomial time algorithm (on a [[Universal Turing Machine | UTM]], or any other [[Turing-equivalent]] [[Abstract Machine]]) for ${\displaystyle \scriptstyle C}$, we could solve all problems in NP in polynomial time.

## NP-complete problems
The easiest way to prove that some new problem is NP-complete is first to prove that it is in NP, and then to reduce some known NP-complete problem to it. Therefore, it is useful to know a variety of NP-complete problems. The list below contains some well-known problems that are NP-complete when expressed as decision problems.

- [[Booolean Satifiability Problem | Boolean satisfiability problem (SAT)]]
- [[Knapsack Problem | Knapsack problem]]
- Hamiltonian path problem
- [[Travelling Salesman Problem | Travelling salesman problem]] (decision version)
- Subgraph isomorphism problem
- Subset sum problem
- Clique problem
- Vertex cover problem