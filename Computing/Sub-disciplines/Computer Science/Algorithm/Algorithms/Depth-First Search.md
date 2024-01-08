# Depth-First Search
**Depth-first search** (**DFS**) is an [[Algorithm]] for [[Graph Traversal|traversing or searching]] [[Tree|tree]] or [[Graph|graph]] data structures.

The algorithm starts at the root node/arbitrary node and explores as far as possible along each branch before backtracking. Extra memory, usually a *stack*, is needed to *keep track of the nodes discovered* so far along a specified branch which helps in backtracking of the graph.

## Output of a depth-first search
The result of a depth-first search of a graph can be conveniently described in terms of a spanning tree of the vertices reached during the search.

Based on this spanning tree, the edges of the original graph can be divided into *three classes*:
- **Forward edges**, which point from a node of the tree to one of its descendants.
- **Back edges**, which point from a node to one of its ancestors.
- **Cross edges**, which do neither.
- **Tree edges**, edges which belong to the spanning tree itself, are classified separately from forward edges.
If the original graph is undirected then all of its edges are tree edges or back edges.
![[Edges.png]]

### Vertex orderings
It is also possible to use depth-first search to linearly order the vertices of a graph or tree. There are four possible ways of doing this:
- A **preordering** is a list of the vertices in the order that they were first visited by the depth-first search algorithm. This is a compact and natural way of describing the progress of the search, as was done earlier in this article. A preordering of an expression tree is the expression in Polish notation.
- A **postordering** is a list of the vertices in the order that they were _last_ visited by the algorithm. A postordering of an expression tree is the expression in reverse Polish notation.
- A **reverse preordering** is the reverse of a preordering, i.e. a list of the vertices in the opposite order of their first visit. Reverse preordering is not the same as postordering.
- A **reverse postordering** is the reverse of a postordering, i.e. a list of the vertices in the opposite order of their last visit. Reverse postordering is not the same as preordering.

For binary trees there is additionally **in-ordering** and **reverse in-ordering**



## [[Pseudocode]]
- *Input*: A graph ${G}$ and a vertex ${v}$ of ${G}$.
- *Output*: A labeling of the edges in the connected component of ${v}$ as discovery edges and back edges.
```java
method DFS(G, v) is
    label v as explored
    for all edges e in G.incidentEdges(v) do
        if edge e is unexplored then
            w ← G.adjacentVertex(v, e)
            if vertex w is unexplored then
                label e as a discovered edge
                recursively call DFS(G, w)
            else
               label e as a back edge
```
## Complexity
**Time Complexity:** ${O(V + E)}$, where ${V}$ is the number of nodes and ${E}$ is the number of edges.
**Space Complexity:** `O(V)`.

## Applications
- Finding connected components.
- [[Topological Sorting|Topological sorting]].
- Finding 2-(edge or vertex)-connected components.
- Finding 3-(edge or vertex)-connected components.
- Finding the bridges of a graph.
- Generating words in order to plot the limit set of a group.
- Finding strongly connected components.
- Determining whether a species is closer to one species or another in a phylogenetic tree.
- Planarity testing.
- Solving puzzles with only one solution, such as mazes.
- Maze generation may use a randomized DFS.
- Finding biconnectivity in graphs.
- Succession to the throne shared by the Commonwealth realms.