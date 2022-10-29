LDA is a supervised ML algorithm that aim to reduce dimensions (just like [[PCA]]) but also wants to keep the maximum difference between cluster of data so that is easier to visualize the clusters.
The main difference is on how the data is centered: not by the center of all data but only by the center of each data cluster so that each elements spans only around the his cluster.
Implementation:
1) For each cluster ($C_1,\dots,C_K$)  we compute the mean of each one of them:
	$$
	c_k(X) = \frac{1}{N_K}\sum_{i \in I_k} x_i
  $$
	Where $N_K$ is the number of element in the cluster K and $I_K$ is set of the indexes of each element of the cluster K in the matrix $X = (x_1,\dots, x_n)$ 
2) Compute the global center:
	$$
	c(X) = \frac{1}{N} \sum_{i = 1}^{N} x_i
	$$
3) Compute the "_within scatter matrix_":
	$$
	\begin{aligned}
	&X_{k,c} = X_k - c_k(X_k)\\
	&X_w = (X_1,c,\dots,X_{k,c})\\
	&S_w = X_w * X_w^T
	\end{aligned}
	$$
4) Compute the "_Between scatter matrix_":
	$$
	\begin{aligned}
	&\bar{X_k} = (c_1,\dots,c_k) \in \mathbb{R}^{d \times N_k}\\
	&\bar{X} = (\bar{X_1},\dots,\bar{X_k})\\
	&\bar{X_c} = \bar{X} - c(X)\\
	&S_b = \bar{X_c} * \bar{X_c^T}
	\end{aligned}
	$$
5) We want to project our data with the maximum distance between clusters while keep the within cluster distance as little as possilble. To do so we maximize the function:
	$$
	H(q) = \frac{q^TS_wq}{q^TS_bQ}
	$$
	Where $Q = (q_1,\dots,q_k)$ are the vector of the matrix of dimension $k$ on which we want to project our data. $Q$ is composef of orthonormal vectors.
	We can rewrite the above function as: 
	$$
	\max_q q^tS_wq \; s.t. \; q^tS_bq = 1
	$$
	$S_w$ is symmetrical ($S_W^T = (X_wX_w^T)^T = (X_wX_w^T) = S_w$) so, if it is [[positive definite]], we can compute the Cholesky decomposition: $S_W = LL^T$.
	Where $L \in \mathbb{R}^{d \times d}$ is a lower triangular matrix. 
	If $S_w$ is not [[positive definite]] we can make it [[positive definite]] by doing:
	$$
	\begin{align}
	&S_w = S_w + \epsilon I\\
	&\epsilon \approx 10^{-6}
	\end{align}
	$$
	 Now we can compute $W$ a matrix containing all the egenvectors of $L^{-1}S_bL$
	 and then keep only the first k elements of it ($W_k \in \mathbb{R}^{d \times k}$).
	Finally $Q = L^{-T}W$ and $Q^T$ will be the projection matrix of LDA 


 