
Every problem formulated in [[linear programming]] and, more in general, [[Operations research]] has a "dual": a problem with the same optimal value that focus more on evaluation of resources rather than allocation.
We can formulate the dual problem as follows:
let $P:\max(cs) \; s.t. \; Ax = b, \; x \geq 0$, the dual of P is: $D(P): \min(by) \; s.t. \; A^T y \geq c, \; y \in \mathbb{R}^m$ with 
- a variable $y_i$ for each constraint $\sum_{j=1}^n a_{i,j}x_j = b_i, \; i = 1,\dots,m$ of P
- a constraint $\sum_{i = 1}^m a_{j,i}, x_j = b_i, \; j = 1,\dots,n$ for each variable $x_j$ of P

### Duality properties
- The dual of a dual is the primal
- Weak duality: the cost of any feasible solution of the primal is ≤ the cost of any solution of the dual
	- If P unbounded, D(P) unfeasible
	- If D(P) unbounded, P unfeasible
- Strong duality: if primal and dual are feasible they have same optimal

### Dual simplex
We can apply the dual simplex algorithm on a problem to find the optimal solution, the dual simplex works in an "opposite" way: starting from an optimal solution it moves towards a feasible one while preserving optimality. (it removes from the basis the value with the minimum negative value and add the one with the maximum negative ratio). 

We can also use a hybrid approach: from a dual solution y look for a primal solution x satisfying certain optimality conditions. A “reduced problem” P′ is solved, if possible; if not, from D(P′) a new dual solution y′ is derived and the procedure is repeated.

The duality property is also very useful for [[Sensitivity analysis]].