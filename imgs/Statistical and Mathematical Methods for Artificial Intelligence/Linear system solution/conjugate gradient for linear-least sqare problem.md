The gradient method is an iterative method that solve the [[linear least-squares problem|lls problem]] computing the [[SVD]] decomposition and then compute x* as:
$$
\underline{x}*= \sum_{i = 1}^{r} \frac{u_i^T * b}{\sigma_i}v_i \; \in \mathbb{R}^n
$$
x* is one if the infinite solutions when Rank(A) < n