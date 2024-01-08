# Matrix Chain Multiplication
**Matrix chain multiplication** (or the **matrix chain ordering problem**) is an [[Optimization Problem | optimization problem]] concerning the most efficient way to multiply a given sequence of matrices. The problem is not actually to *perform* the multiplications, but merely to decide the sequence of the matrix multiplications involved.

> Matrix multiplication is associative

> Two matrices are called *compatible* only if the number of columns in the first matrix and the number of rows in the second matrix are the same

## Cost of chain multiplication
For Example: ${M_1(2, 10), M_2(10, 2), M_3(2, 3)}$. Depending on order of multiplication: ${(M_1M_2)M_3}$ the number of scalar multiplications is ${2*10*2 + 2*2*3 = 52}$, ${M_1(M_2M_3)}$ the number of scalar multiplications is ${10*2*3 + 2*10*3 = 120}$. Thus, carrying out the multiplication on ${(M_1M_2)M_3}$ is faster than ${M_1(M_2M_3)}$.

## Problem Definition
Given n matrices ${A_1, A_2, A_3, …, A_n}$,  in what order matrixes should be multiplied so that it would take a minimum number of computations to derive the result.

## Solution using [[Dynamic Programming]]
The *cost of multiplying a chain of n matrices* ${M_1M_2...M_n}$
depends on the *order* in which the n-1 multiplications are carried out. That order which minimizes the number of scalar multiplications can be found in many ways. The *number of orderings* is equal to the *number of ways to place parentheses* to multiply the n matrices in every possible way.

Let p(n) be the number of ways to fully parenthesize a product of n matrices.
- When n = 1, there is only one matrix and therefore only one way to parenthesize the matrix.
- When n ≥2, a full parenthesized matrix product is the product of two fully parenthesized matrix sub-products, and the split between the two sub-products may occur between the k and k+1 matrices for any k = 1, 2, 3..., n-1.
$${(M_1M_2...M_k)*(M_{k+1}M_{k+2}...M_n)}$$
Thus
$${p(n) = \begin{cases} 1 & \mbox{if n=1} \\
\sum_{k=1}^{n-1}p(k)p(n-k) & \mbox{if n} \geqslant \mbox{2}\end{cases}}$$
Solving the recurrence relation 
$${f(n)=\frac{1}{n}\binom{n-2}{n-1}}$$
gives the sequence of **Catalan Numbers** by
$${\mathit{C_n}=\mathit{f}(n+1)}$$
Using Stirling's formula
$${n!\approx\sqrt{2 \pi n}(\frac{n}{e})^n}$$ where e = 2.71828...
Then
$${f(n)=\frac{1}{n}\binom{n-2}{n-1}=\frac{(2n-2)!}{n((n-1)!)^2} \approx \frac{4^n}{4\sqrt{\pi}n^{1.5}}}$$
Thus 
$${f(n)=\Omega(\frac{4^n}{n^{1.5}})}$$

Any parenthesizations of the product ${M_iM_{i+1}…M_j}$ must split the product between ${M_k}$ and ${M_{k+1}}$ for some integer k in the range i ≤ k < j. That is for some value of k, we first compute the matrices ${M_i…M_k}$ and ${M_{k+1}…M_j}$ and then multiply them together to produce the final product ${M_i…M_j}$  The cost of computing these parenthesizations is the cost of computing ${M_i…M_k}$ , plus the cost of computing ${M_{k+1}…M_j}$ plus the cost of multiplying them together.

Let the cost of multiplication of chain ${M_i…M_j}$ denoted by C\[i, j\]. is measured in terms of the number of scalar multiplications.

**Optimal Structure** is defined as:
$${\mathit{C[i, j]}=
\begin{cases} 0 & \mbox{if } i=j \\
\mathit{\min\limits_{1 < k \leqslant j}}{C[i,k-1]+C[k,j]+r_ir_kr_{j+1}} & \mbox{if } i<j 
\end{cases}}$$
where r = ${r_0,r_1,r_2,...,r_n}$ is the vector of matrix dimensions

### Recursive Solution
1. Create a recursive function C where C\[i, j\] returns the minimum number of operations for multiplying chain of matrices from i to j.
2. For each i and j, find k between i and j with the minimum cost of multiplication.
```Java
method C(p[1...n], int i, int j)
	if(i==j) then
		return 0
    min := MAXINT;
    for k := i to j do
	    cost := C[p, i, k] + C[p, k+1, j] + r[i-1]*r[k]*r[j];
            if cost < min then
                min = cost;
    endfor
	return min
method MatrixChain(p) // p is sequence of n matrices
{
    return C(p, 1, length(p)-1)
}
```
**[[Time Complexity]]:** ${O(2^n)}$
**[[Space Complexity]]:** ${O(n)}$
### Dynamic Programming by Memorization
In dynamic programming approach, use table, where diagonal d is used to store minimum costs of multiplying various chains of d+1 consecutive matrices.

| d0      | ${M_1}$   | ${M_2}$   | ${M_3}$   | ... | ${M_n}$   |
| ------- | --------- | --------- | --------- | --- | --------- |
| ${M_1}$ | C\[1, 1\] | C\[1, 2\] | C\[1, 3\] | ... | C\[1, n\] |
| ${M_2}$ |           | C\[2,2\]  | C\[2, 3\] | ... | C\[2,n\]  |
| ${M_3}$ |           |           | C\[3, 3\] | ... | C\[3,n\]  |
| ...     |           |           |           | ... | ...       |
| ${M_n}$ |           |           |           |     | C\[n, n\] |

In diagonal 0, each chain consists of one matrix only, and hence this diagonal is filled with 0's, since no scalar multiplication is involved. The rest of the diagonals are filled using the formula started above and the values previously stored in the table. Specifically, to find diagonal d, we make use of the values stored in diagonals 0, 1, 2, ..., d-1.
```Java
method MatrixChain(p) // p is sequence of n matrices
{
    n := length(p) - 1; 
    C := A[1...n][1...n]
    for i := 1 to n do //fill in the diagonal r_0
        C[i, i] := 0;
    end
    for d := 1 to n do // Fill in diagonals r_1 to r_(n-1)
        for i := 1 to n-d do //fill in entries in diagonal r_i
            j = i + d;
            // the next three lines compute C[i, j]
            C[i, j] = MAXINT;
            for k := i+1 to j do
                C[i, j] = C[i, k] + C[k+1, j] + r[i]*r[k+1]*r[j+1]; //cost
                S[i, j] = k; // Index of the subsequence split that achieved minimal cost(where to put parenthesis)
    return C[1, n]
}
```
**[[Time Complexity]]:** ${O(n^3)}$
**[[Space Complexity]]:** ${O(n^2)}$
Moreover, we can use second table S\[1..n\]\[1...n\] to store the indexes of matrices after which to put parenthesis. 