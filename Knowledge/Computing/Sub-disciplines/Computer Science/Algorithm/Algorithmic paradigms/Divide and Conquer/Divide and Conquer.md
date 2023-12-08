# Divide and Conquer
In [[Computer Science]], **divide and conquer** is an [[Algorithm#By design paradigm| algorithm design paradigm]]. A divide-and-conquer [[Algorithm| algorithm]] [[recursively]] breaks down a problem into two or more sub-problems of the same or related type, until these become simple enough to be solved directly. The solutions to the sub-problems are then combined to give a solution to the original problem.

The divide-and-conquer paradigm is often used to find an optimal solution of a problem. Its basic idea is to decompose a given problem into two or more similar, but simpler, subproblems, to solve them in turn, and to compose their solutions to solve the given problem. Problems of sufficient simplicity are solved directly.

1. **Divide:** This involves dividing the problem into smaller sub-problems.
2. **Conquer:** Solve sub-problems by calling recursively until solved.
3. **Combine:** Combine the sub-problems to get the final solution of the whole problem.

## Divide and Conquer algorithms:
- [[Quick Sort]]
- [[Merge Sort]]
- [[Closeset Pair of Points]]
- [[Stressen's Algorithm]]
- [[Karatsuba algorithm for fast maltiplication]]

## [[Time Complexity]] 
```
T(n) = aT(n/b) + f(n),
    
    where,
        n = size of input
        a = number of subproblems in the recursion
        n/b = size of each subproblem. All subproblems are assumed to have the same size.
        f(n) = cost of the work done outside the recursive call, which includes the cost of dividing the problem and cost of merging the solutions
```

## Pros and Cons
**Advantages of Divide and Conquer Algorithm:**
- The difficult problem can be solved easily.
- It divides the entire problem into subproblems thus it can be solved parallelly ensuring multiprocessing
- Efficiently uses cache memory without occupying much space
- Reduces time complexity of the problem

**Disadvantages of Divide and Conquer Algorithm:**
- It involves recursion which is sometimes slow
- Efficiency depends on the implementation of logic
- It may crash the system if the recursion is performed rigorously