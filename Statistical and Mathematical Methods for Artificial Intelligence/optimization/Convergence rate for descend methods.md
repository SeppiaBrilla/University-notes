an [[Iterative algorithms]] has convergence rate $q$ if:
$$
\begin{align}
&\frac{||x_{k+1} - x^*||}{||X_k - x^*||^q} < c \\
&\Updownarrow\\
&\frac{||e_{k+1}||}{||e_k||^q} \\
&\Rightarrow ||e_{k+1}|| < c||e_k||^q 

\end{align}
$$

- if q = 1 then the convergence rate is called linear $||e_{k + 1}|| \leq c||e_K|| \rightarrow 0 < c < 1$. The [[Gradient method]] has a linear convergence rate
- if 1< q < 2 then the converge rate is iperlinear