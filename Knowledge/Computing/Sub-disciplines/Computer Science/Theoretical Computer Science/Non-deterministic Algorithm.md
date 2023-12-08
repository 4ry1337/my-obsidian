# Non-deterministic Algorithm
In [[Computer Science | computer science]], a **nondeterministic algorithm** is an [[Algorithm | algorithm]] that, even for the same input, can exhibit different behaviors on different runs, as opposed to a [[Deterministic Algorithm|deterministic algorithm]]. 

In fact, non-deterministic algorithms can’t solve the problem in polynomial time and can’t determine what is the next step.

The non-deterministic algorithms can show different behaviors for the same input on different execution and there is a degree of randomness to it.

## Example
**Problem Statement :** Search an element x on A[1:n] where n>=1, on successful search return j if a[j] is equals to x otherwise return 0. **Non-deterministic Algorithm for this problem :**

```
j := choice(a, n)
if(A[j]==x) then
       write(j);
       success();
write(0);
failure();
```