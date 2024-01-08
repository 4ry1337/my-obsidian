# Breadth-First Search
**Breadth-first search** (**BFS**) is an [[Algorithm|algorithm]] for searching a [[Tree|tree data structure]] for a node that satisfies a given property. It starts at the tree root and explores all nodes at the present depth prior to moving on to the nodes at the next depth level. Extra memory, usually a [[Queue|queue]], is needed to *keep track of the child nodes* that were encountered but not yet explored.

Breadth-first search can be generalized to [[Graph|graphs]], when the start node (*search key*) is explicitly given, and precautions are taken against following a vertex twice.

## [[Pseudocode]]
**Input**: A graph G and a *starting vertex* root of G
**Output**: Goal state. The *parent* links trace the shortest path back to root
```cpp
procedure BFS(G, root) is
	let Q be a queue
	label root as explored
	Q.enqueue(root)
	while Q is not empty do
		v := Q.dequeue()
		if v is the goal then
			return v
		for all edges from v to w in G.adjacentEdges(v) do
			if w is not labeled as explored then
				label w as explored
				Q.enqueue(w)
```

## Complexity
**[[Time Complexity]]:** ${O(|V|+|E|)}$
**[[Space Complexity]]**: ${O(|V|)}$

## Applications
- Copying garbage collection, Cheney's algorithm
- Finding the shortest path between two nodes _u_ and _v_, with path length measured by number of edges.
- (Reverse) Cuthill–McKee mesh numbering
- Ford–Fulkerson method for computing the maximum flow in a flow network.
-   Serialization/Deserialization of a binary tree vs serialization in sorted order, allows the tree to be re-constructed in an efficient manner.
- Construction of the *failure function* of the Aho-Corasick pattern matcher.
- Testing bipartiteness of a graph.
- Implementing parallel algorithms for computing a graph's transitive closure.