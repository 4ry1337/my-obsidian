# Knapsack Problem
The **knapsack problem** is a problem in combinatorial [[Optimization Problem | optimization]]: Given a set of items, each with a weight and a value, determine the number of each item to include in a collection so that the total weight is less than or equal to a given limit and the total value is as large as possible. It derives its name from the problem faced by someone who is constrained by a fixed-size knapsack and must fill it with the most valuable items. The problem often arises in resource allocation where the decision-makers have to choose from a set of non-divisible projects or tasks under a fixed budget or time constraint, respectively.

## Problem Definition
Given a set of items, each with a weight and a value, determine the number of each item to include in a collection so that the total weight is less than or equal to a given limit and the total value is as large as possible.
### 0/1 Knapsack Problem
In 0/1 knapsack problem, answer is given in the form of consecutive ${x_i}$ booleans indicating object at ${i}$th position is included or not. Given a set of ${n}$ items numbered from 1 up to ${n}$, each with a weight ${w_i}$ and a value ${v_i}$, along with a maximum weight capacity ${W}$,

maximize ${\sum_{i=1}^{n}v_{i}x_{i}}$

subject to ${\sum_{i=1}^{n}w_{i}x_{i}\leq W}$ and ${x_i \in \{0,1\}}$.

Here ${x_i}$ represents the number of instances of item ${i}$ to include in the knapsack. Informally, the problem is to maximize the sum of the values of the items in the knapsack so that the sum of the weights is less than or equal to the knapsack's capacity.

## Solution
### [[Dynamic Programming]] with Tabulation
Let ${V[i, j]}$ denote the value obtained by filling a knapsack of size ${j}$ with items taken from the first ${i}$ items ${\{x_1, x_2, ..., x_i\}}$ in optimal way, for ${i \in [0, n]}$ and ${j \in [0, W]}$. Thus, the value at ${V[n, C]}$ is maximum value. Values at ${V[0, j]}$ and ${V[i, 0]}$ are 0, since for former there is nothing in the knapsack and letter nothing can be putted in a knapsack of size 0. Then, for remaining ${V[i, j]}$ are evaluated using:
$${V[i, j]=\mathit{\max}\{V[i-1, j], V[i-1, j-s_i]+w_i\}}$$

- ${V[i-1, j]}$: The maximum value obtained by filling a knapsack of size j with items taken from ${{x_1, x_2, ..., x_{i-1}}}$ only in optimal way.
- ${V[i-1, j-s_i]+w_i}$: The maximum value obtained by filling a knapsack of size ${j-s_i}$ with items taken from ${{x_1, x_2, ..., x_{i-1}}}$ in optimal way plus the value of item ${x_i}$. This case applies only if ${j \geqslant s_i}$ and it amounts to adding item ${x_i}$ to a knapsack, since if ${j < s_i}$, ${j-s_i}$ is negative which is impossible.

Following recurrence for finding the *value* in an optimal packing:
$${V[i, j]=\begin{cases}
0 & \mbox{if } i=0 \mbox{or} j=0 \\
V[i-1, j] & \mbox{if } j<s_i \\
\mathit{\max}\{V[i-1, j], V[i-1, j-s_i]+w_i\} &\mbox{if } i>0 \mbox{ and } j\geqslant s_i
\end{cases}}$$

#### [[Pseudocode]]
```Java
V[1...n, 1...C]
s[1...n] // size
w[1...n] // weight | profit | cost
for i:=0 to n do
	V[i, 0] :=0
endfor
for j:=0 to C do
	V[0, j] :=0
endfor
for i:=1 to n do
	for j:=1 to C do
		V[i, j] := V[i-1, j]
		if s[i] <= j then
			V[i, j] := max(V[i, j], V[i-1, j-s[i]] + w[i])
	endfor
endfor
return V[n, C]
```
**[[Time Complexity]]:** ${\theta(nC)}$ - size of table, as filling each entry requires ${\theta(1)}$
**[[Space Complexity]]:** ${\theta(C)}$

To find which objects are included, use [[Backtracking | backtracking]].
Start backtracking from $v = V[n, C]$.
- If ${v}$ comes from the top entry, the object in this row is *not* included.
- If ${v}$ does not come from the top entry, the object in this row is included, go left by the *weight* of the included item and then vertically up. 