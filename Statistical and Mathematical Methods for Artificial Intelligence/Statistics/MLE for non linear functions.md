We may want to use a non linear function as a model in order to better capture more data.
In order to do so we incapsulate our data in a non linear trasforamtion $\Phi(x)$ such as:
$$
\Phi(x) = 
\begin{bmatrix}
\Phi_0(x)\\
\Phi_1(x)\\
\Phi_2(x)\\
\vdots\\
\Phi_{K-1}(x)\\
\end{bmatrix}
= 
\begin{bmatrix}
1\\
x\\
x^2\\
\vdots\\
x^{K - 1}
\end{bmatrix}
$$
so that: 
$$
p(y| x,\theta) = N(y| \Phi^T(x)\theta, \sigma^2) \Rightarrow y = \Phi^T(x)\theta + \epsilon
$$
where $\epsilon$ is the "noise" (error) that looks like: $N(0,\sigma^2)$.
We now wont to minimize:
$$
\min_\sigma ||y - \Phi(x)\sigma||
$$
and in order to do so we can use several methods like [[Gradient method]] or [[Normal equations]]