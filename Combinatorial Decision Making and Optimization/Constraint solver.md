An algorithm to resolve a [[Combinatorial Decision Making and Optimization/Constraint satisfaction problem|CSP]].
There are many ways to build such algorithm. The simplest one is the generate and test one: generate all possibilities, then check for a good one (computationally awfull). A better approach is to use [[Constraints propagation]] to prune solutions in order to restrict the search area.
The standart algorithm that uses constraints propagation uses backtracking as programming tecnique to find a solution.

## Search heuristics

After a possible variable assignement is choosen, it is not obvious what must be the next variable to assign. The better way to choose such a variable is to try with the one that has more possibility to end with a "dead end" (Fail First principle). There are many ways to do so:
- Dom: choose the variable with smaller domain. 
- Deg: choose the variable with more constraints on it.
- Weighted degree heuristic (domWeg): like Dom, but constraints are weighted. The weight of a variable is given by the sum of all its constraints and the next one is chosen by: $\frac{dom(X_i)}{w(X_i)}$
- [[Randomization]] + [[Restarting]] (to avoid [[Heavy tail behaviour]])
- domWeg + [[Restarting]]

Another thing we can do is to design a problem-specific algorithm that, at each step, chooses the next variable. It is a bit more expensive computationally speaking, but it can prune the search space faster and more efficiently.


# Constraint optimization problems

Often, in a [[Combinatorial Decision Making and Optimization/Constraint satisfaction problem|CSP]], we don't only want to only find a solution but an optimal one (given a function to maximize / minimize). We need to take that into account in the search algorithm or else the computational costs will explode.

### Branch and bound

Find first a solution, then, backtrack with a new constraint that search for a better solution.

### Large neighbourhood search

Define a (generic and large) neighbourhood and, after a solution has been found, search in the neighbourhood for a better one.