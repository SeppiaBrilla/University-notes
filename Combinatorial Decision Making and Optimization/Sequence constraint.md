Constrains the number of values taken from a given set in any sub sequence of q variables.
Also known as amongseq constraint. (See also [[Among constraint]])
$$
\begin{align}
&\text{sequence}(l,u,q, [X_1, X_2, \dots, X_k], v) \; \text{iff} \; \text{among}([X_1, X_2, \dots, X_k], v, l, u) \forall i \in \{1, \dots, k-q+1\}\\
&\text{sequence}(1,2,3[1,0,2,0,3],\{0,1\})
\end{align}
$$