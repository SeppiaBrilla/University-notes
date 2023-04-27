The model image is slid across the target image to be compared at each position to an equally sized window by means of a suitable (dis)similarity function

## Compute the dissimilarity

Different approaches:

1) Compute the pixel-wise intensity difference: $SSD(i,j) = \sum_{m=0}^{M-1} \sum_{n=0}^{N-1} (I(i+m,j+n)-T(m,n))^2$ Not invariant to intensity changes
2) Compute the sum of absolute distances: $SAD(i,j) = \sum_{m=0}^{M-1} \sum_{n=0}^{N-1} |I(i+m,j+n)-T(m,n)|$ Not invariant to intensity changes
3) normalize cross-correlation: $NCC(i,j) = \frac{\sum_{m=0}^{M-1} \sum_{n=0}^{N-1} I(i+m,j+n)\times T(m,n)}{\sqrt{\sum_{m=0}^{M-1} \sum_{n=0}^{N-1} I(i+m,j+n)^2} \times \sqrt{\sum_{m=0}^{M-1} \sum_{n=0}^{N-1} T(m,n)^2}} = \cos \theta$ Invariant to linear intensity changes
4) Zero-Mean Normalized Cross-Correlation: Like NCC, but we subtract the mean before compute the similarity. Invariant to all intensity changes.

### Fast template matching
Template matching may be exceedingly slow whenever the model and/or target images have a large size (i.e. computational complexity is O(M×N×W×H)).
A popular approach is to deploy an image pyramid:  
- Smoothing and sub-sampling  
- Full search at top level and then local refinements traversing back the pyramid down to the original image

## Shape-based Matching

It's an edge-based template matching approach: first we find the edge and their direction in the model image, then we compare them in the target image (scrolling like in the template approach) and we compute the edge detection only in the point corresponding to the edge in the reference image.
$$
\begin{align}
G_k(P_k) &= \begin{bmatrix}I_x(P_k)\\ I_y(P_k)\end{bmatrix}, \; u_k(P_k) = \frac{1}{||G_k(P_k||} \begin{bmatrix}I_x(P_k)\\ I_y(P_k)\end{bmatrix}, \; k = 1,\dots,n\\
\tilde{G}_k(\tilde{P}_k) &= \begin{bmatrix}I_x(\tilde{P}_k)\\ I_y(\tilde{P}_k)\end{bmatrix}, \; \tilde{u}_k(\tilde{P}_k) = \frac{1}{||\tilde{G}_k(P_k||} \begin{bmatrix}I_x(\tilde{P}_k)\\ I_y(\tilde{P}_k)\end{bmatrix}, \; k = 1,\dots,n \\
S(i,j) &= \frac{1}{n} \sum_{k = 1}^n u_k(P_k) \tilde{u}_k(\tilde{P}_k) = \frac{1}{n}\sum_{k=1}^n \cos \theta_k
\end{align}
$$
The similarity function spans the interval \[-1; 1\]. In order to be invariant to intensity changes, we can use the absolute value of the cosine.

## The Hough Transform
The Hough Transform (HT) enables to detect objects having a known shape that can be expressed by an equation (e.g. lines, circles, ellipses...) based on projection of the input data into a suitable space referred to as parameter or Hough space. The HT works better after an edge detection process.
Normally, when searching for a line equation, we fix the m and c parameters and search for the x and y values (line equation: $y = mx + c$) however, we can also fix the x and y values and search for the lines passing through that particular point. We can build a "parameter space" where we can compute the equation in terms of c and m ($c = -mx + y$), repeat the process for all the points and choose the m and c with the highest number of intersections.

![[Pasted image 20230417174050.png]]

To make it work in practice, the parameter space needs to be quantized and allocated as a memory array, which is often refereed to as Accumulator Array (AA).

![[Pasted image 20230417174140.png]]

A better approach is, instead of using c and m, use the line equation $\rho = x \cos \vartheta + y \sin \vartheta$.
![[Pasted image 20230417174427.png]]