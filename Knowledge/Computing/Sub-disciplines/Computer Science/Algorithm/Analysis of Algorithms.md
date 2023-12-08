xIn [[Computer Science]], the **Analysis of Algorithms** is the process of finding the [[Computational Complexity]] of algorithms.

# Cost models
==Time efficiency estimates depend on what we define to be a step. For the analysis to correspond usefully to the actual run-time, the time required to perform a step must be guaranteed to be bounded above by a constant.==

Two cost models are generally used:
-   the **uniform cost model**, also called **uniform-cost measurement**, assigns a constant cost to every machine operation, regardless of the size of the numbers involved
-   the **logarithmic cost model**, also called **logarithmic-cost measurement**, assigns a cost to every machine operation proportional to the number of bits involved

The latter is more cumbersome to use, so it's only employed when necessary, for example in the analysis of arbitrary-precision arithmetic algorithms, like those used in cryptography.

A key point which is often overlooked is that published lower bounds for problems are often given for a [[Model of Computation|model of computation]] that is more restricted than the set of operations that you could use in practice and therefore there are algorithms that are faster than what would naively be thought possible.

# Run-time Analysis
Run-time analysis is a theoretical classification that estimates and anticipates the increase in [running time] (or run-time or execution time) of an [[Algorithm | algorithm]] as its input size (usually denoted as *n*) increases.

Since [[Algorithm]] are platform-independent (i.e. a given algorithm can be implemented in an arbitrary [[Programming Languages]] on an arbitrary [[Computer]] running an arbitrary [[Operating System]], there are additional significant drawbacks to using an empirical approach to gauge the comparative performance of a given set of algorithms.

Take as an example a program that looks up a specific entry in a sorted list of size *n*. Suppose this program were implemented on Computer A, a state-of-the-art machine, using a [[Linear Search]] algorithm, and on Computer B, a much slower machine, using a [[Binary Search]] algorithm. Benchmark testing on the two computers running their respective programs might look something like the following:

|n(list size)|Computer A run-time| Computer B run-time|
|-----|---|-------|
|16   |8  |100,000|
|63   |16 |150,000|
|250  |125|200,000|
|1,000|500|250,000|

Based on these metrics, it would be easy to jump to the conclusion that *Computer A* is running an algorithm that is far superior in efficiency to that of *Computer B*. ==However, if the size of the input-list is increased to a sufficient number, that conclusion is dramatically demonstrated to be in error:==

|n(list size)  |Computer A run-time        | Computer B run-time|
|--------------|---------------------------|--------------------|
|16            |8                          |100000
|63            |16                         |150000
|250           |125                        |200000
|1000          |500                        |250000
|...           |...                        |...
|1000000       |500000                     |500000
|4000000       |2000000                    |550000
|16000000      |8000000                    |600000
|...           |...                        |...   
|$$63072×10^{12}$$|$${31536×10^{12}\text{ ns, or 1 year}}$$|$$1375000\text{ ns, or 1.375 milliseconds}$$

Computer A, running the [[Linear Search]] program, exhibits a linear growth rate.

# Order of Growth
  The order of growth of an algorithm is an approximation of the time required to run a computer program as the input size increases. The order of growth ignores the constant factor needed for fixed operations and focuses instead on the operations that increase proportional to input size.

| Order |
|---|
| Logarithmic |
| Constant |
| Linear |
| Quadratic |
| Exponential |

# Evaluating Run-time Complexity
The run-time complexity for the worst-case scenario of a given algorithm can sometimes be evaluated by examining the structure of the algorithm and making some simplifying assumptions. Consider the following [[Pseudocode]]
```
1    _get a positive integer n from input_
2    **if** n > 10
3        **print** "This might take a while..."
4    **for** i = 1 **to** n
5        **for** j = 1 **to** i
6            **print** i * j
7    **print** "Done!"
```