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
with H an homography.

Given the image of a pattern with 𝑚 corners, we can write 3 linear equations for each corner j where:
- 3D coordinates are known due to the WRF definition
- 2D coordinates are known due to corners having been detected in the i-th imagethe unknowns are the 9 elements in H

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
The solution h* is found by minimizing the norm of the vectorLh:
$h* = \text{argmin}_{h\in \mathbb{R}^9}||Lh||$
and the solution can be found by using the [[SVD]] decomposition.