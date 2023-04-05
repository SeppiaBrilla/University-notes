
Very similar to [[Multi-Scale Feature Detection]] but, instead of computing the derivatives, we can just compute the difference between the image with a gaussian filter and the image itself with a different gaussian filter.
$$
DoG(x,y,\theta) = (G(x,y,k\theta) - (G(x,y,k\theta)) * I(x,y) = L(x,y,k\theta) - L(x,y,\theta)
$$
This is as effective and much faster.

![[Pasted image 20230403153849.png]]

### Extrema detection
a point (x, y, σ) is detected as a keypoint iff its DoG is higher (lower) than that of the 26 neighbours (8 at the same scale and 18=9+9 at the two nearby scales) in the (x, y, σ) space.

According to the orginal paper, the best number of octave is 3, the initial value of $\sigma$ should be 1.6 and the input image shoudl be enlarged by a factor of 2.

![[Pasted image 20230403161003.png]]