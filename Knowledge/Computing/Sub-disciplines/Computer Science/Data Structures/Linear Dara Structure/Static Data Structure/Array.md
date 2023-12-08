# Array
An **Array Data Structure**, or **Array**, is a [[Data Structure]] consisting of a collection of *elements* (values or variables), each identified by at least one *array index* or *key*.

## Array’s size
In C language, the array has a fixed size.

### Resizing
Static arrays have a size that is fixed when they are created and consequently do not allow elements to be inserted or removed. However, by allocating a new array and copying the contents of the old array to it, it is possible to effectively implement a _dynamic_ version of an array; see [[Dynamic Array]]. If this operation is done infrequently, insertions at the end of the array require only amortized constant time.

## Indexing in an array :
When data objects are stored in an array, individual objects are selected by an index that is usually a non-negative scalar integer. Indexes are also called subscripts. An index *maps* the array value to a stored object.

There are three ways in which the elements of an array can be indexed:

- 0 (zero-based indexing): The first element of the array is indexed by a subscript of 0.
- 1 (one-based indexing): The first element of the array is indexed by the subscript of 1.
- N (N-based indexing): The base index of an array can be freely chosen. Usually, programming languages allowing n-based indexing also allow negative index values, and other scalar data types like enumerations, or characters may be used as an array index.

## Types of arrays :
### One dimensional array (1-D arrays)
A one-dimensional array (or single dimension array) is a type of linear array. Accessing its elements involves a single subscript which can either represent a row or column index.

### Multidimensional array
#### Compact layouts
Often the coefficients are chosen so that the elements occupy a contiguous area of memory. However, that is not necessary. Even if arrays are always created with contiguous elements, some array slicing operations may create non-contiguous sub-arrays from them.

**In the row-major order** layout (adopted by C for statically declared arrays), the elements in each row are stored in consecutive positions and all of the elements of a row have a lower address than any of the elements of a consecutive row.

**In column-major order** (traditionally used by Fortran), the elements in each column are consecutive in memory and all of the elements of a column have a lower address than any of the elements of a consecutive column.

# Efficiency
Both *store* and *select* take (deterministic worst case) constant time. Arrays take linear [[Computational Complexity Theory#^BigOh| O(n)]] space in the number of elements *n* that they hold.

|                    | Peek      | Beginning | End            | Middle    | Excess space, average |
| ------------------ | --------- | --------- | -------------- | --------- | --------------------- |
| Linked List        | Θ(n)      | Θ()       | Θ()            | Θ()       | Θ(n)                  |
| **Array**          | **Θ(1)**  | **---**   | **---**        | **---**   | **0**                     |
| Dynamic Array      | Θ(1)      | Θ(n)      | Θ(1) amortized | Θ(n)      | Θ(n)                  |
| Balanced Tree      | Θ(log(n)) | Θ(log(n)) | Θ(log(n))      | Θ(log(n)) | Θ(n)                  |
| Random-Access List | Θ(log(n)) | Θ(1)      | ---            | ---       | Θ(n)                  |
| Hashed Array Tree  | Θ(1)      | Θ(n)      | Θ(1) amortized | Θ(n)      | Θ(n)                  |
