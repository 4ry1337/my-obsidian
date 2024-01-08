# Complexity Classes
In [[Computational Complexity Theory | computational complexity theory]], a **complexity class** is a set of [[Computational Problems]] of related [[Computational Complexity#^resources|resource-based [[Computational Complexity | complexity]] in the context of a [[Model of Computation | computational model]]. In particular, most complexity classes consist of [[Decision Problem|decision problems]] that can be solved by a [[Turing Machine|Turing machine]] with bounded [[Time Complexity | time]] or [[Space Complexity|space]]  resources.

## Basic Complexity Classes
### Basic definitions
Complexity classes are often defined using granular sets of complexity classes called **DTIME**(Deterministic Time) and **NTIME**(Non-Deterministic [[Time Complexity | Time]]) and **DSPACE**(Deterministic Space) and **NSPACE**(Non-Deterministic [[Space Complexity | Space]]). Using [[Computational Complexity Theory#Upper Bound and The Big O|big O notation]], they are defined as follows:
- The time complexity class ${{\mathsf {DTIME}}(t(n))}$ is the set of all problems that are decided by an ${O(t(n))}$ time [[Deterministic Turing Machine]].
- The time complexity class ${{\mathsf {NTIME}}(t(n))}$ is the set of all problems that are decided by an ${O(t(n))}$ time [[Nondeterministic Turing Machine|nondeterministic Turing machine]].
- The space complexity class ${{\mathsf {DSPACE}}(s(n))}$ is the set of all problems that are decided by an ${O(s(n))}$ space [[Deterministic Turing Machine]].
- The space complexity class ${{\mathsf {NSPACE}}(s(n))}$ is the set of all problems that are decided by an ${O(s(n))}$ space [[Nondeterministic Turing Machine|nondeterministic Turing machine]].

**Other basic classes:**

| Complexity class       | [[Model of Computation]]             | Resource Constraint     | Complexity Class | [[Model of Computation]]             | Resource Constraint      |
| ---------------------- | ------------------------------------ | ----------------------- | ---------------- | ------------------------------------ | ------------------------ |
| Deterministic Time     |                                      |                         |                  |                                      |                          |
| DTIME*(f(n))*          | [[Deterministic Turing Machine]]     | Time *O(f(n))*          | DSPACE(f(n))     | [[Deterministic Turing Machine]]     | Space *O(f(n))*          |
|                        |                                      |                         | L                | [[Deterministic Turing Machine]]     | Space *O(log(n))*        |
| P                      | [[Deterministic Turing Machine]]     | Time *O(poly(n))*       | PSPACE           | [[Deterministic Turing Machine]]     | Space *O(poly(n))*       |
| EXPTIME                | [[Deterministic Turing Machine]]     | Time $$O(2^{poly(n)})$$ | EXPSPACE         | [[Deterministic Turing Machine]]     | Space $$O(2^{poly(n)})$$ |
| Non-deterministic Time |                                      |                         |                  |                                      |                          |
| NTIME(f(n))            | [[Nondeterministic Turing Machine]] | Time *O(f(n))*          | NSPACE(f(n))     | [[Nondeterministic Turing Machine]] | Space *O(f(n))*          |
|                        |                                      |                         | NL               | [[Nondeterministic Turing Machine]] | Space *O(log(n))*        |
| NP                     | [[Nondeterministic Turing Machine]] | Time *O(poly(n))*       | NPSPACE          | [[Nondeterministic Turing Machine]] | Space *O(poly(n))*       |
| NEXPTIME               | [[Nondeterministic Turing Machine]] | Time $$O(2^{poly(n)})$$ | NEXPSAPCE        | [[Nondeterministic Turing Machine]] | Time $$O(2^{poly(n)})$$  |


## Properties of complexity classes
### Closure
> [[Further research needed]]
Complexity classes have a variety of closure properties. For example, decision classes may be closed under negation, disjunction, conjunction, or even under all Boolean operations. Moreover, they might also be closed under a variety of quantification schemes.

In mathematics, a subset of a given set is **closed** under an operation of the larger set if performing that operation on members of the subset always produces a member of that subset.

The **closure** of a subset is the result of a closure operator applied to the subset. The *closure* of a subset under some operations is the smallest subset that is closed under these operations. It is often called the *span* or the *generated set*.

### Reduction

^17869a

A **reduction** is an [[Algorithm|algorithm]] for transforming one [[Computational Problems|problem]] into another problem. A sufficiently efficient reduction from one problem to another may be used to show that the second problem is at least as difficult as the first.

#### Properties
A reduction is a *preordering*, that is a *reflexive* and *transitive relation*, on **P**(**N**)×**P**(**N**), where **P**(**N**) is the power set of the natural numbers.

#### Types of reduction
> [[Further research needed]]

### Hardness
Reductions motivate the concept of a problem being **hard** for a complexity class. A problem ${X}$ is hard for a class of problems **C** if every problem in **C** can be polynomial-time reduced to ${X}$. Thus no problem in **C** is harder than ${X}$, since an algorithm for ${X}$ allows us to solve any problem in **C** with at most polynomial slowdown. 

Of particular importance, the set of problems that are hard for **NP** is called the set of [[NP-hardness | NP-hard]] problems.

### Completeness
If a problem ${X}$ is hard for **C** and is also in **C**, then ${X}$ is said to be [[complete]] for **C**. This means that ${X}$ is the hardest problem in **C** (since there could be many problems that are equally hard, more precisely ${X}$ is as hard as the hardest problems in **C**).

Of particular importance is the class of [[NP-completeness | NP-complete]] problems—the most difficult problems in **NP**. Because all problems in **NP** can be polynomial-time reduced to **NP**-complete problems, finding an **NP**-complete problem that can be solved in polynomial time would mean that **P** = **NP**.

## Relationship between Complexity Classes
### Savitch's Theorem
In [[Computational Complexity Theory | computational complexity theory]] **Savitch's theorem** gives a relationship between deterministic and non-deterministic [[Space Complexity|space complexity]]. It states that for any function ${f\in \Omega (\log(n))}$

$${\mathsf{NSPACE}\left(f\left(n\right)\right)\subseteq \mathsf{DSPACE}\left(f\left(n\right)^{2}\right)}$$

In other words, if a [[Nondeterministic Turing Machine]] can solve a problem using ${f(n)}$ space, a [[Deterministic Turing Machine]] can solve the same problem in the square of that space bound. Although it seems that nondeterminism may produce exponential gains in time, this theorem shows that it has a markedly more limited effect on space requirements.

#### Corollaries
Some important corollaries of the theorem include:
- ${\mathsf{PSPACE} = \mathsf{NPSPACE}}$
    - This follows directly from the fact that the square of a polynomial function is still a polynomial function. It is believed that a similar relationship does not exist between the polynomial time complexity classes, P and NP, although this is still an open question.
- ${\mathsf{NL} ⊆ \mathsf{L}}$
    - STCON is NL-complete, and so all languages in NL are also in the complexity class ${\displaystyle {\mathsf {\color {Blue}L}}^{2}={\mathsf {DSPACE}}\left(\left(\log n\right)^{2}\right)}$.

### Hierarchy Theorem
#### Time Hierarchy Theorem
The **time hierarchy theorems** are important statements about time-bounded computation on [[Turing Machine|Turing machines]]. Informally, these theorems say that given more time, a Turing machine can solve more problems.

**Time Hierarchy Theorem.** If ${f(n)}$ is a time-constructible function, then there exists a [[Decision Problem|decision problem]] which cannot be solved in worst-case deterministic time ${f(n)}$ but can be solved in worst-case deterministic time ${f(n)^2}$. In other words,

${\mathsf{DTIME}(f(n))\subsetneq{\mathsf {DTIME}}\left(f(n)^{2}\right)}$

**Note 1.** ${f(n)}$ is at least ${n}$, since smaller functions are never time-constructible.  

**Note 2.** Even more generally, it can be shown that if ${f(n)}$ is time-constructible, then
${\mathsf {DTIME}}\left(o\left({\frac {f(n)}{\log f(n)}}\right)\right)\subsetneq {\mathsf {DTIME}}\left(f(n)\right)$

Non-deterministic time hierarchy theorem
If ${g(n)}$ is a time-constructible function, and ${f(n+1)=o(g(n))}$, then there exists a decision problem which cannot be solved in non-deterministic time ${f(n)}$ but can be solved in non-deterministic time ${g(n)}$.
$NTIME(f(n)) \subsetneq NTIME(g(n))$

#### Space Hierarchy Theorem
The **space hierarchy theorems** are separation results that show that both deterministic and nondeterministic machines can solve more problems in (asymptotically) more space, subject to certain conditions.

The space hierarchy theorems rely on the concept of space-constructible functions. The deterministic and nondeterministic space hierarchy theorems state that for all space-constructible functions ${f(n)}$,

${{\mathsf {SPACE}}\left(o(f(n))\right)\subsetneq {\mathsf {SPACE}}(f(n))}$,

where SPACE stands for either DSPACE or NSPACE, and o refers to the little o notation.

##### Statement
Formally, a function ${\displaystyle f:\mathbb {N} \longrightarrow \mathbb {N} }$ is space-constructible if ${\displaystyle f(n)\geq \log ~n}$ and there exists a Turing machine which computes the function ${\displaystyle f(n)}$ in space ${\displaystyle O(f(n))}$ when starting with an input ${\displaystyle 1^{n}}$, where ${\displaystyle 1^{n}}$ represents a string of _n_ consecutive 1s. Most of the common functions that we work with are space-constructible, including polynomials, exponents, and logarithms.

For every space-constructible function ${\displaystyle f:\mathbb {N} \longrightarrow \mathbb {N} }$, there exists a language L that is decidable in space ${\displaystyle O(f(n))}$ but not in space ${\displaystyle o(f(n))}$.

##### Corollaries
###### Corollary 1
For any two functions ${f_{1}}$, ${f_{2}:\mathbb {N} \longrightarrow \mathbb {N} }$, where ${f_{1}(n)}$ is ${o(f_{2}(n))}$ and ${f_{2}}$ is space-constructible, ${{\mathsf {SPACE}}(f_{1}(n))\subsetneq {\mathsf {SPACE}}(f_{2}(n))}$.

###### Corollary 2
_For any two nonnegative real numbers ${a_{1}<a_{2},{\mathsf {SPACE}}(n^{a_{1}})\subsetneq {\mathsf {SPACE}}(n^{a_{2}})}$._

###### Corollary 3
${NL \subsetneq PSPACE}$

###### Corollary 4
${PSPACE \subsetneq EXPSPACE}$

This last corollary shows the existence of decidable problems that are intractable. In other words, their decision procedures must use more than polynomial space.

###### Corollary 5
There are problems in PSPACE requiring an arbitrarily large exponent to solve; therefore PSPACE does not collapse to DSPACE(_n__k_) for some constant _k_.