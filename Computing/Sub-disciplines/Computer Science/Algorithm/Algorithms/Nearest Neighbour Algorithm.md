# Nearest Neighbour Algorithm
The **nearest neighbour algorithm** is the first [[Algorithm | algorithm]] that solve the [[Travelling Salesman Problem]] approximately. 

## Algorithm
These are the steps of the algorithm:
1.  Initialize all vertices as unvisited.
2.  Select an arbitrary vertex, set it as the current vertex **u**. Mark **u** as visited.
3.  Find out the shortest edge connecting the current vertex **u** and an unvisited vertex **v**.
4.  Set **v** as the current vertex **u**. Mark **v** as visited.
5.  If all the vertices in the domain are visited, then terminate. Else, go to step 3.
The sequence of the visited vertices is the output of the algorithm.

The *nearest neighbour algorithm* is easy to implement and executes quickly, but it can sometimes miss shorter routes which are easily noticed with human insight, due to its "greedy" nature. As a general guide, if the last few stages of the tour are comparable in length to the first stages, then the tour is reasonable; if they are much greater, then it is likely that much better tours exist. Another check is to use an algorithm such as the [lower bound](https://en.wikipedia.org/wiki/Upper_and_lower_bounds "Upper and lower bounds") algorithm to estimate if this tour is good enough.

In the worst case, the algorithm results in a tour that is much longer than the optimal tour. To be precise, for every constant **r** there is an instance of the travelling salesman problem such that the length of the tour computed by the nearest neighbour algorithm is greater than **r** times the length of the optimal tour. Moreover, for each number of cities there is an assignment of distances between the cities for which the nearest neighbor heuristic produces the unique worst possible tour. 

The nearest neighbour algorithm may not find a feasible tour at all, even when one exists.