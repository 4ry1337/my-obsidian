# Topological Sorting
In [[Computer Science|computer science]], a **topological sort** or **topological ordering** of a directed graph is a linear ordering of its vertices such that for every directed edge ${uv}$ from vertex ${u}$ to vertex ${v}$, ${u}$ comes before ${v}$ in the ordering.

A **topological sort** is a [[Graph Traversal|graph traversal]] in which each node ${v}$ is visited only after all its dependencies are visited. A topological ordering is possible if and only if the graph is a *directed acyclic graph* (DAG).
A **directed acyclic graph** (**DAG**) is a directed graph with no directed cycles.

## [[Pseudocode]]
```java
function topsort (graph):
	N = graph.numberOfNodes()
	V = [false, .. , false] //Length N
	ordering = [0,.,0] //Length N
	i = N -1 // Index for ordering array
	
	for at := 0 to N do 
		if V[at] == false:
		visitedNodes := []
		dfs(at, V, visitedNodes, graph)
		for nodeId in visitedNodes do
			ordering [i] = nodeId
			i = i - 1
	return ordering

function dfs(at, V, visitedNodes, graph) :
	V[at] = true
	edges = graph.getEdges0utFromNode(at)
	for edge in edges do
		if V[edge.to] == false:
		dfs(edge.to, V, visitedNodes, graph)
	visitedNodes.add(at)
```



