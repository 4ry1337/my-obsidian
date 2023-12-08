# Merge Algorithm
**Merge algorithms** are a family of [[Algorithm | algorithms]] that take multiple sorted lists as input and produce a single list as output, containing all the elements of the inputs lists in sorted order. These algorithms are used as subroutines in various [[Sorting Algorithms]], most famously [[Merge Sort]].

## Merging Two Lists
Merging two sorted lists into one can be done in [[Analysis of Algorithms#Order of Growth | linear time]] and linear or constant space (depending on the data access model).
```
algorithm merge(A, B) is
    inputs A, B : list
    returns list

    C := new empty list
    while A is not empty and B is not empty do
        if head(A) ≤ head(B) then
            append head(A) to C
            drop the head of A
        else
            append head(B) to C
            drop the head of B
	// By now, either A or B is empty. It remains to empty the other input list.
    while A is not empty do
        append head(A) to C
        drop the head of A
    while B is not empty do
        append head(B) to C
        drop the head of B
    return C
```