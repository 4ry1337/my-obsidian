# Shortest Path Problem
The **shortest path problem** is the problem of finding a path between two vertices in a [[Graph |graph]] such that the sum of the weights of its constituent edges is minimized.

### Problem Variations:
- [[Single-Pair Shortest Path Problem]]
- [[Single-Source Shortest Path Problem]], in which we have to find shortest paths from a source vertex ${v}$ to all other vertices in the graph.
- [[Single-Destination Shortest Path Problem]], in which we have to find shortest paths from all vertices in the directed graph to a single destination vertex ${v}$. This can be reduced to the single-source shortest path problem by reversing the arcs in the directed graph.
- [[All-Pairs Shortest Path Problem]],  in which we have to find shortest paths between every pair of vertices ${v}$, ${v'}$ in the graph.

## Algorithms
- [[Dijkstra's Algorithm]] solves the single-source shortest path problem with non-negative edge weight.
- [[Bellman–Ford algorithm]] solves the single-source problem if edge weights may be negative.
- [[A* search algorithm]] solves for single-pair shortest path using heuristics to try to speed up the search.
- [[Floyd–Warshall algorithm]] solves all pairs shortest paths.
- [[Johnson's algorithm]] solves all pairs shortest paths, and may be faster than Floyd–Warshall on [[sparse graphs]].
- [[Viterbi algorithm]] solves the shortest stochastic path problem with an additional probabilistic weight on each node.