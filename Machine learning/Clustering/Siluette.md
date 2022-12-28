The siluette of a [[Clustering|cluster]] is a quality score whose values are standardized (0,1 or -1,1).
The siluette value encreases with the [[Separation]] between clusters and decreases for cluster with low [[cohesion]].
$$
\begin{align}
a_i &= \text{avg}_{j, y(x_j)=y(x_i)} \; dist(x_i,x_j)\\
b_i &= \min_{k \in Y, k \neq y(x_i)}(\text{avg} \; dist(x_i,x_j))\\
s_i &= \frac{b_i - a_i}{max(b_i,a_i)}  \in [-1,1]
\end{align}
$$
Where a measure the cluster sparsity of the cluster i, b measures the separation between clusters and s is the siluette of score of xi.