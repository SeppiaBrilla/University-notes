There are several different methods to encode a [[NLP]] problem into an equivalent [[Linear programming|LP]] problem.

## Newton's method 

If the problem is in the [[NLP|generic form]], f is constant, m is 0 and p, n are both 1, we can solve the h function using the newton method to solve it (Newton's method is a [[Descend method for minimum of a function]] where $x_{k+1} = x_k - \frac{f(x_K)}{f'(x_K)}$. We can also use [[Gradient method]])

# Linearization

An alternative approach is to linearize the non-linear constraints, but this method only works with bounded variables.

## Reification

If the non-linear function is of the form $a \vee b$ with a and b linear functions, we can use reification to linearize the function.
 
Given a constraint $C(x_1,\dots,x_k)$ a (full) reification of C is a boolean variable b s.t. $b = true \Leftrightarrow C(x_1,\dots,x_k)$. An integer reification is the same with 1 instead of true, while a half reification is when $b = 1 \Rightarrow C(x_1,\dots,x_k)$.
We are looking for half reifcation of constraints.

### Big-M trick
To encode $C_1 \vee \dots \vee C_m$, we introduce m new variables b with value between 0 and 1, and we impose the sum of them to be more than one. Then, to assign a value to the b variables, we can impose a new constraint for each constraint $C_i$: if we assume $C_i \equiv \sum_{i,j} a_{i,j}x_j \leq \beta_i$, we can add a constraint $\sum_{i,j} a_{i,j}x_j - \beta_i \leq M(1-b_i)$ with M a "big enough" constant.


## Min/max constraint

To linearize $y = \min(x_1,x_2)$, we can transform it in $(x_1 \leq x_2 \Rightarrow y = x_1) \vee (x_2 \leq x_1 \Rightarrow y = x_2)$ and linearize it via reification or add a new variable b s.t.:
$$
\begin{align}
&y \leq x_1\\
&y \leq x_2\\
&y \geq x_1 - (u_1 -l_2) * (1-b)\\
&y \geq x_1 - (u_2 -l_1) * b
\end{align}
$$
with $u_1, u_2$ upper bounds and $l_1,l_2$ lower bounds.


## Unary encoding

If D(x) is the domain of x we introduce |D(x)| binary variables with value 0 or 1 and impose $\sum_{k \in D(x)} b_k^x = 1 \wedge \sum_{k \in D(x)} b_k^x k = x$.