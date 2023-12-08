# Computational Complexity Theory
In [[Theoretical Computer Science]], computational complexity theory focuses on classifying [[Computational Problems]], task solved by a computer , according to their resource usage, and relating these classes to each other. A computation problem is solvable by mechanical application of mathematical steps, such as an [[Algorithm | algorithm]].

## Machine Models
#### Turing Machine 
A **Turing machine** is a mathematical [[Model of Computation]] describing an [[Abstract Machine|abstract machine]] that manipulates symbols on a strip of tape according to a table of rules. Despite the model's simplicity, it is capable of implementing any [[Algorithm | algorithm]].

Many types of Turing machines are used to define complexity classes:
- deterministic Turing machines
- probabilistic Turing machines
- non-deterministic Turing machines
- quantum Turing machines
- symmetric Turing machines
- alternating Turing machines

They are all equally powerful in principle, but when resources (such as time or space) are bounded, some of these may be more powerful than others.

## Best, Worst and Average Case Complexity
### Best Case
Best case performance used in [[Computer Science]] to describe an algorithm’s behavior under optimal conditions.

For example:
*The best case for a simple [[Linear Search]] on a list occurs when the desired element is the first element of the list.*
```
array of [1, 3, 4, 2, 34];	
find index of 1 in array;
```

### Worst Case
Worst case performance used to analyze the algorithm's behavior under worst case input and least possible to solve the problem.

For example:
*The worst case for a simple [[Linear Search]] on a list occurs when the desired element is the end element of the list.*
```
array of [1, 3, 4, 2, 34];	
find index of 34 in array;
```

### Average Case
Average case performance measured using the average optimal conditions to solve the problem.

For example:
*The average case for a simple [[Linear Search]] on a list occurs when the desired element is in the middle of the list.*
```
array = [1, 3, 4, 2, 34];	
find index of 2 in array || find index of 4 in array;
```

### Amortized analysis
Amortized analysis considers both the costly and less costly operations together over the whole series of operations of the algorithm.


## Upper, Lower and Tight Bounds
To classify the computation time (or similar resources, such as space consumption), it is helpful to demonstrate upper and lower bounds on the maximum amount of time required by the most efficient algorithm to solve a given problem.

### Upper Bound and The Big O
^BigOh

The asymptotic expression `O(f(n))`, read “order of f(n)”, or “big-oh of f(n)” denotes **the set of all functions that are asymptotically dominated by the function `f(n)`**. This means that the set consists of the functions that grow at the same or slower rate than `f(n)`. Then `f(n)` is an **upper bound** for `g(n)` because ==f(n) grows faster than g(n) as n increases==.

>  For a function `g(n) ∈ O(f(n))` (g(n) that is in the set O(f(n))), if there exist positive constants `n0` and `c` such that for all n ≥ n0, `g(n) ≤ c · f(n)`.

### Lower Bound and The Big Omega
^BigOmega

The asymptotic expression `Ω(f(n))` denotes **the set of all functions that asymptotically dominate the function `f(n)`**. This means that the set  consists of the functions that grow faster than `f(n)`. Then `f(n)` being a **lower bound** for `g(n)` because ==f(n) grows slower than g(n) as n increases==.

> For a function `g(n) ∈ Ω(f(n))` (g(n) that is in the set Ω(f(n))) if there exist positive constants `n0` and `c` such that for all n ≥ n0, `c*f(n) ≤ |g(n)|`

==Proving lower bounds is much more difficult, since lower bounds make a statement about all possible algorithms that solve a given problem. The phrase "all possible algorithms" includes not just the algorithms known today, but any algorithm that might be discovered in the future.==

### Tight Bound and The Big Theta
^BigTheta

The asymptotic expression `Θ(f(n))` denotes **the set of all functions that grow at the same rate as `f(n)`**. The set Θ(f(n)) is the set of functions that are both in O(f(n)) and Ω(f(n)). Then f(n) is a **tight bound** for g(n) because ==f(n) grows at the same rate as g(n) as n increases==.  

>  For a function `g(n) ∈ Θ(f(n))` (g(n) that is in the set Θ(f(n))) if there exist positive constants `n0`, `c1`, and `c2` such that for all n ≥ n0, `c1*f(n) ≤ |g(n)| ≤ c2*f(n)`.
 