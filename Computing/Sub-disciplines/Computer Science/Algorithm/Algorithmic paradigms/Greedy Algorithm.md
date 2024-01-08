# Greedy Algorithm
Greedy is an [[Algorithm#^designparadigm | algorithmic paradigm]] that follows the problem-solving heuristic of making the locally optimal choice at each stage. In other words, ==a greedy algorithm is an approach for solving a problem by selecting the best option available at the moment==. It doesn't worry whether the current best result will bring the overall optimal result.

Greedy algorithms produce good solutions on some [[Mathematical Problems | mathematical problems]], but not on others. Most problems for which they work will have two properties:

**1. Greedy Choice Property**
If an optimal solution to the problem can be found by choosing the best choice at each step without reconsidering the previous steps once chosen, the problem can be solved using a greedy approach.

**2. Optimal Substructure**
If the optimal overall solution to the problem corresponds to the optimal solution to its subproblems, then the problem can be solved using a greedy approach.

## Greedy Algorithms
- [[Dijkstra's Algorithm]]
- [[Kruskal Algorithm]]
- [[Prim's Algorithm]]

## Pros and Cons
**Advantages of Greedy Approach**
- The algorithm is **easier to describe**.
- This algorithm can **perform better** than other algorithms (but, not in all cases).

**Drawback of Greedy Approach**
- doesn't always produce optimal solution