The gradient method is a [[Descend method for minimum of a function]] that choose $P$ like $-\nabla f(x)$. 
__This method do not converge for any $\alpha$__. See [[choiche of alpha for descending methods]]
We can encrease the [[Convergence rate for descend methods| convergence rate]] speed of the gradiant method by introducing a new value $\Delta x_i$  to the equation:
$$
\begin{align}
&\Delta x_i = x_i - x_{i -1}\\
&x_{i + i} = x_i - \alpha \nabla f(x) + \alpha \Delta x_i
\end{align}
$$