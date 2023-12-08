**Binary Search** is a [[Search Algorithms| search algorithm]] used in a sorted array by **repeatedly dividing the search interval in half**. The idea of binary search is to use the information that the array is sorted and reduce the [[Time Complexity]] to O(Log n).

## Basic Algorithm
- Begin with the mid element of the whole array as a search key.
- If the value of the search key is equal to the item then return an index of the search key.
- Or if the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half.
- Otherwise, narrow it to the upper half.
- Repeatedly check from the second point until the value is found or the interval is empty.

**Complexity:**
- **[[Time Complexity]]:** O(log n)  
- **Auxiliary Space:** O(log n)

Binary Search Algorithm can be implemented in the following two ways
### Iterative Method
```
function binary_search(A, n, T)
    L := 0 // left pointer
    R := n − 1 // right pointer
    while L ≤ R do
        m := floor((L + R) / 2)
        if A[m] < T
            L := m + 1
        else if A[m] > T
            R := m − 1
        else:
            return m
    return unsuccessful
```
### Recursive Method
```
function binary_search(A, x, l, r)
    if l > r do
	    return false
	else
        m := floor((l + r) / 2)
        if A[m] = x
	        return m;
	    else if x>A[m]
		    return binary_search(A, x, m, r)
        else:
            return binary_search(A, x, l, m)
    return unsuccessful
```

## Analysis
In terms of the number of comparisons, the performance of binary search can be analyzed by viewing the run of the procedure on a [[Binary Tree]].

In the worst case, binary search makes
$${\textstyle \lfloor \log _{2}(n)+1\rfloor }$$
iterations of the comparison loop, where the
$${\textstyle \lfloor \rfloor }$$
notation denotes the [[floor function]] that yields the greatest integer less than or equal to the argument, and
$${\textstyle \log _{2}}$$
is the [[binary logarithm]]. This is because the worst case is reached when the search reaches the deepest level of the tree, and there are always
$${\textstyle \lfloor \log _{2}(n)+1\rfloor }$$
levels in the tree for any binary search.

- Alternative Proof
In j-th iteration, the number of remaining elements
$${\frac{n}{2^{j-1}}}$$
In the last iteration, either x is found or the size of the subsequence being searched reaches 1, whichever occurs. As a result, the maximum number of iterations needed to search for x is that value of j satisfying the condition  
$${\frac{n}{2^{j-1}}=1}$$
By the definition of the [[floor function]], this happens exactly when  
$${1\le\frac{n}{2^{j-1}} < 2}$$
or  
2j-1 ≤ n < 2j,
$${2j-1\le{n} < 2j}$$
or  
$${j-1\le\log{n} < j}$$
Since j is integer, we conclude that  
$${j=\lfloor\log{n}\rfloor-1}$$

==In terms of iterations, no search algorithm that works only by comparing elements can exhibit better average and worst-case performance than binary search. The comparison tree representing binary search has the fewest levels possible as every level above the lowest level of the tree is filled completely.==

### Space complexity
Binary search requires three pointers to elements, which may be array indices or pointers to memory locations, regardless of the size of the array.
Therefore, the **space complexity of binary search is:** 
$${\displaystyle O(1)}$$ 
in the word RAM [[Model of Computation]].