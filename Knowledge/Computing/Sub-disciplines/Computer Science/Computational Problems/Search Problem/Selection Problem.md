# Selection Problem

## Problem Deifinition
Given  an list L containing n keys, find *k*th smallest (or largest) key in L (1 < i < n).

### Different cases:
- If *i*=1, find smallest key
- If *i*=2, find second smallest key
- By **median**,
$${n= \begin{cases} \frac{n+1}{2} \hspace{1 cm} \text{ if n is odd }\\ \frac{\lfloor n+1 \rfloor}{2} \hspace{1 cm} \text{ if n is even }\end{cases} }$$
- If *i*=n, find the largest key

## Solution 
Solution consist of two steps:
- [[Sorting Algorithms | Sort]] the sequence
- Choose *k*th element from the sorted sequence
### Straightforward way
#### Finding smallest/largest in sorted list
```
method MinNum(A[...])
	min := A[1]
	for i := 2 to n do
		if(min>A[i])
			min := A[i]
	end for
	return min
```
**[[Time Complexity]]:** ${n-1}$ - exact running time, not asymptotic.

#### Finding smallest/largest in sorted list
```
method MinAndMaxNum(A[...])
	min := A[1]
	max := A[1]
	for i := 2 to n do
		if(min>A[i])
			min := A[i]
		if(max<A[i])
			max := A[i]
	end for
	return min, max;
```
**[[Time Complexity]]:** ${2(n-1)}$ - exact running time, not asymptotic.

### Better Way
- Pair the keys and find the minimum and maximum in each pair
- Find minimum among minima of each pair
- Find maximum among maxima of each pair
```java
method BetterMinAndMax(A[...])
	if n is odd
		k := 2
		min := A[1]
		max := A[1]
	else
		k := 3
		if A[1] < A[2]
			min := A[1]
			max := A[2]
		else
			min := A[2]
			max := A[1]
	for i := k to n-1 by 2 do
		if A[i] > A[i + 1]
			swap A[i] and A[i+1]
		else if A[i] < min
			min := A[i]
		else if A[i] > max
			max := A[i]
```

### Straightforward vs Better
Using *straightforward method* number of comparison for pair of elements is 4, while in *better way*, number of comparisons is reduced to 3.

### [[Divide and Conquer]]
- *Divide*: split input list recursively
- *Conquer*: recursively solve **one** sub-problem
- *Combine*: no need to combine

```java
method Select(A[p...r], p, r, i)
	if(p == r) return
	q := PartitionA(A) //divide A[p...r] to two sub lists A1[p...q] and A2[q...r] 
	k := q-p+1 //size of A1
	if(i == k)
		return A[q]
	else if i < k 
		return Select(A, p, q-1, i)
	else
		return Select(A, q+1, r, i-k)
```
But, if the partition divides list into 2 sub-lists, the worst case always results in 0 and n-1 elements in sub-lists. then we need to find a split element q such that ${\alpha}$ fraction of elements is always eliminated.
$${T(n)\leqslant T(1-\alpha)} + \theta(n) $$
then ${T(n)=\theta(n)}$

### Select with Linear Time in the worst-case
1. Divide *A* into *q* groups of *5* elements each. ${q = \lfloor \frac{n}{5} \rfloor}$
2. Sort each of the *q* groups individually and extract its median. Let the set of medians be *M*.
3. mm := select(M, ${\lceil \frac{q}{2} \rceil}$) mm- median of medians
4. Partition A into three lists
	- ${A_1}$ = {a | a < mm}
	- ${A_2}$ = {a | a = mm}
	- ${A_3}$ = {a | a > mm}
5. case
	- ${|A_1| \geqslant k}$ return *select(${A_1}$, k)*
	- ${|A_1| + |A_2| \geqslant k}$ return *mm*
	- ${|A_1| + |A_2| < k}$ return *select(${A_3}$, ${k - |A_1| - |A_2|}$)*
#### Enhance the select algorithm
By executing some pre-steps, if number of elements of *A* is less than predefined threshold *44* use straightforward method. Since it is faster.

### Quick Select
Quick-Select of the *k*th smallest/largest element is the list L is based on [[Prune and Search]] paradigm
- Prune: pick random element x (pivot) from L, instead of *mm*
	- Partition A into three lists
	- ${A_1}$ = {a | a < x}
	- ${A_2}$ = {a | a = x}
	- ${A_3}$ = {a | a > x}
- Search 
	- ${|A_1| \geqslant k}$ return *quickSelect(${A_1}$, x)*
	- ${|A_1| + |A_2| \geqslant k}$ return *x*
	- ${|A_1| + |A_2| < k}$ return *select(${A_3}$, ${x - |A_1| - |A_2|}$)*

#### Running Time
Worst case: ${O(N^2)}$ - if the pivot is always the minimal or maximal element
Expected running time: ${O(N)}$ by [[Master's Theorem]]