The SVD is a data-driven generalization of the [[fourier transform]] and it is really usefull in every data reduction algorithm.
It is based on [[projection]] : ([[projection in practice (multi dimensions)]]) 
Any matrix can be factorize as the product of three matrices:
$$
\begin{aligned}
A &\in \mathbb{R}^{n \times m}\\
U &\in \mathbb{R}^{n \times n}\\
V &\in \mathbb{R}^{m \times m}\\
A &= U * \Sigma * V^T
\end{aligned}
$$
Where $U$ and $V$ are [[orhonormality|orthonormal]] and $\Sigma$ is a diagonal matrix with the ordered (from the biggest to the smallest $\rightarrow$ from the more important to the liest important) eigenvalues of $A$ as the elements. 
The elements of $U$ are called the "_left singualr vectors_"  and the elements of $V^T$ are called the right singual vectors. This decomposition always exists.

Demonstration:
$$
\begin{aligned}
A^TA =& \; (U * \Sigma * V^T)^T * (U * \Sigma * V^T) \\
=& \; V * \Sigma^T * U^T * U * \Sigma * V^T \\
=& \; V * \Sigma^T * I * \Sigma * V^T \\
=& \; V * \Sigma^2 * V^T \\
\Rightarrow&
A^TAV= V*\Sigma^2 
\\ \\
AA^T =& \; (U * \Sigma * V^T) * (U * \Sigma * V^T)^T \\
=& \; U * \Sigma * V^T * V * \Sigma^T * U^T \\
=& \; U * \Sigma^T * I * \Sigma * U^T \\
=& \; U * \Sigma^2 * U^T \\
\Rightarrow&
AA^TU= U*\Sigma^2
\end{aligned}
$$