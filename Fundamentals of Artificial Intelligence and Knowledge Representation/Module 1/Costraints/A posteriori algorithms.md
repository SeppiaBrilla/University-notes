Theta_p, theta_g and w are parameters that should be carefully chosen as they strongly influence the efficiency of the algorithms to find a solution to a [[Fundamentals of Artificial Intelligence and Knowledge Representation/Module 1/Costraints/Constraint satisfaction problem|CSP]] with an a posteriori verification of the constraints (create the solution then check if it is valid).

## Generate and Test (GT)
This algorithm generates all possible solutions then it test them. Very inefficient and slow

## Standard backtracking
Similar to GT but, at each step we check the constraints in order to avoid searching solutions that we already know do not satisfy the constraints.