# Master's Theorem 
In the [[Analysis of Algorithms]], the **master theorem for divide-and-conquer recurrences** provides an [[asymptotic analysis]] (using [[Computational Complexity Theory#^BigOh | Big O notation]]) for [[Recurrence Relation | recurrence relations]] of types that occur in the analysis of many [[Divide and Conquer | divide and conquer algorithms]].

## For Decreasing Function
General form
$${T(n) = aT(n-b) + f(n)}$$
where,
n = size of input
a = number of subproblems in the recursion
b = cost of decreasing
f(n) = cost of the work done outside the recursive call, 
${a > 0}$, ${b > 0}$, and ${f(n) = \theta(n^k)}$, ${k ≥ 0}$
1.  ${a = 1}$ , ${O(n*f(n))}$
2. ${a > 1}$, ${O(n^ka^\frac{n}{b})}$
3. ${a<1}$, ${O(n^k)}$

## For Dividing Function
General form
$${T(n) = aT(\frac{n}{b}) + f(n)}$$
where,
n = size of input
a = number of subproblems in the recursion
n/b = size of each subproblem. All subproblems are assumed 
     to have the same size.
f(n) = cost of the work done outside the recursive call, 
      which includes the cost of dividing the problem and
      cost of merging the solutions
${a ≥ 1}$, ${b > 1}$ and ${f(n) = \theta(n^k\log^p{n})}$
1. If ${a>b^k}$, then ${T(n)=\theta(n^{\log_{b}{a}})}$
2. If ${a=b^k}$
	1. If ${p>-1}$, then ${T(n)=\theta(n^{\log_{b}{a}}\log^{p+1}{n})}$
	2. If ${p=-1}$, then ${T(n)=\theta(n^{\log_{b}{a}}\log{\log{n}})}$
	3. If ${p<-1}$, then ${T(n)=\theta(n^{\log_{b}{a}})}$
3. If ${a<b^k}$
	1. If ${p ≥ 0}$, then ${T(n)=\theta(n^k\log^pn)}$
	2. If ${p < 0}$, then ${T(n)=O(n^k)}$


