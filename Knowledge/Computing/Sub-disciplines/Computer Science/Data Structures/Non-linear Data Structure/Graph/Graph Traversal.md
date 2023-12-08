# Graph Traversal
A **graph traversal** (also known as **graph search**) refers to the process of visiting (checking and/or updating) each vertex in a [[Graph|graph]].

**Keep track of vertexes**
Since each node can have many neighbours and because the graph can have cycles, it is essential to have a method to keep track of where you have been and where you have yet to go. There are three states for each node:
- *Unvisited* – the node has not yet been encountered
- *Discovered* – the node has been encountered (partially explored) but will need to be returned to
- *Visited* – the node has been fully explored and does not need to be returned to again
As the traversal progresses, the state of each node will change.

There are two graph traversal techniques:
- [[Depth-First Search]]
- [[Breadth-First Search]]