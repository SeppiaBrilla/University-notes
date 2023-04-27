It is an approach for solving [[Satisfiability Modulo Theory (SMT)]] problems. It tries to translate the problem into a [[SAT]] formula and solve it with a SAT solver.

## How

1) remove each function/predicate to reduce each atom to equalities between constants
	- Ackermann method
	- Bryant method
2) remove equalities to reduce to propositional logic