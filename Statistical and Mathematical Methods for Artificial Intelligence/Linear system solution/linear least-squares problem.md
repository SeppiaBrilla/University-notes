What happen if we have a [[Linear systems]] $Ax = b$ where $A \in \mathbb{R}^{m \times n}$, $x \in \mathbb{R}^n$ , $b \in \mathbb{R}^m$ and $m > n$?
The result is that we have no solution for such a problem but we can find the "best" approximation for such a solution.
The "best" solution is:
$$
min_{x \in \mathbb{R}^n} ||Ax - b||_2^2
$$
This new problem it is always solvable and:
- if rank(A) = n the solution is unique
- if rank(A) < n the solutions are infinite and they constitute a subspace of size n - r.