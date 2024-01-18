It is a [[Operations research|OR]] framework based on linear systems of inequalities. It is a good solution when an optima allocation of a limited number of resources in needed.

A few definitions:
- __Feasible solution__ : assignment satisfying all the constraints
- __Feasible region__: set of all solutions
- __Goal__: find a point within the feasible region where the objective function has maximal value

### Extreme point property
If an optimal solution for an LP problem exists, then there is one at the extreme point of its feasible region. Even though the number of extreme point is finite, the search space could be exponential and so a brute force search is not a good approach. 

## Canonical form and LP problem representation

An LP in the canonical form can be represented like:
$$
\begin{align}
\max &\sum_{i = 1}^n c_i x_i\\
\text{s.t.}&\sum_{i = 1}^n a_{ji}x_i \leq b_j & 1 \leq j \leq m\\
&x_i \geq 0 & 1 \leq i \leq m\\
\end{align}
$$
Where m is the number of linear constraints, n is the number of __non-negative__ variables.
$a_{ji}, b_j, c_i$ are known parameters with values in $\mathbb{R}$ and $\sum_{i = 1}^n c_i x_i$ is the function to maximize. This representation can be easily transformed in a matrix form to be easier to solve.
The standard form is the same but with equalities instead of $\leq$. We can convert the canonical form to standard form by adding a new parameter $y_i \geq 0$ to compensate for the "remaining" part.  


# Simplex algorithm

Is an algorithm for solving LP problems. It starts the search in an extreme points and the greadly moves toward the better solution. If the search space is convex, we're not afraid of being stuck on an [[Local minimum]] therefore the solution is optimal.

## Steps

### Find a solution
Given an LP problem P in standard form, a basis of P is a subset of m $\leq$ n variables s.t. columns $A^{i1},\dots,A^{im}$ form an m × m invertible matrix. 
We can rewrite P by separating basic ($X_B$) from non-basic ($X_N$) variables. By setting $x_N = 0$, P becomes $\max(c_Bx_B)$ s.t. $A_Bx_B = b$ hence $x_B = A^{-1}_Bb\in \mathbb{R}^m$ with objective value $c_BA^{-1}_Bb$.
This solution is called a basic solution for B. Each basic feasible solution ($\forall_{i = 1}^m (x_B)_i \geq 0$) is an extreme point of the feasible region. 
If we have $\forall_{i = 1}^m (x_B)_i \geq 0$ then the solution is non-degenerate, and it represents a unique basis.
Simplex method iteratively considers BFS $\tilde{x_1}, \tilde{x_2}, \dots \text{ s.t. } c\tilde{x}_k \geq c\tilde{x}_{k-1}$.

### Choosing the next solution
The next solution is chosen by choosing the variable that increase more the objective value and pivoting it with a value in the previous basic solution s.t. the new solution remain a base.

### Optimality
At each iteration, the symplex algorithm performs an optimality check: if all the reduced costs are $\leq 0$ then the solution is optimal. This condition is sufficient but not necessary, therefor we can have an optimal solution even if the optimality check fails.

## Unboundedness
In some cases we can have an objective function whose values are unbounded by the constraints, therefore there is no optimal solution. (e.g. $\max x, y \leq 5$, all solution with y greater than 5 are good) => Symplex algorithm performs an Unboundedness check.

### Pseudocode
```python
def symplex(P:'standard_form_LP') -> 'LP_solution':
	k = 0
	b = []
	b[k] = feasible_base(P)
	if unbounded(P):
		return None
	while True:
		if isOptimal(b[k],P):
			return b[k]
		x_in = choose_next_in_variable(b, P)
		x_out = choose_next_out_variable(b, P)
		
		b[k + 1] = b[k] - [x_out]
		b[k + 1] = b[k] - [x_in]
		k +=1
```

Every Linear programming problem has also a [[Duality|dual]].

Passing from solving linear programming problems from real number to integer is very hard and increase the complexity a lot. ([[LIP]])  
