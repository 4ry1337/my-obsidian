# Turing Machine 
A **Turing machine** is a mathematical [[Model of Computation]] describing an [[Abstract Machine|abstract machine]] that manipulates symbols on a strip of tape according to a table of rules. Despite the model's simplicity, it is capable of implementing any [[Algorithm | algorithm]].

## Description
 Turing machine consists of:
-   A *tape* divided into *cells*, one next to the other. Each cell contains a symbol from some finite *alphabet*. The alphabet contains a special blank symbol (here written as '0') and one or more other symbols. The tape is assumed to be arbitrarily extendable to the left and to the right, so that the Turing machine is always supplied with as much tape as it needs for its computation. Cells that have not been written before are assumed to be filled with the blank symbol. In some models the tape has a left end marked with a special symbol; the tape extends or is indefinitely extensible to the right.
-   A *head* that can read and write symbols on the tape and move the tape left and right one (and only one) cell at a time.
	- In some models the head moves and the tape is stationary.
-   A *state register* that stores the state of the Turing machine, one of finitely many. Among these is the special *start state* with which the state register is initialized.
-   A finite *table* of instructions that, given the *state*(${q_i}$) the machine is *currently in* and the *symbol*(${a_j}$) it is reading on the tape (symbol currently under the head), tells the machine to do the following *in sequence* (for the 5-tuple models):
1. Either erase or write a symbol (replacing ${a_j}$ with ${a_{j1}}$).
2. Move the head (which is described by ${d_k}$ and can have values: 'L' for one step left _or_ 'R' for one step right _or_ 'N' for staying in the same place).
3. Assume the same or a *new state* as prescribed (go to state ${q_{i1}}$).

In *the 4-tuple models*, erasing or writing a symbol (${a_{j1}}$) and moving the head left or right (${d_k}$) are specified as separate instructions. The table tells the machine to (ia) erase or write a symbol _or_ (ib) move the head left or right, _and then_ (ii) assume the same or a new state as prescribed, but not both actions (ia) and (ib) in the same instruction. In some models, if there is no entry in the table for the current combination of symbol and state, then the machine will halt; other models require all entries to be filled.

Every part of the machine (i.e. its state, symbol-collections, and used tape at any given time) and its actions (such as printing, erasing and tape motion) is *finite*, *discrete* and *distinguishable*; it is the unlimited amount of tape and runtime that gives it an unbounded amount of [[storage space]].

## Definition
Following Hopcroft & Ullman (1979, p. 148), a (one-tape) Turing machine can be formally defined as a 7-tuple ${M=\langle Q,\Gamma ,b,\Sigma ,\delta ,q_{0},F\rangle }$ where
- ${\Gamma}$ is a finite, non-empty set of *tape alphabet symbols*;
- ${b\in \Gamma }$ is the *blank symbol* (the only symbol allowed to occur on the tape infinitely often at any step during the computation);
- ${\Sigma \subseteq \Gamma \setminus \{b\}}$ is the set of *input symbols*, that is, the set of symbols allowed to appear in the initial tape contents;
- ${Q}$ is a finite, non-empty set of *states*;
- ${q_{0}\in Q}$ is the *initial state*;
- ${F\subseteq Q}$ is the set of *final states* or *accepting states*. The initial tape contents is said to be *accepted* by ${M}$ if it eventually halts in a state from ${F}$.
- ${\delta :(Q\setminus F)\times \Gamma \not \to Q\times \Gamma \times \{L,R\}}$ is a *partial function* called the *transition function*, where L is left shift, R is right shift. If ${\delta}$ is not defined on the current state and the current tape symbol, then the machine halts; intuitively, the transition function specifies the next state transited from the current state, which symbol to overwrite the current symbol pointed by the head, and the next head movement.

In addition, the Turing machine can also have a reject state to make rejection more explicit. In that case there are three possibilities: accepting, rejecting, and running forever. Another possibility is to regard the final values on the tape as the output. However, if the only output is the final state the machine ends up in (or never halting), the machine can still effectively output a longer string by taking in an integer that tells it which bit of the string to output.

A relatively uncommon variant allows "no shift", say N, as a third element of the set of directions ${\{L,R\}}$.

The 7-tuple for the 3-state [[busy beaver]] looks like this:

- ${Q=\{{\mbox{A}},{\mbox{B}},{\mbox{C}},{\mbox{HALT}}\}}$ (states);
- ${\Gamma =\{0,1\}}$ (tape alphabet symbols);
- ${b=0}$ (blank symbol);
- ${\Sigma =\{1\}}$ (input symbols);
- ${q_{0}={\mbox{A}}}$ (initial state);
- ${F=\{{\mbox{HALT}}\}}$ (final states);
- ${\delta =}$ see state-table below (transition function).

Initially all tape cells are marked with ${0}$.
<table>
<caption>State table for 3-state, 2-symbol busy beaver
</caption>
<tbody>
<tr>
	<th rowspan="2">Tape symbol</th>
	<th colspan="3">Current state A</th>
	<th colspan="3">Current state B </th>
	<th colspan="3">Current state C</th>
</tr>
<tr>
	<td>Write symbol</td>
	<td>Move tape</td>
	<td>Next state</td>
	<td>Write symbol</td>
	<td>Move tape</td>
	<td>Next state</td>
	<td>Write symbol</td>
	<td>Move tape</td>
	<td>Next state</td>
</tr>
<tr>
	<td>0</td>
	<td>1</td>
	<td>R</td>
	<td><b>B</b></td>
	<td>1</td>
	<td>L</td>
	<td><b>A</b></td>
	<td>1</td>
	<td>L</td>
	<td><b>B</b></td>
</tr>
<tr>
	<td>1</td>
	<td>1</td>
	<td>L</td>
	<td><b>C</b></td>
	<td>1</td>
	<td>R</td>
	<td><b>B</b></td>
	<td>1</td>
	<td>R</td>
	<td><b>HALT</b></td>
</tr>
</tbody>
</table>

## Turing Completeness
**Turing completeness** is the ability for a system of instructions to simulate a Turing machine. A [[Programming Language|programming language]] that is Turing complete is theoretically capable of expressing all tasks accomplishable by computers; nearly all programming languages are Turing complete if the limitations of finite memory are ignored.

## Types of Turing Machine
Many types of Turing machines are used to define complexity classes:
- [[Deterministic Turing Machine|deterministic Turing machines]]
- probabilistic Turing machines
- [[Nondeterministic Turing Machine|nondeterministic Turing machines]]
- quantum Turing machines
- symmetric Turing machines
- alternating Turing machines

They are all equally powerful in principle, but when resources (such as time or space) are bounded, some of these may be more powerful than others.

### Limitations
#### [[Computational Complexity Theory | Computational complexity theory]]
A limitation of Turing machines is that they do not model the strengths of a particular arrangement well. For instance, modern stored-program computers are actually instances of a more specific form of [[Abstract Machine|abstract machine]] known as the [[random-access stored-program machine]] or RASP machine model.

#### Concurrency
Turing machines is that they do not model [[concurrency]] well. For example, there is a bound on the size of integer that can be computed by an always-halting [[Nondeterministic Turing Machine]] starting on a blank tape. By contrast, there are always-halting concurrent systems with no inputs that can compute an integer of unbounded size.

#### Interaction
In the early days of computing, computer use was typically limited to batch processing, i.e., non-interactive tasks, each producing output data from given input data. Computability theory, which studies computability of functions from inputs to outputs, and for which Turing machines were invented, reflects this practice.