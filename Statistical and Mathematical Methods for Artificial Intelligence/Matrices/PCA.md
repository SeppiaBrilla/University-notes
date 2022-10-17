The PCA is a unsupervised ML algorthm that's provide an easy way to shrink the number of dimensions (and data as a concequence) needed to represent some data with the minimum loss.
This algorithm is based upon the [[SVD]] matrix decomposition and it is computed as follow (for a matrix $A \in \mathbb{R}^{n \times m}$):

1) compute the mean of every vector of the matrix 
$$
\bar{a}_j = \frac{1}{n} \sum_{i=1}^{n} a_{ij}
$$
2) compute the mean matrix
$$
 \bar{A} = 
 \begin{bmatrix}
 1 \\
 \vdots\\
 1
 \end{bmatrix}	 
 \bar{a}
$$
3) subtract $\bar{X}$ from $X$ result in the mean subtracted data $B$:
$$
B = A - \bar{A}
$$
4) the covariance matrix of the rows of $B$ is given by:
$$
C = \frac{1}{n - 1} B * B
$$
5) the first principal component $u_i$ is given as:
$$
u_1 = \arg\max_{||u_1||=1} u_1*B*Bu_1
$$
which is the eigenvector of $B*B$ corresponding to the largest eigenvalue. 

And so:
```python
(u, s, v) = np.linang.svd(B)
u_1 = u[1, :]
```
