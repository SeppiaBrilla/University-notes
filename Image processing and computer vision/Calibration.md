We need to estimate the parameters for the [[Perspective projection|PPM]] model (+distortion coefficients).  Which can be decomposed into 3 independent elements:
- A: intrinsic parameter matrix
- R: rotation matrix
- t: translation vector

Camera calibration approaches can be split into two main categories:
- hose relying on a single image of a 3D calibration object
- Those relying on several (at least 3) different images of one given planar pattern
In practice, it is difficult to build accurate targets containing multiple planes, while an accurate planar target can be attained rather easily

# Zhang’s Method

It is a process to obtain the camera's parameter. It can be described as follows:
![[Pasted image 20230427231248.png]]

### Acquire n images of a planar pattern with m internal corner
Given a chessboard pattern, we know:
- The number of internal corners of the pattern, usually odd along one dimension and even along the other to remove rotation ambiguities.
- The size of the squares that form the pattern (in mm, cm...)
Thus, the World Reference Frame can be conveniently defined by choosing a reference point as the origin and compute the position of every other point as a consequence.
![[Pasted image 20230427231521.png]]
Depending on the image, we need to compute different WRFs.

### For each image compute an initial guess homography 𝐻
Due to the choice of the WRF associated with calibration images, in each of them we consider only 3D points with z = 0. Accordingly, the PPM for points on the pattern can be simplified to a 3x3 matrix:
$$
k\tilde{m} = k\begin{bmatrix}u\\v\\1\end{bmatrix} = P\tilde{M}_W =
\begin{bmatrix}
P_{11} & P_{12} & \_ & P_{14}\\
P_{21} & P_{22} & \_ & P_{24}\\
P_{31} & P_{32} & \_ & P_{34}\\
\end{bmatrix}
\begin{bmatrix}x\\y\\0\\1\end{bmatrix} = H\tilde{w}
$$
with H a homography.

Given the image of a pattern with 𝑚 corners, we can write 3 linear equations for each corner j where:
- 3D coordinates are known due to the WRF definition
- 2D coordinates are known due to corners having been detected in the i-th image the unknowns are the 9 elements in H

Stacking 3m such equations for the 𝑚 corners, we get a system of equations.
The solution can be found by searching a point in where to move the 9 points.  
![[Pasted image 20230427232524.png]]
Two points lay on the same line if their [[cross product]] is the zero vector.
$$
\begin{align}
\tilde{m}_j \equiv H\tilde{w}_j \Rightarrow \tilde{m}_j \times H\tilde{w}_j = 0 \Rightarrow \tilde{m}_j \times H\tilde{w}_j = \\
\begin{bmatrix}
u_i\\
v_i\\
1
\end{bmatrix} \times
\begin{bmatrix}
h_1^T\tilde{W}_j\\
h_2^T\tilde{W}_j\\
h_3^T\tilde{W}_j
\end{bmatrix} = 
\begin{bmatrix}
v_j h_3^T\tilde{W}_j - h_2^T\tilde{W}_j\\
h_1^T\tilde{W}_j - u_j h_3^T\tilde{W}_j\\
u_j h_2^T\tilde{W}_j - v_j h_1^T\tilde{W}_j
\end{bmatrix} = 
\begin{bmatrix}
0\\
0\\
0
\end{bmatrix} \\
\Rightarrow h_i^T\tilde{W}_j = \tilde{W}_j^Th_i \Rightarrow\\
\begin{bmatrix}
0^T & -\tilde{W}_j^T & v_j\tilde{W}_j^T\\
\tilde{W}_j^T & 0^T & - u_j\tilde{W}_j^T\\
-v_j\tilde{W}_j^T & u_j\tilde{W}_j^T & 0^t
\end{bmatrix}
\begin{bmatrix}
h_1\\
h_2\\
h_3
\end{bmatrix} = 
\begin{bmatrix}
0 \\ 0 \\ 0
\end{bmatrix}\\
\Rightarrow\\
\begin{bmatrix}
0^T & -\tilde{W}_j^T & v_j\tilde{W}_j^T\\
\tilde{W}_j^T & 0^T & - u_j\tilde{W}_j^T\\
\end{bmatrix}
\begin{bmatrix}
h_1\\
h_2\\
h_3
\end{bmatrix} = 
\begin{bmatrix}
0 \\ 0
\end{bmatrix}
\end{align}
$$
Where the matrix on the second line is a 3x9 matrix, the h values are vectors of size 3x1 and the matrix on the third row is the second one where the last row can be removed because linearly dependent from the others (multiply first one by −𝑢 and second one by −𝑣, then sum them)
The solution can be found as:
$$
\begin{bmatrix}
0^T_{3\times1} & - \tilde{W}_1^T & v_1\tilde{W}_1^T\\
\tilde{W}_1^T & 0^T_{3\times1} & - u_1\tilde{W}_1^T\\
\vdots & \vdots & \vdots \\
0^T_{3\times1} & - \tilde{W}_m^T & v_m\tilde{W}_m^T\\
\tilde{W}_m^T & 0^T_{3\times1} & - u_m\tilde{W}_m^T\\
\end{bmatrix}
\begin{bmatrix}
h_1\\
h_2\\
h_3
\end{bmatrix}
= 0_{2m\times1} \Rightarrow Lh \equiv 0
$$
The solution h* is found by minimizing the norm of the vector h:
$h* = \text{argmin}_{h\in \mathbb{R}^9}||Lh||$
and the solution can be found by using the [[SVD]] decomposition.

### Refine each $H_i$ by minimizing the re-projection error
The initial guess of the homography won't be perfect due to all the needed approximation, so, we need to find a better approximation starting from the original one.
![[Pasted image 20230504182813.png]]

We can refine it by using some [[Iterative algorithms]] like [Levenberg-Marquardt algorithm](https://www.youtube.com/watch?v=dPZo74SbkeQ) and optimizing the formula: 
$H_i* = \text{argmin}_{H_i}\sum_{j = 1}^m ||m_j - H_iw_j ||^2\;i=1,\dots,m$, where $H_iw_j = \begin{bmatrix}\frac{h_1^T\tilde{w_j}}{h_3^T\tilde{w_j}}\\\frac{h_2^T\tilde{w_j}}{h_3^T\tilde{w_j}}\end{bmatrix}$.
This additional optimization step corresponds to the minimization of the re-projection error (typically referred to as __geometric error__) measured for each of the 3D corners of the pattern by comparing the pixel coordinates predicted by the estimated homography to the pixel coordinates of the corresponding corner extracted in the image. The error minimized to estimate the initial guess when solving the linear system is instead referred to as __algebraic error__ or distance. Solutions based on minimization of the algebraic error may not be aligned  
with our intuition, yet there exist a unique solution, which is cheap to compute. Hence, they are a good starting point for a geometric, non-linear minimization, which effectively minimize the distance we care about.

### Get an initial guess for 𝐴 given the homographies $𝐻_𝑖$
All the images acquired for calibration share the same intrinsic parameters. 
$$
\begin{align}
&P_i \equiv A[R_i|t_i] = A[r_{i1} \; r_{i2} \; r_{i3} \; t_i]\\
&\Rightarrow H_i = [h_{i1} \; h_{i2} \; h_{i3}] = [kAr_{i1} \; kAr_{i2} \; kAt_i]\\
&\Rightarrow kr_{i1} = A^{-1}h_{i1}, \; kr_{i2} = A^{-1}h_{i2} 
\end{align}
$$
Since the column vector of each $R_i$ are [[orthogonality|orthonormal]] we get:
$$
\begin{align}
&<r_{i1}, r_{i2}> = 0 \Rightarrow <A^{-1}h_{i1}, A^{-1}h_{i2} > = 0 \Rightarrow h_{i1}^TA^{-T}A^{-1}h_{i2} = 0\\
&<r_{i1}, r_{i1}> = <r_{i2}, r_{i2}> \Rightarrow <A^{-1}h_{i1}, A^{-1}h_{i1} > = <A^{-1}h_{i2}, A^{-1}h_{i2} > \\&\Rightarrow h_{i1}^TA^{-T}A^{-1}h_{i1} = h_{i2}^TA^{-T}A^{-1}h_{i2}
\end{align}
$$
By stacking these two constraints for each image, we get a homogeneous system of equations which can be solved again by [[SVD]] if $n \geq 3$ images are collected (with 6 unknown variables)

### Given A and $H_i$, get an initial guess for $R_i$ and $t_i$
Once A has been estimated, it is possible to compute $R_i$ and $t_𝒊$ given A and the previously computed homography $H_i$:
$$
H_i = [h_{i1} \; h_{i2} \; h_{i3}] = [kAr_{i1} \; kAr_{i2} \; kAt_i] \Rightarrow r_{i1} = \frac{1}{k} A^{-1} h_{i1}
$$
Since $r_{i1}$ is a unit vector we can pose the normalization constant as $k = ||A^{-1}h_{i1}||$. Then, the same constant can be used to compute$r_{i2} = frac{1}{k} A^{-1} h_{i2}$ and $r_{i2} = frac{1}{k} A^{-1} h_{i3}$, finally, since $R_i$ is [[Orthonormal basis|Orthonormal]], we can pose $r_{i3} = r_{i1} \times r_{i2}$. Yet, the resulting matrix will not be exactly orthonormal since $r_{i1}$ and $r_{i2}$ are not necessarily orthogonal and $r_{i2}$ does not necessarily have unit length since k was computed for $r_{i1}$. We can still use [[SVD]] to compute the closest orthonormal matrix by substituting D with I.


### Compute an initial guess for distortion parameters k and p
We also need to consider the [[Lenses]] distortion, which has been ignored up to now. Original Zhang’s method deploys such information to estimate coefficients 𝑘1, 𝑘2 of the radial distortion function:
$$
\begin{bmatrix}
x\\
y
\end{bmatrix} = 
L(r)
\begin{bmatrix}
x_{undist}\\
y_{undist}
\end{bmatrix} =
1(k_1r^2 + k_2r^4)
\begin{bmatrix}
x_{undist}\\
y_{undist}
\end{bmatrix}
$$
We can apply the same transformation used for the original lenses model, and we'll get:
$$
\begin{align}
&\begin{bmatrix}
\frac{u - u_0}{f_u}\\
\frac{v - v_0}{f_v}
\end{bmatrix} = 
(1 + k_1r^2 + k_2r^4)
\begin{bmatrix}
\frac{u_{undist} - u_0}{f_u}\\
\frac{v_{undist} - v_0}{f_v}
\end{bmatrix} \Rightarrow
\begin{bmatrix}
u - u_0\\
v - v_0
\end{bmatrix} = 
(1 + k_1r^2 + k_2r^4)
\begin{bmatrix}
u_{undist} - u_0\\
v_{undist} - v_0
\end{bmatrix}\\
&\Rightarrow
\begin{bmatrix}
u - u_0\\
v - v_0
\end{bmatrix} -
\begin{bmatrix}
u_{undist} - u_0\\
v_{undist} - v_0
\end{bmatrix} =
1(k_1r^2 + k_2r^4)
\begin{bmatrix}
u_{undist} - u_0\\
v_{undist} - v_0
\end{bmatrix}\\
&\Rightarrow
\begin{bmatrix}
u - u_{undist}\\
v - v_{undist}
\end{bmatrix} = 
\begin{bmatrix}
(u_{undist} - u_0)r^2 & (u_{undist} - u_0)r^4\\
(v_{undist} - v_0)r^2 & (v_{undist} - v_0)r^4
\end{bmatrix}
\begin{bmatrix}
k_1\\
k_2
\end{bmatrix}
\end{align}
$$

We get a linear, non-homogeneous system of linear equations $Dk = d$ in the unknowns $k = [k_1 \; k_2]^2$.
We get 2nm (n images, m corners) equations in 2 unknowns, which can be solved in a least square sense, minimizing $||Dk - d||_2$, by computing the pseudo-inverse matrix $D^T$ as:
$$
k* = \min_k ||Dk - d||_2 = D^Td = (D^TD)^-1D^Td
$$

### Refine all parameters by minimizing the reprojection error
Final non-linear refinement of the estimated parameters. As for homographies, the procedure highlighted so far seeks to minimize an algebraic error, without any real physical meaning. A more accurate solution can instead be found by a so-called [[Maximum likelihood estimation]] aimed at minimization of the geometric (i.e. reprojection) error. We use all the values estimated so far as initial guesses.