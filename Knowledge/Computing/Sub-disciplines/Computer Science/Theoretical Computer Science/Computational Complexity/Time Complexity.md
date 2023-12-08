# Time Complexity
In [[Computer Science|computer science]], the **time complexity** is the [[Computational Complexity|computational complexity]] that describes the amount of computer time it takes to run an [[Algorithm | algorithm]].

> Time complexity is commonly estimated by counting the number of elementary operations performed by the algorithm, supposing that each elementary operation takes a fixed amount of time to perform.

Thus, the amount of time taken and the number of elementary operations performed by the algorithm are taken to be related by a *constant factor*.

## Complexity Classes
| Name                    | Running Time (T(n))        | [[Complexity Class]] |
| ----------------------- | -------------------------- | -------------------- |
| constant time           | $O(1)$                     |                      |
| ...                     | ...                        | ...                  |
| log-logarithmic time    | $O(\log{\log{n}})$         |                      |
| logarithmic time        | $O(\log{n})$               | DLOGTIME or NLOGTIME |
| polylogarithmic time    | $poly(\log{n})$            |                      |
| fractional power        | $O(n^c)$ where $0 < c < 1$ |                      |
| linear time             | $O(n)$                     |                      |
| linearithmic time       | $O(n\log{n})$              |                      |
| quadratic time          | $O(n^2)$                   |                      |
| cubic time              | $O(n^3)$                   |                      |
| polynomial time         | $2^{O(\log{n})}$           | P or NP              |
| quasipolynomial time    | $2^{poly(\log{n})}$        | QP or NQP            |
| ...                     | ...                        | ...                  |
| exponential time        | $2^{O(n)}$                 | EXPTIME or NEXPTIME  |
| factorial time          | $O(n!)$                    |                      |
| double exponential time | $2^{2^{poly(n)}}$          | 2-EXPTIME            | 