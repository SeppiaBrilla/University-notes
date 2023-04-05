Edges are pixels that separate two (or more) regions of different intensities in the image, often, those regions denote objects.

## 1D step-edge

It finds the edges by looking at the derivative of the change of intensities: if there is a big change in the intensity, the derivative of the intensity function has a spike, and we can infer from it if there are edges. 

## 2D step-edge

Like 1D step-edge, but we take into account also the direction.
![[Pasted image 20230314162706.png]]
$$\begin{align}
\nabla I(x,y) &= \frac{\partial I(x,y)}{\partial x}i + \frac{\partial I(x,y)}{\partial y}j\\
I(x,y) &= \frac{\partial I(x,y)}{\partial x} + \frac{\partial I(x,y)}{\partial y} =\\ 
I_x + I_y &= |\nabla I(x,y)| = \sqrt{i_x^2 + I_y^2} = T_h\\
atan&\left(\frac{I_y}{I_x} \right) \; \text{direction}\\
atan2&\left(I_x, I_y \right) \; \text{direction and sign}
\end{align}$$
![[Pasted image 20230314175014.png]]

## Discrete approximation of the gradient

We can use either backwar, forward or central differences:
$$
\begin{align}
\frac{\partial I(x,y)}{\partial x} \cong I_x(i,j) = I(i,j) - I(i,j-1),\; \frac{\partial I(x,y)}{\partial y} \cong I_y(i,j) = I(i,j) - I(i-1,j) \; \text{backward}\\
\frac{\partial I(x,y)}{\partial x} \cong I_x(i,j) = I(i,j+1) - I(i,j),\; \frac{\partial I(x,y)}{\partial y} \cong I_y(i,j) = I(i+1,j) - I(i,j) \; \text{backward}\\
I_x(i,j) = I(i,j+1)-I(i,j-1), \; I_y(i,j) = I(i+1,j)-I(i-1,j) \; \text{central}
\end{align}
$$

And we can approximate the magnitude using different approximations:
$$
\begin{align}
|\nabla I| = \sqrt{I_x^2 + I_y^2}\\
|\nabla I|_+ = |I_x| + |I_y| \\
|\nabla I|_{\text{max}} = \max(|I_x|, |I_y|)
\end{align}
$$
The last one is faster and more invariant with respect to edge direction.

## Edges and noise

In real scenarios, we cannot assume to have edges that smooth due to [[Noise]].
So, we cannot use derivatives because they are not robust against noise, and we cannot use standard de-noising [[Image filters]] because they blur the image and make the edge detection process more complicated.
As a solution, we can compute the difference of averages rather than making the same in different steps (and use [[Convolution]] to do so).
$$
\begin{align}
&\begin{cases}
\mu_x = \frac{1}{3}[I(i,j - 1) + I(i,j) + I(i,j + 1)]\\
&\text{averages}\\
\mu_y = \frac{1}{3}[I(i - 1,j) + I(i,j) + I(i + 1,j)]
\end{cases}\\
&\bar{I_x}(i,j) = \mu_y(i,j + 1) - \mu_y(i,j)\\
&= \frac{1}{3}[I(i - 1, j + 1) + I(i, j + 1) +I(i + 1, j + 1) - I(i - 1, j) - I(i, j) - I(i + 1, j)] \\
&\Rightarrow \frac{1}{3}
\begin{bmatrix}
-1 & 1\\
-1 & 1\\
-1 & 1\\
\end{bmatrix}\\
&\bar{I_y}(i,j) = \mu_x(i + 1,j) - \mu_x(i,j)\\
&= \frac{1}{3}[I(i +1 1, j - 1) + I(i + 1, j) + I(i + 1, j + 1) - I(i, j - 1) - I(i, j) - I(i, j + 1)]\\
&\Rightarrow \frac{1}{3}
\begin{bmatrix}
-1 & -1 & -1\\
1 & 1 & 1\\
\end{bmatrix}
\end{align}
$$
![[Pasted image 20230314183441.png]]
![[Pasted image 20230314185754.png]]

### Prewitt operator
Given the same smoothing, we would wish to approximate tehe partial derivatives by centra differences
$$
\begin{align}
\bar{I_x}(i,j) = \mu_y(i, j + 1) - \mu_y(i, j - 1) \Rightarrow \frac{1}{3}
\begin{bmatrix}
-1 & 0 & 1 \\
-1 & 0 & 1 \\
-1 & 0 & 1 \\ 
\end{bmatrix}\\
\bar{I_y}(i,j) = \mu_x(i + 1, j) - \mu_x(i - 1, j) \Rightarrow \frac{1}{3} 
\begin{bmatrix}
-1 & -1 & -1 \\
0 & 0 & 0 \\
1 & 1 & 1 \\ 
\end{bmatrix}\\
\end{align}
$$

## Sobel operator
At the same time, we can weight central pixels more 
$$
\begin{align}
\mu_x(i, j) = \frac{1}{4}[I(i, j -1) + 2I(i,j) + I(i,j + 1)]\\
\bar{I_x}(i,j) = \mu_y(i, j + 1) - \mu_y(i, j - 1)\\
\Rightarrow \frac{1}{4}
\begin{bmatrix}
-1 & 0 & 1\\
-2 & 0 & 2\\
-1 & 0 & 0
\end{bmatrix}\\
\mu_y(i, j) = \frac{1}{4}[I(i - 1, j) + 2I(i,j) + I(i + 1, j)]\\
\bar{I_y}(i,j) = \mu_x(i + 1, j) - \mu_x(i - 1, j)\\
\Rightarrow \frac{1}{4}
\begin{bmatrix}
-1 & -2 & -1\\
0 & 0 & 0\\
1 & 2 & 1
\end{bmatrix}\\
\end{align}
$$

## NMS

Deciding a trashold value to detect edges on the gradient function can be difficult. A better approach is finding the maximum local value on the image.
The magnitude of the gradient has to be estimated at points which do not belong to the discrete pixel grid. Such values can be estimated by linear interpolation of those computed at the closest points belonging to the grid

## Canny’s Edge Detector

Canny proposed to set forth quantitative criteria to measure the performance of an edge detector and then to find the optimal filter with respect to such criteria:
- __Good Detection__: the filter should correctly extract edges in noisy images
- __Good localization__: the distance between the found edge and the “true” edge should be minimum
- __One Response to One Edge__: the filter should detect one single edge pixel at each “true” edge

A straightforward Canny edge detector can be achieved by:  
- [[Gaussian filter]] (smoothing)  
- [[Gradient]] computation  
- NMS along the gradient direction

## Zero-crossing

Look for zero-crossing of the second derivative of the signal to locate edges (instead of the peaks of the first derivative)
![[Pasted image 20230320200501.png]]

Since computing the second derivative is pretty expensive, we can approximate them using forward and backward differences:
$$
\begin{align}
I_{xx} &\cong I_x(i,j) - I_x(i, j - 1) = I(i, j - 1) - 2I(i,j) + I(i,j + 1)\\
I_{yy} &\cong I_y(i,j) - I_j(i - 1, j) = I(i - 1, j) - 2I(i,j) + I(i + 1, j)\\
\nabla^2 &= 
\begin{bmatrix}
0 & 1 & 0\\
1 & -4 & 1\\
0 & 1 & 0
\end{bmatrix}
\end{align}
$$
![[Pasted image 20230320202344.png]]
(we can use a [[Convolution]] to approximate the second gradient)

### Laplacian of Gaussian (LOG)

To have a better edge detection we must smooth the image, the log edge detection work as follows:
1) [[Gaussian filter]] (gaussian smoothing) $\bar{I}(x,y) = I(x,y)*G(x,y)$
2) Second order differentiation by the Laplacian
3) Extraction of the zero-crossing of $\nabla^2 \bar{I}(x,y)$

Unlike those based on smooth derivatives, the LOG edge detector allows the degree of  
smoothing to be controlled (i.e. by changing the σ parameter of the Gaussian filter). 
it Is basically impossible to have 0 as a value in the second derivative in corrispondance of the edges, so, a much more realistic approach is to search to a change in sign in the pixel value and use the most close-to-zero value as the edge.

