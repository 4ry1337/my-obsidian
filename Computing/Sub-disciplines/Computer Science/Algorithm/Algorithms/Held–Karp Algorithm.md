# Held–Karp Algorithm
The **Held–Karp algorithm**, also called **Bellman–Held–Karp algorithm**, is a [[Dynamic Programming | dynamic programming]] algorithm proposed in 1962 independently by Bellman and by Held and Karp to solve the [[Travelling Salesman Problem|travelling salesman problem]] (TSP). It finds the exact solution to this problem, and to several related problems including the [[Hamiltonian Cycle Problem|Hamiltonian cycle problem]], in exponential time.

## Derivation
Suppose ${S=\{s_{1},\ldots ,s_{k}\}}$ is a set of ${k}$ cities. For every integer ${1\leq i\leq k}$, write ${S_{i}= S \setminus \{s_{i}\}=\{s_{1},\ldots ,s_{i-1},s_{i+1},\ldots ,s_{k}\}}$ for the *set created by removing ${s_{i}}$ from ${S}$*. 
Then if the shortest path from ${1}$ through ${S}$ to ${e}$ has ${s_{i}}$ as its second-to-last city, then removing the final edge from this path must give the shortest path from ${1}$ to ${s_{i}}$ through ${S_{i}}$. This means there are only ${k}$ possible shortest paths from ${1}$ to ${e}$ through ${S}$, one for each possible second-to-last city ${s_{i}}$ with length ${g(S_{i},s_{i})+d(s_{i},e)}$, and ${g(S,e)=\min _{1\leq i\leq k}g(S_{i},s_{i})+d(s_{i},e)}$.

## Complexity
**[[Time Complexity]]:** ${\Theta (2^{n}n^{2})}$
**[[Space Complexity]]:** ${\Theta (n2^{n})}$

## Pseudocode
```java
function algorithm TSP (G, n) is
    for k := 2 to n do
        g({k}, k) := d(1, k)
    end for

    for s := 2 to n−1 do
        for all S ⊆ {2, ..., n}, |S| = s do
            for all k ∈ S do
                g(S, k) := min{g(S\{k}, m) + d(m, k)}
            end for
        end for
    end for

    opt := min{g({2, 3, ..., n}, k) + d(k, 1)}
    return (opt)
end function
```