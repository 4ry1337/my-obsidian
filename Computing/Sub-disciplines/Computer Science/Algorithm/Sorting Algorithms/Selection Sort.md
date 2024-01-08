# Selection Sort
**selection sort** is an [[In-place Algorithms | in-place]] [[comparison]] [[Sorting Algorithms | sorting algorithm]]. 

# Basic Algorithm
The algorithm divides the input list into two parts: 
- *sorted sublist*
- *unsorted sublist*

Initially, the sorted sublist is empty and the unsorted sublist is the entire input list.
The algorithm proceeds by finding the smallest (or largest, depending on sorting order) element in the unsorted sublist, exchanging (swapping) it with the leftmost unsorted element (putting it in sorted order), and moving the sublist boundaries one element to the right.

![Selection-Sort-Flowhchart](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20220203094305/Selection-Sort-Flowhchart.png)

Implementation in [[C]]
``` C
/* a[0] to a[aLength-1] is the array to sort */
int i,j;
int aLength; // initialise to a's length
/* advance the position through the entire array */
/*   (could do i < aLength-1 because single element is also min element) */
for (i = 0; i < aLength-1; i++)
{
    /* find the min element in the unsorted a[i .. aLength-1] */
    /* assume the min is the first element */
    int jMin = i;
    /* test against elements after i to find the smallest */
    for (j = i+1; j < aLength; j++)
    {
        /* if this element is less, then it is the new minimum */
        if (a[j] < a[jMin])
        {
            /* found new minimum; remember its index */
            jMin = j;
        }
    }
    if (jMin != i) 
    {
        swap(a[i], a[jMin]);
    }
}
```

## Analysis:
Selection sort is not difficult to analyze compared to other [[Sorting Algorithms]], since none of the loops depend on the data in the array. Selecting the minimum requires scanning $${\displaystyle n}$$ elements (taking $${\displaystyle n-1}$$ comparisons) and then swapping it into the first position. Finding the next lowest element requires scanning the remaining $${\displaystyle n-1}$$ elements and so on. Therefore, the total number of comparisons is

$${\displaystyle (n-1)+(n-2)+...+1=\sum _{i=1}^{n-1}i}$$

By [[arithmetic progression]],

$${\displaystyle \sum _{i=1}^{n-1}i={\frac {(n-1)+1}{2}}(n-1)={\frac {1}{2}}n(n-1)={\frac {1}{2}}(n^{2}-n)}$$

**[[Time Complexity]]:** The [[Time Complexity]] of Selection Sort is $$O(N^2)$$ as there are two nested loops:

-   One loop to select an element of Array one by one: $$O(N)$$
-   Another loop to compare that element with every other Array element: $$O(N)$$

Therefore overall complexity: $$O(N)*O(N) = O(N * N) = O(N^2)$$ which makes it inefficient on large lists, and generally performs worse than the similar [[Insertion Sort]].

**Auxiliary Space:** O(1) as the only extra memory used is for temporary variables while swapping two values in Array. The selection sort never makes more than O(N) swaps and can be useful when memory write is a costly operation.

Selection sort is noted for its simplicity and has performance advantages over more complicated algorithms in certain situations, particularly where [[auxiliary memory]] is limited.

## Variants
- A **bidirectional variant** of selection sort (called **double selection sort** or sometimes **cocktail sort** due to its similarity to [[cocktail shaker sort]] finds _both_ the minimum and maximum values in the list in every pass. This requires three comparisons per two items (a pair of elements is compared, then the greater is compared to the maximum and the lesser is compared to the minimum) rather than regular selection sort's one comparison per item, but requires only half as many passes, a net 25% savings.
- Selection sort can be implemented as a **[[stable sort]]** if, rather than swapping in step 2, the minimum value is *inserted* into the first position and the intervening values shifted up. However, this modification either requires a data structure that supports efficient insertions or deletions, such as a linked list, or it leads to performing $${\displaystyle \Theta (n^{2})}$$ writes.
- In the **bingo sort** variant, items are sorted by repeatedly looking through the remaining items to find the greatest value and moving *all* items with that value to their final location. Like [[Counting Sort]], this is an efficient variant if there are many duplicate values: selection sort does one pass through the remaining items for each *item* moved, while Bingo sort does one pass for each *value*. After an initial pass to find the greatest value, subsequent passes move every item with that value to its final location while finding the next value as in the following [[Pseudocode]] (arrays are zero-based and the for-loop includes both the top and bottom limits, as in [[Pascal]]):

```
bingo(array A)

{ This procedure sorts in ascending order by
  repeatedly moving maximal items to the end. }
begin
    last := length(A) - 1;

    { The first iteration is written to look very similar to the subsequent ones,
      but without swaps. }
    nextMax := A[last];
    for i := last - 1 downto 0 do
        if A[i] > nextMax then
            nextMax := A[i];
    while (last > 0) and (A[last] = nextMax) do
        last := last - 1;

    while last > 0 do begin
        prevMax := nextMax;
        nextMax := A[last];
        for i := last - 1 downto 0 do
             if A[i] > nextMax then
                 if A[i] <> prevMax then
                     nextMax := A[i];
                 else begin
                     swap(A[i], A[last]);
                     last := last - 1;
                 end
        while (last > 0) and (A[last] = nextMax) do
            last := last - 1;
    end;
end;
```