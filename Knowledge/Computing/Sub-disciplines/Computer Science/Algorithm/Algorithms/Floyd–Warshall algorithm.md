# Floyd–Warshall Algorithm
The **Floyd–Warshall algorithm** (also known as **Floyd's algorithm**, the **Roy–Warshall algorithm**, the **Roy–Floyd algorithm**, or the **WFI algorithm**) is an [[Algorithm| algorithm]] for finding [[Shortest Path Problems | shortest paths]] in a directed [[weighted graph]] with positive or negative edge weights (but with no negative cycles).

## Derivation
Let ${G = (V, E)}$ be a directed graph in which each edge (i, j) has a nonnegative length ${l[i, j]}$.
- If there is no edge from vertex ${i}$ to vertex ${j}$, then ${l[i, j] = ∞}$, 0 is for self loops.

The problem is to find the distance from each vertex to all other vertices, where the distance from vertex ${x}$ to vertex ${y}$ is the length of a shortest path from ${x}$ to ${y}$. For simplicity, we will assume that V = {1, 2, . . . , n}. Let ${i}$ and ${j}$ be two different vertices in V.

Define ${d_{i,j}^k}$ to be the length of a shortest path from ${i}$ to ${j}$ that does not pass through any vertex in ${\{k + 1, k + 2, . . . , n\}}$. Thus, for example, ${d_{i,j}^0 = l[i, j]}$, ${ d_{i,j}^1}$ is the length of a shortest path from ${i}$ to ${j}$ that does not pass through any vertex except possibly vertex 1, ${d_{i,j}^2}$ is the length of a shortest path from ${i}$ to ${j}$ that does not pass through any vertex except possibly vertex 1 or vertex 2 or both, and so on.

Then, by definition, ${d_{i,j}^n}$ is the length of a shortest path from ${i}$ to ${j}$, i.e., the distance from ${i}$ to ${j}$. Given this definition, we can compute ${d_{i,j}^k}$ recursively as follows:

$${d_{i,j}^k=
\begin{cases}
l[i, j] & \mbox{if }k=0 \\
\mathit{\min}\{d_{i,j}^{k-1}, d_{i,k}^{k-1}+d_{k,j}^{k-1}\} & \mbox{if }1 \leqslant k \leqslant n
\end{cases}}$$

## [[Pseudocode]]
```Java
method FloydWarshall(l[1...n, 1...n])
	D := l // copy the input matrix L into D
	for k:=1 to n do
		for i:=1 to n do
			for j:=1 to n do
				D[i, j] = min(D[i, j], D[i, k] + D[k, j])
			endfor
		endfor
	endfor
```
**[[Time Complexity]]:** ${\theta(|V|^3)}$
**[[Space Complexity]]:** ${\theta(|V|^2)}$