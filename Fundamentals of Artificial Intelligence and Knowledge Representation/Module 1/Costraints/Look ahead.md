Is a type of [[Propagation algorithms]] for [[Constraint satisfaction problem|CSP]].
It is very similar to [[Forward checking]] but, if [[Forward checking]] updates the possible values only by deleting the one incompatible with the current choice, Look ahead update the values of each variable also by looking at the updated value of the previous one.
There are two look ahead implementations:

## partial look ahead (PLA)
it does update the possible values of current variable looking at the next one.
Example:
$$
\begin{align}
&X_0 < X_1 < X_2 < X_3 \;\;\;\;\;\; X_0, X_1, X_2, X_3 \in [0,1,2,3]\\
&X_0 = 0\\
&X_1 = [1,2] \; \; \text{because x1 must be lower than x2 and 3 does not have a possible value in x2}\\
&X_2 = [1,2] \; \; \text{because x2 must be lower than x3 and 3 does not have a possible value in x3}\\
&X_3 = [1,2,3] \; \; \text{no checks because there aren't other variables}

\end{align}
$$

## full look ahead (FLA)
it does update the possible values of current variable looking at the next one and it's predecessor.
Example:
$$
\begin{align}
&X_0 < X_1 < X_2 < X_3 \;\;\;\;\;\; X_0, X_1, X_2, X_3 \in [0,1,2,3]\\
&X_0 = 0\\
&X_1 = [1,2] \; \; \text{because x1 must be lower than x2 and 3 does not have a possible value in x2}\\
&X_2 = [1,2] \; \; \text{because x2 must be lower than x3 and 3 does not have a possible value in x3}\\
&X_3 = [2,3] \; \; \text{because x3 must be greater then x2 and 1 does not have a possible value in x2}

\end{align}
$$