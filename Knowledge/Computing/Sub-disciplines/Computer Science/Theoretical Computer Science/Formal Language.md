# Formal Language
In [[Computer Science | computer science]], a **formal language** consists of words whose letters are taken from an alphabet and are well-formed according to a specific set of rules.

The *alphabet* of a formal language consists of symbols, letters, or tokens that concatenate into strings of the language. Each string concatenated from *symbols* of this alphabet is called a *word*, and the words that belong to a particular formal language are sometimes called _well-formed words_ or _well-formed formulas_. A formal language is often defined by means of a formal grammar such as a regular grammar or context-free grammar, which consists of its formation rules.

> In [[Computer Science | computer science]], formal languages are used as the basis for defining the grammar of [[Programming Language | programming languages]] and formalized versions of subsets of natural languages in which the words of the language represent concepts that are associated with particular meanings or semantics.

> In [[Computational Complexity Theory | computational complexity theory]], [[Decision Problem|decision problems]] are typically defined as formal languages, and [[Complexity Class|complexity classes]] are defined as the sets of the formal languages that can be parsed by machines with limited computational power.

## Definition
A **formal language** _L_ over an alphabet Σ is a subset of Σ*, that is, a set of words over that alphabet.

## Operations on languages
Certain operations on languages includes the standard set operations, such as union, intersection, and complement. Another class of operation is the element-wise application of string operations.

Let ${L_{1}}$ and ${L_{2}}$ are languages over some common alphabet ${\Sigma}$.
- The *concatenation* ${L_{1}\cdot L_{2}}$ consists of all strings of the form ${vw}$ where ${v}$ is a string from ${L_{1}}$ and ${w}$ is a string from ${L_{2}}$.
- The *intersection* ${L_{1}\cap L_{2}}$ of ${L_{1}}$ and ${L_{2}}$ consists of all strings that are contained in both languages
- The *complement* ${\neg L_{1}}$ of ${L_{1}}$ with respect to ${\Sigma }$ consists of all strings over ${\Sigma }$ that are not in ${L_{1}}$.
- The Kleene star: the language consisting of all words that are concatenations of zero or more words in the original language;
- *Reversal*:
	- Let *ε* be the empty word, then ${\varepsilon ^{R}=\varepsilon }$, and
    - for each non-empty word ${w=\sigma_{1} \cdots \sigma_{n}}$ (where ${\sigma_{1},\ldots ,\sigma_{n}}$ are elements of some alphabet), let ${w^{R}=\sigma _{n}\cdots \sigma _{1}}$,
    - then for a formal language ${L}$, ${L^{R}=\{w^{R}\mid w\in L\}}$.
- String homomorphism


## Applications
- [[Programming Language | Programming languages]]