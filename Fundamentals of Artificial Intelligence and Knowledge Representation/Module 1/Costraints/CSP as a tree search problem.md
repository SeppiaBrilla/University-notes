theta_p, theta_g and w are parameters that should be carefully choose  as they strongly influence the efficencyA [[Fundamentals of Artificial Intelligence and Knowledge Representation/Module 1/Costraints/Constraint satisfaction problem|CSP]] problem  can be solved with a [[Search strategies|search]] on a tree.
The first step is to order the variables then we can assign a variable to each level of the tree and at each level there is going to be a node for each possible value of the variable. Each leaf would correspond to a full variable assignement (not necessarely correct). 
The resulting tree will have a d cardinality at each level and the number of possible leaves is going to be $d^n$.

A CSP algorithm that uses a tree search has 3 degree of freedom:
- the choice of ordering variables ([[Search euristics]])
- the choice of ordering of values to be assigned([[Search euristics]])
- the choice of propagation carried to each node (none: [[A posteriori algorithms]], some: [[Propagation algorithms]], [[Look ahead]])