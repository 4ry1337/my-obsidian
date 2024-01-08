# Randomized Algorithm
A randomized algorithm is an [[Algorithm| algorithm]] that employs a degree of randomness as part of its logic or procedure.

The algorithm typically uses uniformly random bits as an auxiliary input to guide its behavior, in the hope of achieving good performance in the "average case" over all possible choices of random determined by the random bits; thus either the running time, or the output (or both) are random variables.

In common practice, randomized algorithms are approximated using a [[Pseudorandom Number Generator]] in place of a true source of random bits; such an implementation may deviate from the expected theoretical behavior and mathematical guarantees which may depend on the existence of an ideal true random number generator.

## Definition
Randomized algorithms are used when presented with a time or memory constraint, and an average case solution is an acceptable output. Due to the potential erroneous output of the algorithm, an [[Algorithm | algorithm]] known as amplification is used in order to boost the probability of correctness by sacrificing runtime.

Amplification works by repeating the randomized algorithm several times with different random subsamples of the input, and comparing their results. It is common for randomized algorithms to amplify just parts of the process, as too much amplification may increase the running time beyond the given constraints.

## Forms
Randomized algorithms are usually designed in one of two common forms: 

- [[Las Vegas Algorithm]]
- [[Monte Carlo Algorithm]]

|                       | Running Time  | Correctness   |
| --------------------- | ------------- | ------------- |
| Las Vegas Algorithm   | probabilistic | certain       |
| Monte Carlo Algorithm | certain       | probabilistic |

## Computational complexity
[[Computational Complexity Theory]] models randomized algorithms as _[[Probabilistic Turing Machine]]_. Both [[Las Vegas]] and [Monte Carlo algorithms] are considered, and several [[Complexity Class|complexity classes]] are studied.

The most basic randomized complexity class is [RP], which is the class of [[Decision Problem|decision problems]] for which there is an efficient (polynomial time) randomized algorithm (or probabilistic Turing machine) which recognizes NO-instances with absolute certainty and recognizes YES-instances with a probability of at least 1/2.
The complement class for RP is co-RP. Problem classes having (possibly nonterminating) algorithms with polynomial time average case running time whose output is always correct are said to be in ZPP.

The class of problems for which both YES and NO-instances are allowed to be identified with some error is called BPP. This class acts as the randomized equivalent of P, i.e. BPP represents the class of efficient randomized algorithms.