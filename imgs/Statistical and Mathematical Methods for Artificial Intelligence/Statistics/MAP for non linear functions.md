Just like in linear [[MAP (maximum a posteriori)]] we want to use the [[Bayes theorem]] to transform our maximization:
$$
p(\theta|X,Y) = \frac{p(Y|X,\theta)p(\theta)}{p(Y|X)}
$$
and we seek $\theta$ such that:
$$
\theta \in \arg \min\{-\log p(Y|X,\theta) - \log p(\theta)\}
$$
and so with $p(\theta) = N(0, b^2I)$ we obtain:
$$
\min ||y - \Phi \sigma||^2 + \frac{1}{b^2} ||\sigma||^2
$$
that is exactly the [[Hyperparameter tuning for learning process of AI|regularization]] where $\lambda = \frac{1}{b^2}$.