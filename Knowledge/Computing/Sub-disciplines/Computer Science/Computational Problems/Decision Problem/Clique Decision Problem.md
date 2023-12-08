# Clique Decision Problem
In [[Computer Science|computer science]], the **clique decision problem** is a subproblem of [[Clique Problem]] that is a [[Decision Problem]] that finds existence of k-sized complete subgraph in a [[Graph|graph]].

## Problem Definition
Given a graph ${G=(V,E)}$, and a positive integer ${k}$. Determine if G has a k-clique, that is,  there is a set of vertices U of size k such that for each pair of vertices in U there is and edge in E between them.

## NP-completeness
The clique decision problem is [[NP-completeness|NP-complete]]. Because of the hardness of the decision problem, the problem of finding a maximum clique is also [[NP-hardness|NP-hard]]. If one could solve it, one could also solve the decision problem, by comparing the size of the maximum clique to the size parameter given as input in the decision problem.

Karp's NP-completeness proof is a many-one reduction from the [[Boolean Satisfiability Problem|Boolean satisfiability problem]]. It describes how to translate Boolean formulas in [[Boolean Satisfiability Problem#^ce1a9d|conjunctive normal form]] (CNF) into equivalent instances of the maximum clique problem.
Satisfiability, in turn, was proved NP-complete in the *Cook–Levin theorem*.
From a given CNF formula, Karp forms a graph that has a vertex for every pair ${(v,c)}$, where ${v}$ is a *variable or its negation* and ${c}$ is a *clause* in the formula that contains v.
Two of these vertices are connected by an edge if they represent compatible variable assignments for different clauses. That is, there is an edge from ${(v,c)}$ to ${(u,d)}$ whenever ${c \neq d}$ and ${u}$ and ${v}$ are not each other's negations. If k denotes the number of clauses in the CNF formula, then the k-vertex cliques in this graph represent consistent ways of assigning truth values to some of its variables in order to satisfy the formula. Therefore, the formula is satisfiable if and only if a k-vertex clique exists.