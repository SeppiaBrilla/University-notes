Iterative methods are numerical methods that approximate a solution using a procedure with a large (or infinite) amount of steps.
The basic idea is to costruct a sequence of vectors $x_k$ that converge to the right solution:
$$
x^* = \lim_{k \to \infty }x_k 
$$
where $x^*$ is the exact solution and the starting $x_0$ is given
the [[Truncation error| truncating error]] is due to the fact that is impossible to perform an infinite amount of steps and the algorithm stops after a finite number of steps $k^*$. The total costs of the algorithm is $k^* * c_{it}$ where $c_{it}$ is the cost for each iteration.
Two examples of iterative methods are:
- *stationary iterative methods* 
     $$
   x_{k+1} = Bx_k + f
   $$
    where $B$ is called *iteration matrix* and $f$ is a vector obtained from $b$
- *gradient-like methods* 
    $$
    x_{k+1} = x_k + a_k\boldsymbol{p}_k
  $$
    where $a_k \in \mathbb{R}$, $\boldsymbol{p}_k$ is a vector called *direction*.
    If $A$ is symmetric and [[positive definite]] and the vector $\boldsymbol{p}_k$ have the *conjuancy* property, (i.e. $\boldsymbol{p}_k^T A\boldsymbol{p}_k = 0 \; if \; i \neq k$ ) then the method is called *Conjungate gradients*.

All those methods require a matrix-vector multiplication per iteration. Hence the complexity is up to $O(n^2)$ per iteration.
The stopping criteria ($k^*$ value) for iterative methods are:
- defined the residual $\boldsymbol{r}_k = b -Ax_k$ at iteration $k_i$, stops the algorithm when:
    - $||\boldsymbol{r}_k|| \leq \epsilon$  (absolute criterion)
    - $||\frac{\boldsymbol{r}_k}{b}|| \leq \epsilon$ (relative criterion)
- $||x_{k+1} - x_k|| < \tau$ (absolute criterion)

