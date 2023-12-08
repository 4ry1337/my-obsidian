# Space Complexity
In [[Computer Science|computer science]], the **space complexity**
is the [[Computational Complexity|computational complexity]] that describes the amount of memory space required to run an [[Algorithm | algorithm]].

## Space complexity classes
The complexity classes DSPACE(f(n)) and NSPACE(f(n)) are the sets of languages that are decidable by deterministic (respectively, non-deterministic) [[Turing Machine | Turing machines]] that use ${O(f(n))}$ space. The complexity classes [PSPACE] and [NPSPACE] allow ${f}$ to be any polynomial, analogously to [P](https://en.wikipedia.org/wiki/P_(complexity) "P (complexity)") and [NP](https://en.wikipedia.org/wiki/NP_(complexity) "NP (complexity)"). That is,

${{\mathsf{PSPACE}}=\bigcup{c \in \mathbb{Z}^{+}}{\mathsf{DSPACE}}(n^{c})}$

and

${{\mathsf{NPSPACE}}=\bigcup {c\in\mathbb{Z}^{+}}{\mathsf{NSPACE}}(n^{c})}$

## Auxiliary space complexity
The term **auxiliary space** refers to space other than that consumed by the input.

Auxiliary space complexity could be formally defined in terms of a [[Turing Machine | Turing machine]] with a separate *input tape* which cannot be written to, only read, and a conventional working tape which can be written to. The auxiliary space complexity is then defined (and analyzed) via the working tape.