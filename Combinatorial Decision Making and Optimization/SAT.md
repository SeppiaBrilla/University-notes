Any decision (and [[Combinatorial Decision Making and Optimization/Constraint satisfaction problem|optimization]]) problem can be described as a proposition formula to satisfy. Doing so, allows using logic formuals to find a solution to a given problem. 
SAT tries to "satisfy" a given logic formula using logic. SAT is an NP-complete problem and, thus, finding a solution to a problem with SAT can be very costly, even tho modern algorithms can find a solution (if it exists) in a very efficient way.

## Basic SAT solver idea: DPLL

```python
def DPLL(X):
	X:= unit_resolve(X)
	if X is empty():
		return True # SAT
	if not bottom() in X:
		U = Choose_a_random_variable(X)
		return Max(DPLL(X.append(U)), DPLL(X.append(!U)))
	return False # Not SAT
```
Where unit_resolve is a function that, given a formula and a set of predicates, derives new predicates. 


