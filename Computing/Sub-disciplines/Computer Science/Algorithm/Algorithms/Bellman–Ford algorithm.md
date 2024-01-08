# Bellman-Ford Algorithm
The **Bellman–Ford algorithm** is an [[Algorithm | algorithm]] that computes [[Shortest Path Problems | shortest paths]] from a single source vertex to all of the other vertices in a weighted digraph It is slower than [[Dijkstra's Algorithm]] for the same problem, but more versatile, as it is capable of handling graphs in which some of the edge weights are negative numbers.

## Derivation
Bellman–Ford proceeds by [[#^RelaxationOfEdge]], in which approximations to the correct distance are replaced by better ones until they eventually reach the solution. Algorithm simply relaxes *all* the edges, and does this ${|V|-1}$ times, where ${|V|}$ is the number of vertices in the graph.

In each of these repetitions, the number of vertices with correctly calculated distances grows, from which it follows that eventually all vertices will have their correct distances.

Problems with Bellman Ford Algorithm:
1. If there are negative weight cycles, the search for a shortest path will go on forever.
2. Choosing a bad ordering for relaxations leads to exponential relaxations.

This method allows the Bellman–Ford algorithm to be applied to a wider class of inputs than Dijkstra. The intermediate answers depend on the order of edges relaxed, but the final answer remains the same.

### Relaxation

^RelaxationOfEdge

${\lambda[y]=\mathit{\min}\{\lambda[y], \lambda[w] + length(w, y)\}}$

## [[Pseudocode]]
```java
for v in V
	v.distance = MAXINT
	v.p = none
endfor
source.distance=0
for i:= 1 to |V|-1
	for (u, v) in E
		if v.distance > u.distance + weight(u, v):
	        v.distance = u.distance + weight(u, v)
	        v.p = u
	endfor
endfor
```
the `p` value for each vertex is set to nothing. This value is a pointer to a predecessor vertex so that we can create a path later.

### Detecting Negative Cycles
A very short and simple addition to the Bellman-Ford algorithm can allow it to detect negative cycles, something that is very important because it disallows shortest-path finding altogether.

Add this code block after main code
```java
for (u, v) in E:
    if v.distance > u.distance + weight(u, v):
        print "A negative weight cycle exists"
```

## Complexity
**[[Time Complexity]]:**
- worst case: ${O(|V||E|)}$
- best case: ${O(|E|)}$
**[[Space Complexity]]:**

## Applications
A version of Bellman-Ford is used in the distance-vector routing protocol. This protocol decides how to route packets of data on a network. The distance equation (to decide weights in the network) is the number of routers a certain path must go through to reach its destination.