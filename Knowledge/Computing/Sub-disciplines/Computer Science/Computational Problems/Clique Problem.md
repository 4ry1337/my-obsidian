# Clique Problem
In [[Computer Science|computer science]], the **clique problem** is the [[Computational Problems|computational problem]] of finding cliques in a [[Graph|graph]].

Clique -  a subset of vertices of an undirected graph such that every two distinct vertices in the clique are adjacent (Subgraph is complete graph).

## Definitions
An undirected graph is formed by a finite set of vertices and a set of unordered pairs of vertices, which are called edges.

By convention, in [[Analysis of Algorithms|algorithm analysis]], the number of *vertices* in the graph is denoted by ${n}$ and the number of *edges* is denoted by ${m}$.
A clique in a graph G is a complete subgraph of G.

> A *maximal clique* is a clique to which no more vertices can be added. For each vertex v that is not part of a maximal clique, there must be another vertex w that is in the clique and non-adjacent to v, preventing v from being added to the clique.

> A *maximum clique* is a clique that includes the largest possible number of vertices. The clique number ${\omega(G)}$ is the number of vertices in a maximum clique of G.

# Types of problem:
- In the *maximum clique problem*, the input is an undirected graph, and the output is a maximum clique in the graph. If there are multiple maximum cliques, one of them may be chosen arbitrarily.
- In the *weighted maximum clique problem*, the input is an undirected graph with weights on its vertices (or, less frequently, edges) and the output is a clique with maximum total weight. The maximum clique problem is the special case in which all weights are equal. As well as the problem of optimizing the sum of weights, other more complicated bicriterion optimization problems have also been studied.
- In the *maximal clique listing problem*, the input is an undirected graph, and the output is a list of all its maximal cliques. The maximum clique problem may be solved using as a subroutine an algorithm for the maximal clique listing problem, because the maximum clique must be included among all the maximal cliques.
- In the *k-clique problem*, the input is an undirected graph and a number k. The output is a clique with k vertices, if one exists, or a special value indicating that there is no k-clique otherwise. In some variations of this problem, the output should list all cliques of size k.
- In the *[[Clique Decision Problem|clique decision problem]]*, the input is an undirected graph and a number k, and the output is a Boolean value: true if the graph contains a k-clique, and false otherwise.