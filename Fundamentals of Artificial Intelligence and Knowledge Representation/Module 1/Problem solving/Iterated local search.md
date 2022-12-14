It is a set of [[Meta heuristics]] rules to improve [[Iterative improvement - hill climbing]] search.
It search as efficently as possible the first solution and then tries to escape the local optima with some perturbation steps.
Pseudo code:
```python
def IterativeLocalSearch(s):
	s_star = localSearch(s)
	while not termination_conditions:
		s_ = perturbation(s_star, history)
		s_star_ = localSearch(s_)
		s_star = ApplyAcceptanceCriterion(s_star, s_star_, history)
	return s_star
```