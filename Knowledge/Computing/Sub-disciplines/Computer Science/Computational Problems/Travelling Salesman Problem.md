# Travelling Salesman Problem
The **travelling salesman problem** (also called the **travelling salesperson problem** or **TSP**) is an [[NP-hardness|NP-hard]] problem in combinatorial optimization, important in [[Theoretical Computer Science | theoretical computer science]] and operations research.

## Problem Definition
Given a list of cities and the distances between each pair of cities, what is the shortest possible route that visits each city exactly once and returns to the origin city?

## Solution
### [[Brute-Force Search]] / Naive Solution
1) Consider city 1 as the starting and ending point.
2) Generate all (n-1)! Permutations of cities. 
3) Calculate the cost of every permutation and keep track of the minimum cost permutation.
4) Return the permutation with minimum cost. 

**[[Time Complexity]]**: Θ(n!)
### [[Dynamic Programming]]
One of the earliest applications of dynamic programming is the [[Held–Karp Algorithm]] that solves the problem in time ${O(n^{2}2^{n})}$ This bound has also been reached by Exclusion-Inclusion in an attempt preceding the dynamic programming approach.
### [[Greedy Algorithm]]
The [[Nearest Neighbour Algorithm|nearest neighbour (NN) algorithm]] lets the salesman choose the nearest unvisited city as his next move. This algorithm quickly yields an effectively short route. For N cities randomly distributed on a plane, the algorithm on average yields a path 25% longer than the shortest possible path.