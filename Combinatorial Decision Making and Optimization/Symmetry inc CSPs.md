It is a common problem in [[CSP|CSPs]] where the variable order is not important or partially important (e.g. the n queens problem where, for each solution, the mirror of that solution is also a valid one). If we do not avoid symmetry in our models, we could waste some computational time in the discovery of the same solution over and over.

__The definition__:
A permutation $\pi$ of the variable indices s.t. for each (un)feasible assignment, we can re-arrange the variables according to π and obtain another (un) feasible assignment.

In order to avoid symmetries, we can introduce new [[Constraints]]. These kinds of constraints are very delicate, tho, because we need to make sure that they prune all the symmetric solutions but one.

### An example, [[Modelling is important|Golomb ruler]]:

For the Golomb ruler, for each solution, any permutation of the given solution is a valid one.
In this case, we can introduce an ordering constraint such like $X_1 < X_2 < X_3 < \dots < X_m$. In order to avoid every permutation but the one with increasing marks.