This process deeply depends on the type of [[Define a model for learning process in AI|model]] chosen:

## Deterministic function model
In the case of a deterministic function we want the model to minimize the distance between the real label ($y$) and the predicted one ($\hat{y}$). In order to do this we use a special function called _[[loss function]]_. After we have defined the [[loss function]] we precede to minimize it with a function called [[empirical risk]].
In the special case we choose the [[loss function]] to be $l(y, \hat{y}) = (y - \hat{y})^2$ then the [[empirical risk]] function became identical to the [[linear least-squares problem]].
$$
\begin{align}
\frac{1}{N} \sum_{n = 1}^N &(y_n - \hat{y_n})^2 \\
\Rightarrow\\
\frac{1}{N} \sum_{n = 1}^N &(y_n - f(x_n,\Theta))^2 \\
\Rightarrow\\
\frac{1}{N} \sum_{n = 1}^N &(y_n - \Theta^T x_n)^2 \\
\Rightarrow\\
\frac{1}{N} ||&y_n - \Theta^T X|| \\
\end{align}
$$
We can also define the _Expected risk_ as:
$$
R_{true}(f) = \mathbb{E}[l(y,f(x))]
$$
where $\mathbb{E}$ is the [[Expected value]], $l$ is the loss function and $f$ is our [[Define a model for learning process in AI|model]].
The _Expected risk_ is computed on the test set.

## Probabilistic model

A way to estimate the parameters of a probabilistic model is to use the [[Maximum likelihood estimation]] technique. 