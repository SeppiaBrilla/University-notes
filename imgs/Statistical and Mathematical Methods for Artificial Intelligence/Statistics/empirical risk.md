The empirical risk is a function used in the [[Training or parameter estimation for learning process of AI]] when the [[Define a model for learning process in AI|model]] is a deterministic function that allow us to minimize the [[loss function]].
$$
R_{emp}(f,X,Y) = \frac{1}{N} \sum_{n = 1}^N l(y_n,\hat{y_n})
$$
where $N$ is the number of data we have, $X$ is our data, $l$ is the [[loss function]], $y_n \in Y$ is the real label for the parameter $x_n \in X$ and $\hat{y_n} = f(x_n, \Theta)$, is the label predicted by f (our [[Define a model for learning process in AI|model]]) for the parameter $x_n$. 
The whole function is minimized on the parameter $\Theta$ in which depends on the [[Define a model for learning process in AI|model]] we have chosen. 