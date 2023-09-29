The expected value of a function $g: \mathbb{R} \rightarrow \mathbb{R}$ of a continuous [[Random variable]]  is a [[Statistic]] and it is given by:
$$
\mathbb{E}_x[g(x)] = \int_X g(x)p(x) \; dx
$$
or for a discrete [[Random variable]]:
$$
\mathbb{E}_x[g(x)] = \sum_{x \in X} g(x)p(x)
$$
where $X$ are the possible outcomes on the target space for $x$.

for [[multivariate random variable]]:
$$
\begin{align}
x &= [x_1,\dots,x_d] \in \mathbb{R}^d \\
\mathbb{E}_x[g(x)] &= 
\begin{bmatrix}
\mathbb{E}_{x_1}[g(x)]\\
\mathbb{E}_{x_2}[g(x)]\\
\vdots\\
\mathbb{E}_{x_d}[g(x)]
\end{bmatrix}
\end{align}
$$

The [[mean for density functions]] or [[mean for discrete random variables]] can be seen as a special case of the expected value where the $g$ is the identiy.