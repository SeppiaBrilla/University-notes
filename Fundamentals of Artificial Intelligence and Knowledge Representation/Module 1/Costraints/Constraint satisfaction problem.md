Many artificial intelligence problems can be seen as constrant satisfaction problems: we can model our problem as finding a state that meets a given sets of constraints.

## Formal definition
A CSP (Constraint Satisfaction Problem) is defined on a finite set of variables:
-  $(x_1, x_2, \dots, x_n)$ decision that we have to take
- $(d_1, d_2, \dots, d_n)$ domains of possible values
- a set of constraints

A constraint $c(x_{i_1}, x_{i_2}, \dots, x_{i_k})$ between k variables is a subset of the cartesian product $d_{i_1} \times d_{i_2} \times \dots \times d_{i_k}$ that specifies the values of the variables that are compatible with each other. The subset must be expresses in terms of relationship.
A solution for the CSP problem is a set of variables values that satisfies all the constraints.

### pseudocode
```python
def CSP_resolver():
	state = []
	while len(nextAssignement(state)) > 0
		state.append(nextAssignement(state))
		if state.metAllConstraints():
			return state
	return "Failure"

```

two approaches:
- [[CSP as a tree search problem]]
- [[Consistency tecnique]]