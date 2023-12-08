# Longest Common Subsequence Problem
The **longest common subsequence** (**LCS**) **problem** is the problem of finding the longest subsequence common to all sequences in a set of sequences (often just two sequences). It differs from the [[Longest Common Substring Problem]]: unlike substrings, subsequences are not required to occupy consecutive positions within the original sequences.

## Problem Definition for two sequences 
Given two sequences, find the length of longest subsequence present in both of them. A subsequence is a sequence that appears in the same relative order, but not necessarily contiguous.

## Solution for two sequences
### [[Brute-Force Search]]
Enumerate all the ${2^n}$ subsequences of A, and for each subsequence, determine if it is also a subsequence of B in ${\theta(m)}$ time. Clearly, the running time of this algorithm is ${\theta(m2^n)}$, which is exponential.
### [[Dynamic Programming]]
**LCS has**
1) [[Dynamic Programming#^OptimalSubstructure | optimal structure]]: the problem can be broken down into trivial subproblems.
2) [[Dynamic Programming#^OverlappingSubproblems| Overlapping subproblems]]: the solutions to high-level subproblems often reuse the solutions of lower-level subproblems.
Then problem is amenable to [[Dynamic Programming]] approaches, i.e. memorization method.

Let LCS(X , Y) be a function that computes a longest subsequence common to X and Y. Such function has two properties.
1) LCS(X^A), Y^A)) = LCS(X, Y)^A, for all strings X, Y and symbols A, where `^` denotes string concatenation. This allows one to simplfy the LCS computation for two sequences ending in the same symbol.
2) If A and B are distinct symbols (${A \ne B}$), then LCS(X^A, Y^B) is one of the maximal-length strings in the set {LCS(X^A, Y), LCS(X, Y^B)}, for all strings X, Y.

**LCS function defined**
Let two sequences be defined as follows: ${X = (x_1x_2...x_m)}$ and ${Y = (y_1y_2...y_n)}$.
The [[Prefixes | prefixes]] of X are ${X_0, X_1, X_2, ..., X_m}$,
the prefixes of Y are ${Y_0, Y_1, Y_2, ..., Y_n}$.
Let ${LCS(X_i, Y_j)}$ represent the set of longest common subsequence of prefixes ${X_i}$ and ${Y_j}$.
$${\mathit{LCS}(X_i,Y_j)=
\begin{cases} 0 & \mbox{if }i=0\mbox{ or }j=0 \\
\mathit{LCS}(X_{i-1},Y_{j-1}) \hat{} x_i & \mbox{if }i,j>0\mbox{ and }x_i=y_j \\
\operatorname{\max}\{\mathit{LCS}(X_i,Y_{j-1}),\mathit{LCS}(X_{i-1},Y_j)\} & \mbox{if }i,j>0\mbox{ and }x_i\ne y_j.
\end{cases}}$$

To find the LCS of ${X_{i}}$ and ${Y_j}$, compare ${x_i}$ and ${y_j}$. If they are equal, then the sequence ${\mathit {LCS}(X_{i-1},Y_{j-1})}$ is extended by that element, ${x_i}$. If they are not equal, then the longest among the two sequences, ${\mathit {LCS}(X_i,Y_{j-1})}$, and ${\mathit{LCS}(X_{i-1},Y_j)}$, is retained. (If they are the same length, but not identical, then both are retained.)

An Table[n+1, m+1] is used to compute ${\mathit{LCS}(X_i,Y_i)}$ for each pair of values ${i}$ and ${j}$, ${0 \leqslant i \leqslant n}$ and ${0 \leqslant j \leqslant m}$. Table is filled row by row using above function.

#### [[Pseudocode]]
```java
method LCSLength(X[1..m], Y[1..n])
    C[0..m, 0..n] // 2d array
    for i := 0 to m do
        C[i,0] = 0
    for j := 0 to n do
        C[0,j] = 0
    for i := 1 to m do
        for j := 1 to n do
            if X[i] = Y[j]
                C[i,j] := C[i-1,j-1] + 1
            else
                C[i,j] := max(C[i,j-1], C[i-1,j])
    return C[m,n]
```

#### Running Time
[[Time Complexity]]: ${\theta(nm)}$ as filling each entry requires ${\theta(1)}$
[[Space Complexity]]: ${\theta(nm)}$