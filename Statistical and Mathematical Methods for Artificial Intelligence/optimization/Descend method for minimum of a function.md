the descend method is a family of [[Iterative algorithms]] to find a [[Local minimum]] of a function $f$ where we compute $x_{k+1}$ as:
$$
\begin{align}
P_k &\in \mathbb{R}^n\\
\alpha_k &\in \mathbb{R}^+\\
x_{k+1} &= x_k + \alpha_kP_k
\end{align}
$$
$P_k$ is the direction in where we search the minimum and $\alpha_k$ is the length of the step.
$P$ is a descending direction for $f$ in $x$ if $\exists \bar{\alpha} > 0$:
$$
f(x + \alpha P) < f(x) \; \; \forall \alpha \in [0, \bar{\alpha}]
$$
if $f$ is continuos, differentiable in a neighbourhud of $x \in \mathbb{R}^n, \; p \in \mathbb{R}^n, \; p \neq 0$ and $p^T* \nabla f(x) < 0$ then $p$ is a descent direction for $f$ in $x$.
See also [[Convergence rate for descend methods]]
