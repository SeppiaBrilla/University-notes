Constrains the number of variables taking certain values.
Example:
$$
\begin{align}
&\text{among}([X_1, \dots, X_k], v, l, u) \; \text{iff} \; l \leq |\{i|X_i \in v, 1 \leq i \leq k\}| \leq u \\
&\text{among}([1,5,3,2,5,4],\{1,2,3,4\},3,4)
\end{align}
$$