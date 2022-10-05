The multi dimensional case of the projection is very similar to the two dimension case ([[projection in practice (two dimension)|see here]]).
The main difference is, of course, the basis vectors that produces $U$.
Therefore:
$$
\phi_U(x) = \sum^{m}_{i=1}\lambda_Ib_i = B\lambda
$$
	Where: $B \in \mathbb{R}^{n \times m}= [b_1, ..., b_m]$ and $\lambda \in \mathbb{R}^m = [\lambda_1, ..., \lambda_m]$   
In this case $\phi_U(x)$ must be orthogonal to every element of $B$:
$$
\begin{aligned}
<b_1,x - \phi_U(x)> \; =& \; b_1^T(x - \phi_U(x)) = 0 \\
\vdots\\
<b_m,x - \phi_U(x)> \; =& \; b_m^T(x - \phi_U(x)) = 0 \\
&\Longrightarrow \\
\begin{bmatrix}
b_1^T \\
\vdots \\
b_m^T
\end{bmatrix}
\begin{bmatrix}
\\ 
x - B\lambda
\\ \;
\end{bmatrix}
= 0 &\Longleftrightarrow B^T(x-B\lambda) = 0 \\
&\Longleftrightarrow B^TB\lambda = B^T x
\end{aligned}
$$
The [[projection matrices|projection matrix]] is:
$$
P_\phi = B(B^TB)^{-1}B^T
$$
