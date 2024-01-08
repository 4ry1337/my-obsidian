# Insertion Sort
**Insertion sort** is a simple [[Sorting Algorithms | sorting algorithm]] that builds the final sorted array (or list) one item at a time.
- Algorithmic Paradigm: [[Incremental Approach]]
### Advantages:
-   Efficient for (quite) small data sets, much like other quadratic [[Sorting Algorithms]]
-   More efficient in practice than most other simple quadratic (i.e., $${\displaystyle O(n^2)}$$ ([[Computational Complexity Theory#^BigOh | Big-Oh]]) algorithms such as [[Selection Sort]] or [[Bubble Sort]]
-   [[Adaptive Sort | Adaptive]], i.e., efficient for data sets that are already substantially sorted: the time complexity is [[Computational Complexity Theory#^BigOh | O(kn)]] when each element in the input is no more than k places away from its sorted position
-   [[Stable Sort | Stable]] i.e., does not change the relative order of elements with equal keys
-   [[In-place Algorithms|In-place]]; i.e., only requires a constant amount O(1) of additional memory space
-   [[Online Algorithms | Online]]; i.e., can sort a list as it receives it

### Disadvantages
It is much less efficient on large lists than more advanced algorithms such as [[Quick Sort]], [[Heap Sort]], or [[Merge Sort]].

## Basic Algorithm
Insertion sort iterates, consuming one input element each repetition, and grows a sorted output list. At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there. It repeats until no input elements remain.

The most common variant of insertion sort, which operates on arrays, can be described as follows:

1.  Suppose there exists a function called _Insert_ designed to insert a value into a sorted sequence at the beginning of an array. It operates by beginning at the end of the sequence and shifting each element one place to the right until a suitable position is found for the new element. The function has the side effect of overwriting the value stored immediately after the sorted sequence in the array.
2.  To perform an insertion sort, begin at the left-most element of the array and invoke _Insert_ to insert each element encountered into its correct position. The ordered sequence into which the element is inserted is stored at the beginning of the array in the set of indices already examined. Each insertion overwrites a single value: the value being inserted.

[[Pseudocode]] of the complete algorithm follows, where the arrays are zero-based.
```
i ← 1
while i < length(A)
    j ← i
    while j > 0 and A[j-1] > A[j]
        swap A[j] and A[j-1]
        j ← j - 1
    end while
    i ← i + 1
end while
```

## Analysis
**[[Time Complexity]]:** O(N^2)   
**Auxiliary Space:** O(1)

The *best case* input is an array that is already sorted. In this case,  
the number of element comparisons is exactly n - 1, as each element A[i],  
2 ≤ i ≤ n, is compared with A[i - 1] only. 
Thus, insertion sort has a linear running time (i.e., *O(n)*). During each iteration, the first remaining element of the input is only compared with the right-most element of the sorted subsection of the array.

The simplest *worst case* input is an array sorted in reverse order. The set of all worst case inputs consists of all arrays where each element is the smallest or second-smallest of the elements before it. In these cases every iteration of the inner loop will scan and shift the entire sorted subsection of the array before inserting the next element. 
$${\sum_{i=2}^{n}{i-1}=\sum_{i=2}^{n-1}{i}=\frac{n*(n-1)}{2}}$$
as each element A[i], 2 ≤ i ≤ n, is compared with each entry in the subarray  
A[1..i - 1]. This gives insertion sort a quadratic running time:
$${O(n^2)}$$

The average case is also quadratic, which makes insertion sort impractical for sorting large arrays. However, insertion sort is one of the fastest algorithms for sorting very small arrays, even faster than [[Quick Sort]].

## Variants
### Shell Sort

^shellsort

[[Shell sort]]. The sorting algorithm compares elements separated by a distance that decreases on each pass. Shell sort has distinctly improved running times in practical work, with two simple variants requiring O(_n_3/2) and O(_n_4/3) running time.