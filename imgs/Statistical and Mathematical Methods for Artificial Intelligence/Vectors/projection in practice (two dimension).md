The [[projection]] $\phi_U(x)$ where: $\phi_U:V \rightarrow U, U \subseteq V$ and $x \in V$ finds the "closest" element in $U$ to $x$, in other words $\phi_U$ minimize the distance between $\phi_U(x)$ and $x$ $\Rightarrow$ 
$$
\phi_U(x) = minimal \: ||x - \phi_U(x)||
$$
It follows that the segment $\phi_U(x) - x$ is [[orthogonality|orthogonal]] to $U$.
That means that: $<\phi_U(x),x> = 0$ ([[Dot product]]).
The [[projection]] $\phi_U(x)$ is an element of $U$ and, therefore a multiple of the basis vector $b \in U$. Therefore: $\phi_U(x) = \lambda b$ for some $\lambda \in \mathbb{R}$.

The [[projection matrices|projection matrix]] for two dimensions is:
$$
P_\phi = \frac{bb^T}{b^Tb}  \; b\in U
$$

See also: [[projection in practice (multi dimensions)]]