# Graph
A **graph** is an [[Data Type#^AbstractDataTypes | abstract data type (ADT)]] that is meant to implement the undirected graph and directed graph concepts from the field of [[Graph theory | graph theory]] within [[Mathematics | mathematics]].

## Structure
A graph data structure consists of 
- V - a finite (and possibly mutable) set of vertices (also called *nodes* or *points*)
- E - a set of edges

#### Weighted graph
A _weighted graph_ or a _network_ is a graph in which a number (the weight) is assigned to each edge. Such weights might represent for example costs, lengths or capacities, depending on the problem at hand. Such graphs arise in many contexts, for example in [[Shortest Path Problems]] such as the [[Travelling Salesman Problem]].

## Basic Operations on Graphs
Below are the basic operations on the graph:
- Insertion of Nodes/Edges in the graph – Insert a node into the graph.
- Deletion of Nodes/Edges in the graph – Delete a node from the graph.
- Searching on Graphs – Search an entity in the graph.
- [[Graph Traversal|Traversal of Graphs]] – Traversing all the nodes in the graph.

## Representation
- [[Adjacency list]]
Vertices are stored as records or objects, and every vertex stores a list of adjacent vertices. This data structure allows the storage of additional data on the vertices. Additional data can be stored if edges are also stored as objects, in which case each vertex stores its incident edges and each edge stores its incident vertices.

- [[Adjacency matrix]]
A two-dimensional matrix, in which the rows represent source vertices and columns represent destination vertices. Data on edges and vertices must be stored externally. Only the cost for one edge can be stored between each pair of vertices.

- [[Incidence matrix]]
A two-dimensional matrix, in which the rows represent the vertices and columns represent the edges. The entries indicate the incidence relation between the vertex at a row and edge at a column.

## Types Of Graph
- *Null Graph* is known as a null graph if there are no edges in the graph.
- *Trivial Graph* having only a single vertex, it is also the smallest graph possible.
- **[[Undirected Graph]]** is graph in which edges do not have any direction. 
- **[[Directed Graph]]** or **digraph** is a graph in which edges have orientations.
- Connected graph
*In an undirected graph*, an unordered pair of vertices *{x, y}* is called *connected* if a path leads from *x* to *y*. Otherwise, the unordered pair is called disconnected.
*In a directed graph*, an ordered pair of vertices (_x_, _y_) is called _strongly connected_ if a directed path leads from _x_ to _y_. Otherwise, the ordered pair is called _weakly connected_ if an undirected path leads from _x_ to _y_ after replacing all of its directed edges with undirected edges. Otherwise, the ordered pair is called _disconnected_.
- **Regular graph** is a graph in which each vertex has the same number of neighbours, i.e., every vertex has the same degree. A regular graph with vertices of degree _k_ is called a _k_‑regular graph or regular graph of degree _k_.
- **Complete graph** is a graph in which each pair of vertices is joined by an edge. A complete graph contains all possible edges.
- **Cycle graph** or _circular graph_ of order _n_ ≥ 3 is a graph in which the vertices can be listed in an order $${v_1,v_2,…,v_n}$$ such that the edges are the $${\{v_i,v_{i+1}\}}$$ where i = 1, 2, …, n − 1, plus the edge $${\{v_n, v_1\}}$$ Cycle graphs can be characterized as connected graphs in which the degree of all vertices is 2. If a cycle graph occurs as a subgraph of another graph, it is a cycle or circuit in that graph.
- **[[Weighted Graph]]** or a *network* is a graph in which a number (the weight) is assigned to each edge. Such weights might represent for example costs, lengths or capacities, depending on the problem at hand. 
- **[[Planar graph]]** is a graph whose vertices and edges can be drawn in a plane such that no two of the edges intersect.
- **[[Tree]]** is an undirected graph in which any two vertices are connected by *exactly one* path, or equivalently a connected acyclic undirected graph.