# Binary Tree
A **binary tree** is a [[Tree | tree data structure]] in which each node has at most two children, which are referred to as the _left child_ and the _right chil_.

## Types of Binary Tree
- A **rooted** binary [[Tree | tree]] has a root node and every node has at most two children.
- A **full** binary tree (sometimes referred to as a **proper** or **plane** or **strict** binary tree) is a tree in which every node has either 0 or 2 children. Another way of defining a full binary tree is a recursive definition. A full binary tree is either:
    - A single vertex.
    - A tree whose root node has two subtrees, both of which are full binary trees.
- A **perfect** binary tree is a binary tree in which all interior nodes have two children _and_ all leaves have the same _depth_ or same _level_.
- A **complete** binary tree is a binary tree in which every level, _except possibly the last_, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2_h_ nodes at the last level _h_. A perfect tree is therefore always complete but a complete tree is not necessarily perfect.
- A **balanced** binary tree is a binary tree structure in which the left and right subtrees of every node differ in height by no more than 1.

## Properties of binary trees
- The number of nodes $${\displaystyle n}$$ in a full binary tree is at least $${\displaystyle 2h+1}$$ and at most $${\displaystyle 2^{h+1}-1}$$, where $${\displaystyle h}$$ is the height of the tree. A tree consisting of only a root node has a height of 0.
- The number of leaf nodes $${\displaystyle l}$$ in a perfect binary tree, is $${\displaystyle l=(n+1)/2}$$ because the number of non-leaf (a.k.a. internal) nodes $${\displaystyle n-l=\sum _{k=0}^{\log _{2}(l)-1}2^{k}=2^{\log _{2}(l)}-1=l-1}$$
- This means that a full binary tree with $${\displaystyle l}$$ leaves has $${\displaystyle n=2l-1}$$ nodes.
- In a **balanced** full binary tree, $${\displaystyle h=\lceil \log _{2}(l)\rceil +1=\lceil \log _{2}((n+1)/2)\rceil +1=\lceil \log _{2}(n+1)\rceil }$$
- In a **perfect** full binary tree, $${\displaystyle l=2^{h}}$$ thus $${\displaystyle n=2^{h+1}-1}$$.
- The number of null links (i.e., absent children of the nodes) in a binary tree of _n_ nodes is (_n_+1).
- The number of internal nodes in a **complete** binary tree of _n_ nodes is $${\displaystyle \lfloor n/2\rfloor }$$.
- For any non-empty binary tree with *$${n_0}$$ leaf nodes and $${n_2}$$ nodes of degree 2, $${n_0=n_2+1}$$*.