In [[Computer Science]], the **computational complexity** or simply **complexity** of an [[Algorithm | algorithm]] is the amount of resources required to run it. Particular focus is given to time and memory requirements. The complexity of a [[Computational Problems]] is the complexity of the best algorithms that allow solving the problem.

## Resources

^resources

### [[Time Complexity | Time]]
Complexity theory seeks to quantify the intrinsic time requirements of algorithms, that is, the basic time constraints an algorithm would place on any computer. ==This is achieved by counting the number of *elementary operations* that are executed during the computation.== These operations are assumed to take constant time on a given machine, and are often called **steps**

### Bit
is the number of operations on bits that are needed for running an algorithm.

With most models of computation, it equals the time complexity up to a constant factor.  So, the *time complexity* and the *bit complexity* are equivalent for realistic models of computation.

### [[Space Complexity | Space]]
Another important resource is the size of [[Computer Memory]] that is needed for running algorithms.

### Other
The number of arithmetic operations is a resource. **Arithmetic complexity**. An upper bound on the size of the binary representation of the numbers that occur during a computation, the time complexity is generally the product of the arithmetic complexity by a constant factor.

## Complexity as a function of input size
the complexity is typically expressed as a function $${n \rightarrow f(n) \text{, where n}}$$ is the size of the input. However, the complexity of an algorithm may vary dramatically for different inputs of the same size. Therefore, several complexity functions are commonly used.

## Asymptotic Complexity
It is generally difficult to compute precisely the worst-case and the average-case complexity. In addition, these exact values provide little practical application, as any change of computer or of [[Model of Computation | model of computation]] would change the complexity somewhat. Moreover, the resource use is not critical for small values of n, and this makes that, for small n, the ease of implementation is generally more interesting than a low complexity.

For these reasons, one generally focuses on the behavior of the complexity for large n, that is on its [[asymptotic behavior]] when n tends to the infinity.

## Models of Computation
The evaluation of the complexity relies on the choice of a [[Model of Computation|model of computation]], which consists in defining the basic operations that are done in a unit of time. When the [[Model of Computation]] is not explicitly specified, this is generally meant as being multi-tape Turing machine.