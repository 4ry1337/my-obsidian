# NP complexity
In [[Computational Complexity Theory | computational complexity theory]], **NP** (**nondeterministic polynomial time**) is a [[Complexity Class | complexity class]] used to classify [[Decision Problem | decision problems]]. NP is the set of decision problems for which the problem instances, where the answer is "yes", have proofs verifiable in polynomial time by a [[Deterministic Turing Machine]], or alternatively the set of problems that can be solved in polynomial time by a [[Nondeterministic Turing Machine|nondeterministic Turing machine]].

## Formal definition
The [[Complexity Class]] NP can be defined in terms of NTIME as follows:

${{\mathsf {NP}}=\bigcup _{k\in \mathbb {N} }{\mathsf {NTIME}}(n^{k}).}$

where ${{\mathsf {NTIME}}(n^{k})}$ is the set of decision problems that can be solved by a [[Nondeterministic Turing Machine|nondeterministic Turing machine]] in ${O(n^{k})}$ time.

Alternatively, NP can be defined using deterministic Turing machines as verifiers. A [[language]] *L* is in NP if and only if there exist polynomials *p* and *q*, and a deterministic Turing machine *M*, such that

- For all *x* and *y*, the machine *M* runs in time $p(|x|)$ on input ${(x,y)}$
- For all *x* in *L*, there exists a string *y* of length $q(|x|)$ such that ${M(x,y)=1}$
- For all *x* not in *L* and all strings *y* of length $q(|x|)$, ${M(x,y)=0}$

## Properties
NP is closed under union, intersection, concatenation, [[Kleene star]] and [[reversal]]. It is not known whether NP is closed under complement (this question is the so-called "NP versus co-NP" question).