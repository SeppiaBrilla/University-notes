Any linear system can be solved by calculating the inverse of the matrix $A$:
$$
Ax=b \Rightarrow A^{-1}Ax = A^{-1}b \Rightarrow x = A^{-1}b 
$$
To solve a linear square system using a direct method we first compute the "*LU*" maxtrix factorization then solve two triangular system:
$$
\begin{align}
&Ax = b\\
&A = LU\\
&Ly = b\\
&Ux = y 
\end{align}
$$
Where $L$ is a lower triangular matrix
$$
\begin{bmatrix}
    x_{11}       & 0 & 0 & \dots & 0 \\
    x_{21}       & x_{22} & 0 & \dots & 0 \\
    \dots  &\dots & \dots & \dots & \dots \\
    x_{n1}       & x_{n2} & x_{n3} & \dots & x_{nn}
\end{bmatrix}
$$
And $U$ is an upper triangular matrix
$$
\begin{bmatrix}
    x_{11}       & x_{12} & x_{13} & \dots & x_{1n} \\
    0       & x_{22} & x_{23} & \dots & x_{2n} \\
    \dots  &\dots & \dots & \dots & \dots \\
    0       & 0 & 0 & \dots & x_{nn}
\end{bmatrix}
$$
Solving a triangular system costs $O(\frac{n^2}{2})$ and the computation of the inverse matrix $A^{-1}$ costs $O(n^3)$

The *LU* factorization can't be performed if the matrix $A$ is [[non-singular]] and the algorithm is [[Unstable algorithm|unstable]].
In order to solve those problems we can perform the *pivoting factorization* $PA = LU$
where $P$ is a [[permutation matrix]]. The *pivoting factorization* is stable and can be performed on any [[non-singular]] matrix. The cost of resolving a linear system with the *pivoting factorization* is $O(\frac{2}{3}n^3)$ 