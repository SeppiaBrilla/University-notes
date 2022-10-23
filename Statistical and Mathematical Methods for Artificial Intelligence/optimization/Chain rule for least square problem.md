 We can use the [[The chain rule for functions of vectors|chain rule]] to solve the [[linear least-squares problem]].
To solve the $\min ||Ax - b||^2_2$ (renamed as $||\Phi \theta - y||^2_2$) we can identify two functions:
$e = \Phi \theta - y$ and $L = ||e||^2_2$ where the argument for g is $\phi$ and use the chain rule for $L \circ e$.
$$
\begin{align}
\nabla L(\phi) &= \frac{\partial L}{\partial e} \frac{\partial e}{\partial \phi}\\
\frac{\partial L}{\partial e} &= 2 e^T\\
\frac{\partial e}{\partial \phi} &= \Phi\\
&\Longrightarrow\\
\nabla L(\phi) &= 2(\Phi \theta - y)^T \Phi \\
&= 2 \theta^T \Phi^T \Phi - 2 y^T \Phi
\end{align}
$$

So, in order to solve the [[linear least-squares problem]] we must minimize $L(\phi)$ and, in order to do so we must compute the $\nabla L(\phi) = 0$.
