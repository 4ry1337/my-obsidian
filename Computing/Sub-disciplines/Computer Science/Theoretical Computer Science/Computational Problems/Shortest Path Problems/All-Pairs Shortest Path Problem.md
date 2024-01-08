# All-Pairs Shortest Path Problem
## Problem Definition
> Given a graph ${G}$, with vertices ${V}$, edges ${E}$ with weight function ${w(u, v) = w_{u, v}}$ return the shortest path from ${u}$ to ${v}$ for all ${(u, v)}$ in ${V}$.

The most common algorithm for the all-pairs problem is the [[Floyd–Warshall algorithm | floyd-warshall algorithm]]. This algorithm returns a matrix of values ${D}$, where each cell ${D_{i, j}}$ is the distance of the shortest path from vertex ${i}$ to vertex ${j}$.
Path reconstruction is possible to find the actual path taken to achieve that shortest path, but it is not part of the fundamental algorithm.
