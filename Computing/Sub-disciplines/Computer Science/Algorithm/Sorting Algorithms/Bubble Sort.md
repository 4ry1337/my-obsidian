# Bubble Sort
**Bubble sort**, sometimes referred to as **sinking sort**, is a simple [[sorting algorithm]] that repeatedly steps through the input list element by element, comparing the current element with the one after it, swapping their values if needed. These passes through the list are repeated until no swaps had to be performed during a pass, meaning that the list has become fully sorted.

## Basic Algorithm
```
function bubbleSort(A : list of sortable items)
    n := length(A)
    repeat
        swapped := false
        for i := 1 to n-1 inclusive do
            /* if this pair is out of order */
            if A[i-1] > A[i] then
                /* swap them and remember something changed */
                swap(A[i-1], A[i])
                swapped := true
            end if
        end for
    until not swapped
end function
```

## Analysis
**Worst and Average Case [[Time Complexity]]:** $$O(N^2)$$. The worst case occurs when an array is reverse sorted.  
**Best Case [[Time Complexity]]:** $$O(N)$$. The best case occurs when an array is already sorted.  
**Auxiliary Space:** $$O(1)$$