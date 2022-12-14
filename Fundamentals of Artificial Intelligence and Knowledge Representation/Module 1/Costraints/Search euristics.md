The search euristics in as [[Constraint satisfaction problem|CSP]] algorithm determine:
- The order of the variables to assign. The two most commonly used tecnique are __first fail__ that chooses the next variable as the one with the least remaining values and __most constrained principle__ that chooses the next variable as the one with the largest amount of constraints
- The value to assign to a varible. There are no general rules but the rationale is try the values that are most likely to succeed (__least constraining principlple__)

A further classification is as follow:
- __Static euristics__: determine the variable and value order before starting the search and this order remains unchanged throught the research
- __Dynamic heuristics__: select the new variable each time a value is selected. The computation of the new variable may have the same complexity as the computation of the original problem, so a trade of has to be made