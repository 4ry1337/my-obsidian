# Radix Sort
In [[Computer Science]], **radix sort** is a non-comparative [[Sorting Algorithms|sorting algorithm]]. It avoids comparison by creating and distributing elements into buckets according to their radix.

In a positional numeral system, the **radix** or **base** is the number of unique digits, including the digit zero, used to represent numbers.

## Digit order
Radix sorts can be implemented to start at either the most significant digit (MSD) or least significant digit (LSD).
## Complexity and performance
Radix sort operates in ${O(nw)}$ time, where ${n}$ is the number of keys, and ${w}$ is the key length.
LSD variants can achieve a lower bound for ${w}$ of 'average key length' when splitting variable length keys into groups as discussed above.

Optimized radix sorts can be very fast when working in a domain that suits them. They are constrained to lexicographic data, but for many practical applications this is not a limitation. Large key sizes can hinder LSD implementations when the induced number of passes becomes the bottleneck.