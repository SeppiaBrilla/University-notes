It is an approach for solving [[Satisfiability Modulo Theory (SMT)]] problems. Instead of compiling SMT problems to [[SAT]] (like with the [[Eager approach to solve SMT]]), we integrate SAT solvers with theory-specific decision procedures.
Basic idea:
```python
def TCDLC(formula, assigments):
	if pre_processing(formula, assignement) == "conflict": # check with some domain knowledge non-SAT dependant
		return False
	f_p = T2B(formula) # Boolean abstractions
	a_p = T2B(assignements) # Boolean abstractions
	
	while True:
		l = decide_next_literal(f_p, a_p)
		while True:
			status = propagate(f_p, a_p, l)
			if status = "SAT": return B2T(a_p)
			else if status = "UNSAT":
				level = conflict_analysis(f_p, a_p)
				if level = 0: return False # unsatisfiable
				backjump(level, f_p , a_p)
			else: break
```