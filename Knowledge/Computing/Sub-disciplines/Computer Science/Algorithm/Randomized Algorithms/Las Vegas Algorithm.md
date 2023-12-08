# Las Vegas Algorithm
**Las Vegas algorithm** is a [[Randomized Algorithm|randomized algorithm]] that always gives correct results; that is, it always produces the correct result or it informs about the failure. However, the runtime of a Las Vegas algorithm differs depending on the input. The usual definition of a Las Vegas algorithm includes the restriction that the _expected_ runtime be finite, where the expectation is carried out over the space of random information, or entropy, used in the algorithm.

An alternative definition requires that a Las Vegas algorithm always terminates (is effective, but may output a symbol not part of the solution space to indicate failure in finding a solution.)

> The nature of Las Vegas algorithms makes them suitable in situations where the number of possible solutions is limited, and where verifying the correctness of a candidate solution is relatively easy while finding a solution is complex.

## Definition
An algorithm ${A}$ is a Las Vegas algorithm for problem class ${X}$, if
1. whenever for a given problem instance ${x \in X}$ it returns a solution ${s}$, ${s}$ is guaranteed to be a valid solution of ${x}$
2. on each given instance ${x}$, the run-time of A is a random variable ${RT_{A,x}}$

There are three notions of _completeness_ for Las Vegas algorithms:
- _complete Las Vegas algorithms_ can be guaranteed to solve each solvable problem within run-time ${t_{max}}$, where ${t_{max}}$ is an instance-dependent constant.

Let ${P({RT}_{A,x} \leq t)}$ denote the probability that ${A}$ finds a solution for a soluble instance ${x}$ in time within ${t}$, then ${A}$ is complete exactly if for each ${x}$ there exists some ${t_{max}}$ such that ${P({RT}_{A,x} \leq t_{max}) = 1}$.

- _approximately complete Las Vegas algorithms_ solve each problem with a probability converging to 1 as the run-time approaches infinity. Thus, ${A}$ is approximately complete, if for each instance ${x}$, ${\lim_{t \to \infty} P({RT}_{A,x} \leq t) = 1}$.
- _essentially incomplete Las Vegas algorithms_ are Las Vegas algorithms that are not approximately complete.

Approximate completeness is primarily of theoretical interest, as the time limits for finding solutions are usually too large to be of practical use.

### Application scenarios
Las Vegas algorithms have different criteria for the evaluation based on the problem setting. These criteria are divided into three categories with different time limits since Las Vegas algorithms do not have set time complexity. Here are some possible application scenarios:

- Type 1: There are no time limits, which means the algorithm runs until it finds the solution.
- Type 2: There is a time limit ${t_{max}}$ for finding the outcome.
- Type 3: The utility of a solution is determined by the time required to find the solution.

(Type 1 and Type 2 are special cases of Type 3.)

For Type 1 where there is no time limit, the average run-time can represent the run-time behavior. This is not the same case for Type 2.

Here, ${P(RT \leq t-{max})}$, which is the probability of finding a solution within time, describes its run-time behavior.

In case of Type 3, its run-time behavior can only be represented by the run-time distribution function rtd: ${R \to [0,1]}$ defined as ${rtd(t) = P(RT \leq t)}$ or its approximation.

The run-time distribution (RTD) is the distinctive way to describe the run-time behavior of a Las Vegas algorithm.

With this data, we can easily get other criteria such as the mean run-time, standard deviation, median, percentiles, or success probabilities ${P(RT \leq t)}$ for arbitrary time-limits ${t}$.