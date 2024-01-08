# P versus NP problem
The **P versus NP problem** is a major unsolved problem in [[Theoretical Computer Science | theoretical computer science]]. In informal terms, it asks whether every problem whose solution can be quickly verified can also be quickly solved.

The relation between the [[Complexity Class | complexity classes]] P and NP is studied in [[Computational Complexity Theory | computational complexity theory]], the part of the [[Theory of Computation | theory of computation]] dealing with the resources required during computation to solve a given problem. The most common resources are [[Time Complexity | time]] and [[Space Complexity | space]].

In such analysis, a model of the computer for which time must be analyzed is required. Typically such models assume that the computer is deterministic and [[Model of Computation#^59c4f1|sequential]].

The class P consists of all those [[Decision Problem|decision problems]] that can be solved on a deterministic sequential machine in an amount of time that is polynomial in the size of the input; 

The class NP consists of all those decision problems whose positive solutions can be verified in polynomial time given the right information, or equivalently, whose solution can be found in polynomial time on a non-deterministic machine.

Clearly, P ⊆ NP. Arguably, the biggest open question in [[Theoretical Computer Science | theoretical computer science]] concerns the relationship between those two classes:

Is P equal to NP?

To attack the P = NP question, the concept of [[NP-completeness]] is very useful. NP-complete problems are a set of problems to each of which any other NP-problem can be reduced in polynomial time and whose solution may still be verified in polynomial time. That is, any NP problem can be transformed into any of the NP-complete problems. Informally, an NP-complete problem is an NP problem that is at least as "tough" as any other problem in NP.

[[NP-hardness | NP-hard]] problems are those at least as hard as NP problems; i.e., all NP problems can be reduced (in polynomial time) to them. NP-hard problems need not be in NP; i.e., they need not have solutions verifiable in polynomial time.

![[np np-complete np-hard.png]]

## Consequences of solution
One of the reasons the problem attracts so much attention is the consequences of the possible answers. Either direction of resolution would advance theory enormously, and perhaps have huge practical consequences as well.

### P = NP
A proof that P = NP could have stunning practical consequences if the proof leads to efficient methods for solving some of the important problems in NP. The potential consequences, both positive and negative, arise since various NP-complete problems are fundamental in many fields.

It is also very possible that a proof would _not_ lead to practical algorithms for NP-complete problems. The formulation of the problem does not require that the bounding polynomial be small or even specifically known. A non-constructive proof might show a solution exists without specifying either an algorithm to obtain it or a specific bound. Even if the proof is constructive, showing an explicit bounding polynomial and algorithmic details, if the polynomial is not very low-order the algorithm might not be sufficiently efficient in practice. In this case the initial proof would be mainly of interest to theoreticians, but the knowledge that polynomial time solutions are possible would surely spur research into better (and possibly practical) methods to achieve them.

### P ≠ NP
A proof that showed that P ≠ NP would lack the practical computational benefits of a proof that P = NP, but would nevertheless represent a very significant advance in [[Computational Complexity Theory]] and provide guidance for future research. It would allow one to show in a formal way that many common problems cannot be solved efficiently, so that the attention of researchers can be focused on partial solutions or solutions to other problems. Due to widespread belief in P ≠ NP, much of this focusing of research has already taken place.

## Formal definitions
Conceptually speaking, a _decision problem_ is a problem that takes as input some string _w_ over an alphabet Σ, and outputs "yes" or "no". If there is an algorithm that can produce the correct answer for any input string of length _n_ in at most _cnk_ steps, where _k_ and _c_ are constants independent of the input string, then we say that the problem can be solved in _polynomial time_ and we place it in the class P.

Formally, P is defined as the set of all languages that can be decided by a deterministic polynomial-time Turing machine. That is,

${\displaystyle \mathbf {P} =\{L:L=L(M){\text{ for some deterministic polynomial-time Turing machine }}M\}}$

where

${\displaystyle L(M)=\{w\in \Sigma^{*}:M{\text{ accepts }}w\}}$

and a deterministic polynomial-time Turing machine is a deterministic Turing machine _M_ that satisfies the following two conditions:

1.  _M_ halts on all inputs _w_ and
2.  there exists {\displaystyle k\in N} such that {\displaystyle T_{M}(n)\in O(n^{k})}, where _O_ refers to the [[Computational Complexity Theory#^BigOh|big O notation]] and
   ${\displaystyle T_{M}(n)=\max\{t_{M}(w):w\in \Sigma ^{*},|w|=n\}}$
   ${\displaystyle t_{M}(w)={\text{ number of steps }}M{\text{ takes to halt on input }}w.}$

NP can be defined similarly using nondeterministic Turing machines. However, a modern approach to define NP is to use the concept of *certificate* and _verifier_.
Formally, NP is defined as the set of languages over a finite alphabet that have a verifier that runs in polynomial time, where the notion of "verifier" is defined as follows.

Let _L_ be a language over a finite alphabet, Σ.

_L_ ∈ NP if, and only if, there exists a binary relation ${\displaystyle R\subset \Sigma ^{*}\times \Sigma ^{*}}$ and a positive integer _k_ such that the following two conditions are satisfied:

1.  For all ${\displaystyle x\in \Sigma ^{*}}$, ${\displaystyle x\in L\Leftrightarrow \exists y\in \Sigma ^{*}}$ such that (_x_, _y_) ∈ _R_ and ${\displaystyle |y|\in O(|x|^{k})}$;
2.  the language ${\displaystyle L_{R}=\{x\#y:(x,y)\in R\}} over ${\displaystyle \Sigma \cup \{\#\}}$ is decidable by a deterministic Turing machine in polynomial time.

A Turing machine that decides _LR_ is called a _verifier_ for _L_ and a _y_ such that (_x_, _y_) ∈ _R_ is called a _certificate of membership_ of _x_ in _L_.

In general, a verifier does not have to be polynomial-time. However, for _L_ to be in NP, there must be a verifier that runs in polynomial time.