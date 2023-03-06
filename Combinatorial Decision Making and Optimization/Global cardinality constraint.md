Constrains the number of times each value is taken by the variables.
Example:
$$
\begin{align}
&gcc([X_1, \dots, X_k], [v_1, \dots, v_m], [O_1, \dots, O_m]) \; \text{iff} \; \forall j \in \{1, \dots, m\} O_j = |\{X_i| X_i = v_j, 1 \leq i \leq k\}|\\
&gcc([1,1,3,2,3],[1,2,3,4],[2,1,2,0])
\end{align}
$$