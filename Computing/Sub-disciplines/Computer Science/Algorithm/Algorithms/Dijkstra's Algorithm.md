# Dijkstra's Algorithm
**Dijkstra's algorithm** is an [[Algorithm | algorithm]] for finding the [[Shortest Path Problems|shortest paths]] from source vertex to target vertex in a [[Graph | graph]].

Graph:
- Can be *weighted* 
	- Can't have *Nonnegative* weight on every edge
- Can either be *undirected* or *directed*

## Derivation
Let ${G=(V,E)}$ be a directed graph in which each edge has a nonnegative length, and there is a distinguished vertex s called the source. For simplicity, we will assume that ${V=\{1, 2, ..., n\}}$ and ${s=1}$.  

Initially, the set of vertices is partitioned into two sets ${X=\{1\}}$ and ${Y=\{2, 3, ..., n\}}$. The intention is that X contains the set of vertices whose distance from the source has already been determined. At each step, we select a vertex ${y \in Y}$ whose distance from the source vertex has already been found and move it to ${X}$. Associated with each vertex ${y \in Y}$ is a label ${\lambda[y]}$, which is the length of a shortest path that passes only through vertices in ${X}$. Once a vertex ${y \in Y}$ is moved to ${X}$, the label of each vertex ${w \in Y}$ that is adjacent to ${y}$ is [[#^RelaxationOfEdge|updated]] indicating that a shorter path to ${w}$ via ${y}$ has been discovered. Throughout this section, for any vertex ${v \in V}$ , ${\delta[v]}$ will denote the distance from the source vertex ${s}$ to ${v}$. As will be shown later, at the end of the algorithm, ${\delta[v] = \lambda[v]}$ for each vertex ${v \in V}$.

1. ${X \leftarrow {1}}$; ${Y \leftarrow V - {1}}$  
2. For each vertex ${v \in Y}$ if there is an edge from ${1}$ to ${v}$, then let ${\lambda[v]}$ (the label of v) be the length of that edge; otherwise, let ${\lambda[v] = ∞}$. Let  ${\lambda[1] = 0}$.  
3. while ${Y \ne \{\}}$  
4. Let ${y \in Y}$ be such that ${\lambda[y]}$ is minimum.  
5. move ${y}$ from ${Y}$ to ${X}$.  
6. update the labels of those vertices in ${Y}$ that are adjacent to ${y}$.  
7. end while

### Relaxation

^RelaxationOfEdge

${\lambda[y]=\mathit{\min}\{\lambda[y], \lambda[w] + length(w, y)\}}$

## [[Pseudocode]]
```java
method dijkstra(G, S)
	X := {1}
	Y := V-{1}
	λ[1] := 0
	for y:=2 to n
		if y is adjacent to 1 then
			λ[1]:=length[1, y]
		else λ[1] = MAXINT
	endfor
	for j:=1 to n-1 do
		Let y ∈ Y be such that λ[y] is minimum  
		X := X ∪ {y} {add vertex y to X}  
		Y := Y - {y} {delete vertex y from Y }  
		for each edge (y, w)  
			if w ∈ Y and λ[y] + length[y, w] < λ[w] then  
			λ[w]← λ[y] + length[y, w]  
		end for
	endfor
```
**[[Time Complexity]]:** ${\theta(|V|^2)}$
**[[Space Complexity]]:** ${\theta(V)}$


## Dijkstra's Algorithm Applications
-   To find the shortest path
-   In social networking applications
-   In a telephone network
-   To find the locations in the map