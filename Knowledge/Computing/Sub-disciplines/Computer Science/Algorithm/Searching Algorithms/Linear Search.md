# Linear Search
Linear Search is defined as a sequential [[Search Algorithms| search algorithm]] that starts at one end and goes through each element of a list until the desired element is found, otherwise the search continues till the end of the data set.

## Basic algorithm
- Start from the leftmost element of arr[] and one by one compare x with each element of arr[]
- If x matches with an element, return the index.
- If x doesn’t match with any of the elements, return -1.

**Complexity:**
- **[[Time Complexity]]:** O(N)  
- **Auxiliary Space:** O(1)

## Linear Search Recursive Approach:
- If the size of the array is zero then, return -1, representing that the element is not found. This can also be treated as the base condition of a recursion call.
- Otherwise, check if the element at the current index in the array is equal to the key or not i.e, arr[size – 1] == key
    -   If equal, then return the index of the found key.

**Complexity:**
- **[[Time Complexity]]:** O(N)  
- **Auxiliary Space:** O(1)


## Analysis
For a list with *n* items, the [[Computational Complexity Theory#Best Worst and Average Case Complexity | best-case]] is when the value is equal to the first element of the list, in which case only one comparison is needed. The worst case is when the value is not in the list (or occurs only once at the end of the list), in which case *n* comparisons are needed.

If the value being sought occurs *k* times in the list, and all orderings of the list are equally likely, the expected number of comparisons is

$$ \begin{cases} n \hspace{1 cm} \text{ if } k = 0\\ \frac{n+1}{k+1} \hspace{1 cm} \text{ if } 1 \leq n \leq k \end{cases} $$

For example, if the value being sought occurs once in the list, and all orderings of the list are equally likely, the expected number of comparisons is
$$\frac{n+1}{n}$$
However, if it is *known* that it occurs once, then at most *n* - 1 comparisons are needed, and the expected number of comparisons is

$$\frac{(n+2)(n-1)}{2n}$$

(for example, for *n* = 2 this is 1, corresponding to a single if-then-else construct).

Either way, [[Computational Complexity Theory | asymptotically]] the [[Computational Complexity Theory#Best Worst and Average Case Complexity | worst-case]] cost and the expected cost of linear search are both [[Computational Complexity Theory#^BigOmega|O(n)]].

### Non-uniform probabilities
The performance of linear search improves if the desired value is more likely to be near the beginning of the list than to its end. Therefore, if some values are much more likely to be searched than others, it is desirable to place them at the beginning of the list.

In particular, when the list items are arranged in order of decreasing probability, and these probabilities are geometrically distributed, the cost of linear search is only O(1).