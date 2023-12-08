# Merge Sort
**Merge sort** (also commonly spelled as **mergesort**) is an efficient, general-purpose, and [[Comparison sort | comparison-based]] [[Sorting Algorithm]]
- Algorithmic paradigm: [[Divide and Conquer]]

## Basic Algorithm
Conceptually, a merge sort works as follows:
1. Divide the unsorted list into *n* sublists, each containing one element (a list of one element is considered sorted).
2. Repeatedly [[Merge Algorithm | merge]] sublists to produce new sorted sublists until there is only one sublist remaining. This will be the sorted list.

### Types of Merge Sort
An array A[l...r] of elements and three indices l, m and r, with  l ≤ m < r, such that both the subarrays A[l...m] and A[m + 1...r] are sorted individually in nondecreasing order.
```
function merge(A, l, m, r) is
	B[p...r] empty array
	i := l // starting index of first array
	j := m+1 // starting index of second array
	k := l // starting index of B empty array
	while i ≤ m and j ≤ r do
		if A[i] ≤ A[j] then
			B[k] := A[i]
			i := i+1
		else
			B[k] := A[j]
			j := j + 1
		end if
		k := k + 1
	end while
	// if one of array is bigger than second all the remaining elements from bigger should be transefered to B.
	if i = m + 1 then B[k...r] := A[j...r]
	else B[k+r] := A[i...q]
	end if
	A[l...r] := B[l...r]
    
```
#### Top-Down Implementation
[[Pseudocode]] for top-down merge sort algorithm which recursively divides the input list into smaller sublists until the sublists are trivially sorted, and then merges the sublists while returning up the call chain.
```
function merge_sort(list m) is
    /* Base case.
    A list of zero or one elements is sorted, by definition.*/
    if length of m ≤ 1 then
        return m

    // Recursive case.
    /* First, divide the list into equal-sized sublists 
    consisting of the first half and second half of the list.
    This assumes lists start at index 0.*/
    var left := empty list
    var right := empty list
    for each x with index i in m do
        if i < (length of m)/2 then
            add x to left
        else
            add x to right

    // Recursively sort both sublists.
    left := merge_sort(left)
    right := merge_sort(right)

    // Then merge the now-sorted sublists.
    return merge(left, right)
```
#### Bottom-Up Implementation for Arrays
[[Pseudocode]] for bottom-up merge sort algorithm 
```
function BottomUpMergeSort(A)
	step := 1
	while step < length do
		size := step
		step := size * 2
		i := 0
		while size + step <= length do
			merge(A, i, i + size, i + step)
			i := i + step
		end while
		if size + i < length then
			MERGE(A, i, i + size, length)
		end if
	end while
```

##### Analysis of Bottom-Up Merge Sort
In the j-th iteration of the while loop, there are
$$\frac{n}{2^j}$$
merge operations on two subarrays of size
$$2^{j-1}$$
and it follows that the number of comparisons needed in the j-th iteration is between
$$\frac{n}{2^j}2^{j-1}$$
and
$$\frac{n}{2^j}2^{j - 1}$$.
Thus, if let
$$k = log n$$
, then the number of element comparisons is at least
$$\sum_{j=1}^k{\frac{n}{2^j}2^{j-1}} = \sum_{j=1}^k{\frac{n}{2} = \frac{kn}{2} = \frac{k\log(n)}{2}}$$
and is at most  
$$\sum_{j=1}^k{\frac{n}{2^j}2^{j-1}} = \sum_{j=1}^k{(n-\frac{n}{2^j})} = kn - n \sum_{j=1}^k{\frac{1}{2^j}} =$$
$$ kn - n(1-\frac{1}{2^k}) = kn - n(1-\frac{1}{n}) = n\log(n) - n + 1$$