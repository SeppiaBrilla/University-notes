We may need an algorithm that finds corners in an image (e.g. for [[Local invariant feature]])

# Harris corner detector

Harris&Stephens proposed to rely on a continuous formulation of the Moravec’s “error” function. We assume to shift the image with a generic, infinitesimal shift $(\Delta x, \Delta y)$.
$$
E(\Delta x, \Delta y) = \sum_{x,y} w(x,y)(I(x + \Delta x, y + \Delta y) - I(x,y))^2
$$
where $w(x,y)$ is 1 in the pixel under evaluation, 0 otherwise. We can deploy Taylor’s expansion of the intensity function at (x, y):
$$
\begin{align}
f(x + \Delta x) &= f(x) + f'(x)\Delta x\\
I(x + \Delta x, y + \Delta y) &\cong I(x,y) + \frac{\partial I(x,y)}{\partial x} \Delta x + \frac{\partial I(x,y)}{\partial y} \Delta y\\
I(x + \Delta x, y + \Delta y) - I(x,y) &\cong \frac{\partial I(x,y)}{\partial x} \Delta x + \frac{\partial I(x,y)}{\partial y} \Delta y\\
&= I_x(x,y) \Delta x + I_y(x,y) \Delta y\\
&\Rightarrow\\
E(\Delta x, \Delta y) &= \sum_{x,y} w(x,y)(I_x(x,y) \Delta x + I_y(x,y) \Delta y)^2\\
&= \sum_{x,y} w(x,y)(I_x(x,y)^2 \Delta x^2 + I_y(x,y)^2 \Delta y^2 + 2 I_x(x,y)I_y(x,y)\Delta x \Delta y)\\
&= \sum_{x,y} w(x,y)\left(\begin{bmatrix}\Delta x & \Delta y\end{bmatrix} \begin{bmatrix}I_x(x,y)^2 & I_x(x,y)I_y(x,y) \\ I_x(x,y)I_y(x,y) & I_y(x,y)^2\end{bmatrix} \begin{bmatrix}\Delta x \\ \Delta y\end{bmatrix}\right)\\
=\begin{bmatrix}\Delta x & \Delta y\end{bmatrix}& \begin{bmatrix} \sum_{x,y}w(i,x)I_x(x,y)^2 & \sum_{x,y}w(i,x)I_x(x,y)I_y(x,y) \\ \sum_{x,y}w(i,x)I_x(x,y)I_y(x,y) & \sum_{x,y}w(i,x)I_y(x,y)^2\end{bmatrix} \begin{bmatrix}\Delta x \\ \Delta y\end{bmatrix}\\
&\Longrightarrow\\
E(\Delta x, \Delta y) &= \begin{bmatrix}\Delta x & \Delta y\end{bmatrix} M \begin{bmatrix}\Delta x \\ \Delta y\end{bmatrix}
\end{align}
$$
M encodes the local image structure around the considered pixel.
If we hypotize M diagonal ($\begin{bmatrix}\lambda_1 & 0 \\ 0 & \lambda_2\end{bmatrix}$), we have:
$$
E(\Delta x, \Delta y) = \begin{bmatrix}\Delta x & \Delta y\end{bmatrix} M \begin{bmatrix}\Delta x \\ \Delta y\end{bmatrix} = \begin{bmatrix}\Delta x & \Delta y\end{bmatrix} \begin{bmatrix}\lambda_1 & 0 \\ 0 & \lambda_2\end{bmatrix} \begin{bmatrix}\Delta x \\ \Delta y\end{bmatrix} = \lambda_1 \Delta x^2 + \lambda_2 \Delta y^2
$$

![[Pasted image 20230321174242.png]]

The previous considerations have general validity as M is real and symmetric, and thus can always be diagonalized by a rotation of the image coordinate system
$$
M = R \begin{bmatrix} \lambda_1 & 0 \\ 0 & \lambda_2 \end{bmatrix} R^T
$$
The columns of R are the orthogonal unit eigenvectors of M, $\lambda_i$ the corresponding eigenvalues, $R^T$ is the rotation matrix that aligns the image axes to the eigenvectors of M.
=> We just compute the eigenvalues of M.
But computing the eigenvalue is costly, then, we can compute a more efficient function:
$$
C = \det(M) - k * tr(M)^2 = \lambda_1\lambda_2 - k(\lambda_1 + \lambda_2)^2
$$
The Harris corner detection algorithm can thus be summarized as follows:  
1. Compute C at each pixel  
2. Select all pixels where C is higher than a chosen positive threshold (T)  
3. Within the previous set, detect as corners only those pixels that are local maxima of C ([[Edge detection|NMS]])
It is worth highlighting that the weighting function w(x,y) used by the Harris corner detector is Gaussian rather than Box-shaped, so to assign more weight to closer pixels and less weight to those farther away

## Invariance properties
- Rotation: yes
- Additive bias: yes
- Multiplication bias: no
- scale: no