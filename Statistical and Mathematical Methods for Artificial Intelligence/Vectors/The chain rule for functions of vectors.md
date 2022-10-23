
The gradient of $f(x_1, x_2)$ where $f: \mathbb{R}^2 \rightarrow \mathbb{R}$ and $x_1, x_2: \mathbb{R} \rightarrow \mathbb{R}$ is defined as:
$$
\frac{\nabla f}{\nabla t} =
\begin{bmatrix}
\frac{\partial f}{\partial x_1} & \frac{\partial f}{\partial x_1}  
\end{bmatrix}
\begin{bmatrix}
\frac{\partial x_1}{\partial t} \\ \frac{\partial x_2}{\partial t}  
\end{bmatrix} = \frac{\partial f}{\partial x_1}\frac{\partial x_1}{\partial t} + \frac{\partial f}{\partial x_1} \frac{\partial x_2}{\partial t}
$$
where $\partial$ denotes the partial derivatives.

The partial derivatives of $f(x_1, x_2), x_1(s,t), x_2(s,t)$ where $f: \mathbb{R}^2 \rightarrow \mathbb{R}$ and $x_1, x_2: \mathbb{R}^2 \rightarrow \mathbb{R}$ is defined as:
$$
\begin{align}
\frac{\partial f}{\partial s} = \frac{\partial f}{\partial x_1}\frac{\partial x_1}{\partial s} + \frac{\partial f}{\partial x_1} \frac{\partial x_2}{\partial s} \\
\frac{\partial f}{\partial t} =  \frac{\partial f}{\partial x_1}\frac{\partial x_1}{\partial t} + \frac{\partial f}{\partial x_1} \frac{\partial x_2}{\partial t}
\end{align}
$$
and the gradient is computed as:
$$
\frac{\nabla f}{\nabla (s,t)} = \frac{\partial f}{\partial x}\frac{\partial x}{\partial (s,t)} = 
\begin{bmatrix}
\frac{\partial f}{\partial x_1} \frac{\partial f}{partial x_2}
\end{bmatrix}
\begin{bmatrix}
\frac{\partial x_1}{\partial s} & \frac{\partial x_1}{\partial t} \\
\frac{\partial x_2}{\partial s} & \frac{\partial x_2}{\partial t}
\end{bmatrix}
$$

The gradient of a function $f(x)$ where $f: \mathbb{R}^n \rightarrow \mathbb{R}^m$ and $x = (x1,\dots,x_n) \in \mathbb{R}^n$ can be performed as:
$$
\begin{align}
\frac{\partial f}{\partial x_i} &= 
\begin{bmatrix}
\lim_{h \rightarrow 0} \frac{f_1(x1,\dots,x_i + h,\dots, x_n) -f_1(x)}{h}
\\
\vdots
\\
\lim_{h \rightarrow 0} \frac{f_m(x1,\dots,x_i + h,\dots, x_n) -f_m(x)}{h}
\end{bmatrix}
\\ \\
\frac{\nabla f(x)}{\nabla x} &= 
\begin{bmatrix}
\frac{\partial f(x)}{\partial x_1} & \dots & \frac{\partial f(x)}{\partial x_n}
\end{bmatrix}
\\
&\Longrightarrow
\\
\frac{\nabla f}{\nabla x} &= 
\begin{bmatrix}
\frac{\partial f_1(x)}{\partial x_1} & \dots & \frac{\partial f_1(x)}{\partial x_n}
\\
\vdots & & \vdots
\\
\frac{\partial f_m(x)}{\partial x_1} & \dots & \frac{\partial f_m(x)}{\partial x_n}
\end{bmatrix}
\end{align}
$$