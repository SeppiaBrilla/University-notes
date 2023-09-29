SMT concerns the study of the satisfiability of formulas with the respect to some theories (integer arithmetic, strings, array, ...).
It extends [[SAT]]. 
There are two main approach to solve an SMT problem.
- [[Eager approach to solve SMT|Eager approach]]: translates upfront the SMT formula in an equi-satisfiable SAT formula, and solves it with a SAT solver
- [[Lazy approach to solve SMT|Lazy approach]]: uses ad-hoc procedures for the background theory in a “lazy” way

Some interesting way we can use SMT:
- [[EUF theory]]
- [[Arithmetic theory]]
- Array theory
- Theory of bit-vectors
- Theory of strings
- [[LRA theory]]
- [[LIA theory]]
- [[Difference logic theory]]