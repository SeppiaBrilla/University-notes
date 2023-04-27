It is the geometric model of the image formation in a [pinhole camera](https://en.wikipedia.org/wiki/Pinhole_camera).
It composed by:
- M: scene point
- m: corresponding image point
- I: image plane
- C: optical center of the pinhole (the line through C and ortogonal to I is called Optical axis)
- c: the intersection between the optical axis and the image plane (also image center or piercing point)
- f: focal length
- F: focal plane
![[Pasted image 20230224170107.png]]

We want to find the relationship between the 3d real plane to its 2d representation.
With $u, v$ as the horizontal and vertical axis of the 2d plane and $X,Y$ the corresponding on the 3d plane, we have:
$$
\begin{align}
\frac{u}{x} &= -\frac{f}{z} \Rightarrow\\
u &= -x\frac{f}{z}\\
\frac{v}{y} &= -\frac{f}{z} \Rightarrow\\
v &= -y\frac{f}{z}
\end{align}
$$
The - mirror the image so, in order to transform it, we can get rid of it.


## Properties

The furtherst the objects are from the camera, the smallest they will appear. We can compute the new dimension (or get the original one) with the formula:
$$
l = L \frac{f}{z}
$$
where L is the origina length of the segment we want to know the new dimension, f is the focal lenght and z is the distance from the optical center. This formula assumes the segment L is lying on the horizontal axis because ratios of length are not preserved unless the scene is parallel to the camera.


# A more realistic approach

Basic Idea: map the real 3D coordinate system in an inner 3D representation of the world and then in a 2D system.
![[Pasted image 20230421134122.png]]
We call the parameters that translate the real world coordinates in the inner ones "Extrinsic" parameters and the ones from the inner representation to the 2D one "Intrinsic" parameters.

## Image pixalization

We can account for the digitalization process by use the pixel size $\Delta u \;\text{and} \;\Delta v$ along the two axis.
$$
\begin{align}
u = \frac{1}{\Delta u}\frac{f}{Z_c}x_c\\
v = \frac{1}{\Delta v}\frac{f}{Z_c}y_c\\
\end{align}
$$
With $\Delta u \;\text{and} \;\Delta v$ being the horizontal and vertical pixel size in mm.
We also need to model the translation of the piercing point wrt the origin of the image coordinate system (center of the image -> top left corner of the image).
$$
\begin{align}
u = \frac{1}{\Delta u}\frac{f}{Z_c}x_c + u_0\\
v = \frac{1}{\Delta v}\frac{f}{Z_c}y_c + v_0\\
\end{align}
$$
Often, we can find $\frac{f}{\Delta u}$ and $\frac{f}{\Delta v}$ written as $f_u$ and $f_v$ respectevly. So, in the end, there are 4 intrinsic parameters. $f_u, f_v, u_0 \;\text{and}\; v_0$.

## From WRF to CRF

3D coordinates are measured into a World Reference Frame (WRF) external to the camera, related to the CRF by a Roto-Translation (rotation + translation)
$$
M_c = 
\begin{bmatrix}
x_c\\
y_c\\
z_c
\end{bmatrix} = 
R\,M_W + t = 
\begin{bmatrix}
r_{11} & r_{12} & r_{13} \\ 
r_{21} & r_{22} & r_{23} \\
r_{31} & r_{32} & r_{33}
\end{bmatrix}
\begin{bmatrix}
X_W\\
Y_W\\
Z_W
\end{bmatrix} + 
\begin{bmatrix}
t_1\\
t_2\\
t_3
\end{bmatrix}
$$

The rotation is handled by a [[Rotation matrix]]. 
The center of the new reference system is: $0 = RC_W+ t\Rightarrow RCW = -t \Rightarrow C_w = -R^Tt$.
The rotation matrix has 9 entries, but it has only 3 independent parameters, which correspond to the rotation angles around the axes of the Reference Frame, the t matrix has also 3 parameters => there are 6 extrinsic parameters.

==>

## Combining the trasformations

We can combine the trasformations from WRT to CRF and from CRF to 2D into a singolar operation:

$$
\begin{cases}
u = f_u \frac{r_{11}x_w + r_{12}y_w + r_{13}z_w + t_1}{r_{31}x_w + r_{32}y_w + r_{33}z_w + t_3} + u_0 \\
v = f_v \frac{r_{21}x_w + r_{22}y_w + r_{23}z_w + t_2}{r_{31}x_w + r_{32}y_w + r_{33}z_w + t_3} + v_0
\end{cases}
$$
But this model is non-linear.
In order to linearize it, we can insert a "dummy" parameter that transform the 2D point in a homogenuous 3D space ($\begin{bmatrix}u\\v\end{bmatrix} \equiv \begin{bmatrix}u\\v\\1\end{bmatrix} \equiv \begin{bmatrix}ku\\kv\\k\end{bmatrix}$): 
$$
\begin{bmatrix}
u \\
v
\end{bmatrix} \equiv 
\begin{bmatrix}
ku \\
kv \\
k
\end{bmatrix} \equiv
\begin{bmatrix}
f_u & 0 & U_0 & 0 \\
0 & f_v & v_0 & 0 \\
0 & 0 & 1 & 0
\end{bmatrix}
\begin{bmatrix}
x_c \\
y_c \\
z_c \\
1
\end{bmatrix} \equiv
P_{int}\tilde{M}_C 
\equiv [A|0]\tilde{M}_c
$$

The 3x3 matrix leftmost part of $P_{int}$ is called the intrinsic parameter matrix. It is usually referred to as A or K, and it models the characteristics of the image sensing device. It is always an upper-right triangular matrix. A more general model would include a 5th parameter, known as skew, to account for possible non-orthogonality between the axes of the image sensor, but is usually 0 in practice.

We can rewrite the model as:
$$
\tilde{M}_c \equiv 
\begin{bmatrix}
x_c\\
y_c\\
z_c\\
1
\end{bmatrix} \equiv
\begin{bmatrix}
R & t \\
0 & 1
\end{bmatrix} \tilde{M}_w \equiv
\begin{bmatrix}
r_{11} & r_{12} & r_{13} & t{1}\\
r_{21} & r_{22} & r_{23} & t{2}\\
r_{31} & r_{32} & r_{33} & t{3}\\
0 & 0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
x_W\\
y_W\\
z_W\\
1
\end{bmatrix} \equiv
G\tilde{M}_W
$$

We now have:
$$
\begin{align}
\begin{bmatrix}
u\\
v\\
1
\end{bmatrix}\equiv
\begin{bmatrix}
f_u & 0 & U_0 & 0 \\
0 & f_v & v_0 & 0 \\
0 & 0 & 1 & 0
\end{bmatrix}
\begin{bmatrix}
x_c \\
y_c \\
z_c \\
1
\end{bmatrix}\\
\Longrightarrow\\
\tilde{m} = P_{int}\tilde{M}_C
\end{align}
$$
and 
$$
\begin{align}
\begin{bmatrix}
x_c\\
y_c\\
z_c\\
1
\end{bmatrix} =
\begin{bmatrix}
r_{11} & r_{12} & r_{13} & t{1}\\
r_{21} & r_{22} & r_{23} & t{2}\\
r_{31} & r_{32} & r_{33} & t{3}\\
0 & 0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
x_W\\
y_W\\
z_W\\
1
\end{bmatrix}\\
\Longrightarrow\\
\tilde{M}_c \equiv G\tilde{M}_W
\end{align}
$$
Putting everything together we obtain:
$\tilde{m} \equiv P_{int}\tilde{M}_c \equiv P_{int}G\tilde{M}_W \equiv P\tilde{M}_W$. P is known as the perspective projection matrix (PPM).
P is a $3 \times 4$ full rank matrix and the most basic one is $P \equiv [I|0]$ with I as the [[identity matrix]]. We can factorize every possible P as $A[I|0]G$ with:
- A convert from WRF to CRF
- $[I|0]$ perform the perspective projection 
- G apply camera specific transformation

Moreover, we can factorize P as: 
$$
P \equiv A[I|0]G \equiv A[I|0] 
\begin{bmatrix}
R & t \\ 
0 & 1
\end{bmatrix} \equiv
A[R|t]
$$
### Lens distortion

The PPM just described works only with the standard pinhole model. In order for it to work with a more realistic model, we need to consider [[Lenses]] distortion. The most significant deviation from the ideal pinhole model is known as radial distortion (lens “curvature”). Second order effects are induced by tangential distortion (“misalignments” of optical components and/or defects). 
Lens distortion is modelled through a non-linear transformation which maps ideal image coordinates into the observed image coordinates.
$$
\begin{bmatrix}
x\\
y
\end{bmatrix} = 
L(r)
\begin{bmatrix}
x_{undist}\\
y_{undist}
\end{bmatrix}
+
\begin{bmatrix}
dx(x_{undist}, y_{undist}, r)\\
dy(x_{undist}, y_{undist}, r)
\end{bmatrix}
$$
with the first therm as the radial distortion and the second one as the tangential. r is the distance from the distortion centre, which is usually assumed to correspond with the piercing point $c = [0,0]^T, r = \sqrt{(x_{undist})^2 + (y_{undist})^2}$.
The radial distortion function L(r) is defined for positive r only and such that L(0) = 1. This non-linear function is typically approximated by its Taylor series (up to a certain approximation order)
$L(r) = 1 + k_1r^2 + k_2r^4 + k_3r^6, \dots$  
The tangential distortion vector is instead approximated as follows:
$$
\begin{bmatrix}
dx(x_{undist}, y_{undist}, r)\\
dy(x_{undist}, y_{undist}, r)
\end{bmatrix} = 
\begin{bmatrix}
2p_1 x_{undist} y_{undist} + p_2 (r^2 + x_{undist}^2)\\
p_1 (r^2 + y_{undist}^2) + 2p_2 y_{undist} x_{undist}
\end{bmatrix}
$$
he radial distortion coefficients $k_1, k_2, \dots, k_n$, together with the two tangential distortion coefficients $p_2$ and $p_1$ form the set of the lens distortion parameters, which extends the set of intrinsic parameters required to build a realistic camera model.

The full procedure to apply the transformation is:
1) Transformation of 3D points from the WRF to the CRF, according to extrinsic parameters $G\tilde{M}_W$
2) Canonical perspective projection (i.e. scaling by the third coordinate): $\begin{bmatrix}\frac{x_c}{z_c}\\ \frac{y_c}{z_c}\end{bmatrix}$ 
3) Non-linear mapping due to lens distortion
4) Mapping from image coordinates to pixels coordinates according to the intrinsic parameters

How to estimate the parameters? [[Calibration]]