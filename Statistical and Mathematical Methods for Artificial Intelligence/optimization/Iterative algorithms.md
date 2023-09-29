An iterative algorithm that finds the [[Local minimum]] of a function $f$ creates a series of approximated $x^*$ that converges to the exact solution.
$$
x_k \rightarrow_{k \rightarrow \infty} x^*
$$
Starting from an initial guess $x_0$.
Those methos looks like: $x_k = G(x_{k-1})$. The procedure shold be infinite but it must be trucated at some point and that generate a [[Truncation error]].

## stopping criteria

- $||\nabla f(x_k)|| < \tau_1$ where $\tau_1$ is an arbitrary small value ([[Gradient]])
- $||x_{k+1} - x_k|| < \tau_2$  where $\tau_2$ is an arbitrary small value 
- $k \leq \underline{MAXK}$ where $\underline{MAXK}$ is an arbitrary big value 