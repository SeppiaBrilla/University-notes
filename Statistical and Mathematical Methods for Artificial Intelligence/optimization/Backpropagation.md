The [[The chain rule for functions of vectors]] is often used in deep networks where de function value $y$ is computed as the composition of many functions:
$$
y = (f_k \circ f_{k-1} \circ \dots \circ f_1)(x) 
$$
where $x$ is the input and every function $f_i$ has its parameters.
Every function $f_i$ can be written as: 
$$
f_i(x_{i-1}) = \sigma (A_{i-1}x_{i-1} + b_{i-1})
$$
where $x_{i-1}$ is the output of the previus function and $\sigma$ is an activation function (??).
In order to train the model we require to compute the [[loss function]] $L$ for each function.
For example if:
$$
\begin{align}
f_0 &= x \\
f_i &= \sigma_i(A_{i -1}x_{i - 1} + b_{i - 1})
\end{align}
$$
we may want to find $A_j,b_j$ for $j = 0, \dots , K-1$ such as the square loss:
$$
L(\sigma) = ||y - f_k(\sigma, x)||^2
$$
is minimized where $\sigma = \{A_0,b_0,\dots,A_{k - 1}, b_{k - 1}\}$.
The chain rule allow us to determinate the partial derivatives as:
$$
\begin{align}
\frac{\partial L}{\partial \Theta_{k -1}} &= \frac{\partial L}{\partial f_k} \frac{\partial f_k}{\partial \Theta_{k - 1}}\\
\frac{\partial L}{\partial \Theta_{k -2}} &= \frac{\partial L}{\partial f_k} \frac{\partial f_k}{\partial f_{k-1}} \frac{\partial f_{k-1}}{\partial \Theta_{k-2}}\\
\frac{\partial L}{\partial \Theta_{k -3}} &= \frac{\partial L}{\partial f_k} \frac{\partial f_k}{\partial f_{k-1}} \frac{\partial f_{k-1}}{\partial f_{k-2}}\frac{\partial f_{k-2}}{\partial \Theta_{k-3}}\\
&\dots
\end{align}
$$
At every steps we must compute each partial derivative of the previus steps and so, most of them can be reused in order to avoid their computation.
This tequnique is called Backpropagation
