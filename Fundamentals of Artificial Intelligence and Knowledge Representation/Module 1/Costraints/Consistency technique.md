In contrast to [[Propagation algorithms]] that propagate the constraints as a result of the instantiations of variables, consistency technique reduces the original problem by eliminating domain values that cannot appear in the final solution.
They can be applied statically or at every step on not-yet instantiated variables.
All the consistency techniques see the problem as a graph where arcs are the constraints that connects variables and the arcs can be directional or not.
A node could also have arcs that point to itself that represent unary constraints
(Example: $X_1, \;\; D_1 = [r,g,b] \bigwedge X_1 \neq r$). 

## Node consistency
A node is consistent if: $\forall X_{the} \in D_{the}$ the unary constraints on $X_{the}$ are satisfied.
A graph is node consistent, or level one consistent, if all its node are node consistent

## Arc consistency
An arc i,j is consistent if $\forall x \in D_i \; \exists y \in D_j$ such that the constraints between i and j are satisfied. y is called support for i. 
A network is arc consistent, or level 2 consistent, if every node is consistent.
After the consistency checks some possible values of the variables could be deleted, therefore, further check must be applied until the graph reaches a stability and consistency (__QUIESCENT__).
The arc consistency can be applied as a pre-processing technique or as a propagation step.
An example of an arc consistency finding technique is [[AC-3]]
__Arc consistency does not guarantee the existence of a solution__

## Path consistency
Is obtained starting from a graph that is level 2 consistent.
A path between nodes i,j,k is consistent if $\forall x \in D_i, \; y \in D_j \; \; \text{(x and y arc and node consistent)} \; \exists z \in D_k: P(i,k) \bigwedge P(k,j)$ with P that check the constraints between two nodes.

## K-consistency
In principle, in a [[Fundamentals of Artificial Intelligence and Knowledge Representation/Module 1/Costraints/Constraint satisfaction problem|CSP]] of k variable, if we want to be sure that only the values that can be part of a solution remains in the domain of each variable we must have a k consistent graph. For each k-1-tuple of values consistent with the constraints imposed by the problem, there is a value for each k-th variable that satisfies the constraints among all k variables. If a CSP containing n variables is n-consistent, then you can find a solution without search. However, making n-consistent a network of n variables has an complexity exponential in n (the cost is the same as solving the original problem).