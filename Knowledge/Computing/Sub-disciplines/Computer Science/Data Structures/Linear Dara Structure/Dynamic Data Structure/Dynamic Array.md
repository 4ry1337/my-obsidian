# Dynamic Array
A **dynamic array**, **growable array**, **resizable array**, **dynamic table**, **mutable array**, or **array list** is a random access, variable-size list [[Data Structure]] that allows elements to be added or removed.

## Bounded-size dynamic arrays and capacity
A simple dynamic array can be constructed by allocating an array of fixed-size, typically larger than the number of elements immediately required. The elements of the dynamic array are stored contiguously at the start of the underlying array, and the remaining positions towards the end of the underlying array are reserved, or unused.

### Adding
Elements can be **added** at the end of a dynamic array in **constant time by using the reserved space, until this space is completely consumed**. **When all space is consumed**, and an additional element is to be added, then the underlying **fixed-size array needs to be increased in size**. ==Typically resizing is expensive because it involves allocating a new underlying array and copying each element from the original array.==

### Removing
Elements can be **removed** from the end of a dynamic array in **constant time, as no resizing is required**.

### Logical Size and Capacity
The number of elements used by the dynamic array contents is its *logical size* or *size*, while the size of the underlying array is called the dynamic array's *capacity* or *physical size*, which is the maximum possible size without relocating data.

### Static vs Dynamic
A fixed-size array will suffice in applications where the maximum logical size is fixed (e.g. by specification), or can be calculated before the array is allocated. A dynamic array might be preferred if:
-   the maximum logical size is unknown, or difficult to calculate, before the array is allocated
-   it is considered that a maximum logical size given by a specification is likely to change
-   the amortized cost of resizing a dynamic array does not significantly affect performance or responsiveness

## Geometric expansion and amortized cost
To avoid incurring the cost of resizing many times, dynamic arrays resize by a large amount, such as doubling in size, and use the reserved space for future expansion. The operation of adding an element to the end might work as follows:

```
function insertEnd(dynarray a, element e)
    if (a.size == a.capacity)
        // resize a to twice its current capacity:
        a.capacity ← a.capacity * 2(growth factor) 
        // (copy the contents to the new memory location here)
    a[a.size] ← e
    a.size ← a.size + 1
```

As *n* elements are inserted, the capacities form a geometric progression. Expanding the array by any constant proportion *a* ensures that inserting *n* elements takes *O(n)* time overall, meaning that each insertion takes amortized constant time.

### Growth factor
The growth factor for the dynamic array depends on several factors including a space-time trade-off and algorithms used in the memory allocator itself.
For growth factor *a*, the average time per insertion operation is about a/(a−1), while the number of wasted cells is bounded above by (a−1)n. If memory allocator uses a [[first-fit allocation]] algorithm, then growth factor values such as *a*=2 can cause dynamic array expansion to run out of memory even though a significant amount of memory may still be available.
There have been various discussions on ideal growth factor values, including proposals for the golden ratio as well as the value 1.5. Many textbooks, however, use *a* = 2 for simplicity and analysis purposes.

Below are growth factors used by several popular implementations:

| Implementation            | Growth rate(a)     |
| ------------------------- | ------------------ |
| Java ArrayList            | 1.5(3/2)           |
| Python PyListObject       | ~1.125(n+(n))      |
| Microsoft Visual C++ 2013 | 1.5(3/2)           |
| G++ 5.2.0                 | 2                  |
| Clang                     | 2                  |
| Facebook folly/FBVector   | 1.5(3/2)           |
| Rust Vec                  | 2                  |
| Go Slices                 | between 1.25 and 2 |
| Nim sequence              | 2                  |

## Efficiency

|                    | Peek      | Beginning | End                | Middle    | Excess space, average |
| ------------------ | --------- | --------- | ------------------ | --------- | --------------------- |
| Linked List        | Θ(n)      | Θ()       | Θ()                | Θ()       | Θ(n)                  |
| Array              | Θ(1)      | ---       | ---                | ---       | 0                     |
| **Dynamic Array**  | **Θ(1)**  | **Θ(n)**  | **Θ(1) amortized** | **Θ(n)**  | **Θ(n)**              |
| Balanced Tree      | Θ(log(n)) | Θ(log(n)) | Θ(log(n))          | Θ(log(n)) | Θ(n)                  |
| Random-Access List | Θ(log(n)) | Θ(1)      | ---                | ---       | Θ(n)                  |
| Hashed Array Tree  | Θ(1)      | Θ(n)      | Θ(1) amortized     | Θ(n)      | Θ(n)                  |

The dynamic array has performance similar to an array, with the addition of new operations to add and remove elements:

-   Getting or setting the value at a particular index (constant time)
-   Iterating over the elements in order (linear time, good cache performance)
-   Inserting or deleting an element in the middle of the array (linear time)
-   Inserting or deleting an element at the end of the array (constant amortized time)