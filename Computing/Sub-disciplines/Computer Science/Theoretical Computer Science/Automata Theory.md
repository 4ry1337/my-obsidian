# Automata Theory
In [[Theoretical Computer Science|theoretical computer science]], **Automata theory** is the study of [[Abstract Machine|abstract machines]] and automata, as well as the [[Computational Problems | computational problems]] that can be solved using them.

### Formal definition
**Automaton**
An automaton can be represented formally by a 5-tuple ${M=\langle \Sigma ,\Gamma ,Q,\delta ,\lambda \rangle }$, where:

- ${\Sigma}$ is a finite set of _symbols_, called the _input alphabet_ of the automaton,
- ${\Gamma }$ is another finite set of symbols, called the _output alphabet_ of the automaton,
- ${Q}$ is a set of _states_,
- ${\delta}$ is the _next-state function_ or _transition function_ ${\displaystyle \delta :Q\times \Sigma \to Q}$ mapping state-input pairs to successor states,
- ${\lambda}$ is the *next-output function* ${\lambda :Q\times \Sigma \to \Gamma }$ mapping state-input pairs to outputs.

If ${\displaystyle Q}$ is finite, then ${\displaystyle M}$ is a finite automaton.

**Input word**
An automaton reads a finite string of symbols ${a_{1}a_{2}...a_{n}}$, where ${a_{i}\in \Sigma}$, which is called an *input word*. The set of all words is denoted by ${\Sigma ^{*}}$.

**Run**
A sequence of states ${q_{0},q_{1},...,q_{n}}$, where ${q_{i}\in Q}$ such that ${q_{i}=\delta (q_{i-1},a_{i})}$ for ${0<i\leq n}$, is a _run_ of the automaton on an input ${a_{1}a_{2}...a_{n}\in \Sigma^{*}}$ starting from state ${q_{0}}$. In other words, at first the automaton is at the start state ${q_{0}}$, and receives input ${a_{1}}$. For ${a_{1}}$ and every following ${a_{i}}$ in the input string, the automaton picks the next state ${q_{i}}$ according to the transition function ${\delta (q_{i-1},a_{i})}$, until the last symbol ${a_{n}}$ has been read, leaving the machine in the _final state_ of the run, ${q_{n}}$. Similarly, at each step, the automaton emits an output symbol according to the output function ${\lambda (q_{i-1},a_{i})}$.

The transition function ${\delta}$ is extended inductively into ${{\overline{\delta}}:Q\times\Sigma^{*}\to Q}$ to describe the machine's behavior when fed whole input words. For the empty string ${\varepsilon}$, ${{\overline{\delta}}(q,\varepsilon)=q}$ for all states ${q}$, and for strings ${wa}$ where ${a}$ is the last symbol and ${w}$ is the (possibly empty) rest of the string, ${{\overline{\delta}}(q,wa)=\delta({\overline{\delta}}(q,w),a)}$. The output function ${\lambda}$ may be extended similarly into ${{\overline{\lambda}}(q,w)}$, which gives the complete output of the machine when run on word ${w}$ from state ${q}$.

**Acceptor**
In order to study an automaton with the theory of [[Formal Language|formal languages]], an automaton may be considered as an _acceptor_, replacing the output alphabet and function ${\Gamma}$ and ${\lambda}$ with
- ${q_{0}\in Q}$, a designated _start state_, and
- ${F}$, a set of states of ${Q}$(i.e. ${F\subseteq Q}$ called _accept states_.

This allows the following to be defined:

**Accepting word**
A word ${w=a_{1}a_{2}...a_{n}\in\Sigma^{*}}$ is an _accepting word_ for the automaton if ${{\overline{\delta}}(q_{0},w)\in F}$, that is, if after consuming the whole string ${w}$ the machine is in an *accept state*.

**Recognized language**
The language ${L\subseteq\Sigma^{*}}$ _recognized_ by an automaton is the set of all the words that are accepted by the automaton, ${L=\{w\in \Sigma ^{*}\ |\ {\overline {\delta }}(q_{0},w)\in F\}}$.
Recognizable languages

The *recognizable languages* are the set of languages that are recognized by some automaton. For _finite automata_ the recognizable languages are *regular languages*. For different types of automata, the recognizable languages are different.

## Types of automata
| Automaton            | Recognizable languages           |
| -------------------- | -------------------------------- |
| [[Finite-State Machine]] | [[Regular Languages]]                |
| [[Pushdown Automaton]]   | [[Context-Free Languages]]           |
| [[Turing Machine]]       | [[Recursively Enumerable Languages]] | 

### Hierarchy in terms of powers
Automaton From lowest to highest
Deterministic Finite Automaton (DFA) || Nondeterministic Finite Automaton (NFA)  
$${\cap}$$  
Deterministic Push Down Automaton(DPDA) || Nondeterministic Push Down Automaton (NPDA)  
$${\cap}$$
Deterministic Turing Machine (DTM) || Nondeterministic Turing Machine (NTM) || Probabilistic Turing Machine (PTM) || Multitape Turing Machine (MTM) || Multidimensional Turing Machine