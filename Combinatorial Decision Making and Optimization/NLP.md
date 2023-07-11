It stands for Non-Linear Programming, which, is like [[Linear programming]] (thus, also an [[Operations research|OR]]) but with non-linear functions like $y = x^2 + \frac{1}{z}$. In order to solve this kind of problems, we can operate in two different ways:
- Encode the problem in an equally satifiable linear problem ([[From NLP to LP]])
- Use a specific NLP approach


## Generic form of an NLP problem

Generally, a NLP problem has the form:
$$
\begin{align}
\min &f(x);\\
&g_i(x) \leq 1 \; i = 1,\dots, m\\
& h_j(x) = 0 \; j = 1,\dots,p
\end{align}
$$
With $x \in \mathbb{R}^n$ and one of the $f,g_i,h_j$ a non-linear function