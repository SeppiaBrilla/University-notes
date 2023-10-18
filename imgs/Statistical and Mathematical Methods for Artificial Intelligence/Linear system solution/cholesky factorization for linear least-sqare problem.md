The Cholesky factorization for the [[linear least-squares problem|lls problem]] is a direct method to find the solution.
1) we can rewrite the equation as: $A^TA = A^Tb$
2) we can factorize $A^TA$ with the Cholesky factorization in $A^TA = LL^T$ where $L$ is a lower triangular matrix. No pivoting is needed and this factorization always exist for $A^TA$ symmetric [[positive definite]]
3) $LL^T = A^Tb \Rightarrow Ly = A^Tb$, then $L^Tx = y$ 

The computational costs is: $O(\frac{n^3}{6})$ 