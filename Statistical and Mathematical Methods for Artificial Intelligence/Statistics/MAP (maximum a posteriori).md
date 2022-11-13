The MAP, maximum a posteriori analisys is a way to prevent [[overfitting]] when we're using a probabilistic model to predict a label.
The idea is similar to the [[Maximum likelihood estimation]] but instead o maximizing $p(X|\theta)$ we maximize $p(\Theta|X)$. This is possible because of the [[Bayes theorem]]. In practice we want to avoid overfitting and to do so we multiply the $L$ function by the probability of Theta. So we can use the [[Bayes theorem]] and get the described result as follow:
$$
\begin{align}
\max_\theta L(\theta) * p(\theta) &= \max_\theta p(X|\theta)*p(\theta)\\
&= \max_\theta p(\Theta|X) * p(X)\\
&= \max_\theta p(\Theta|X)
\end{align}
$$