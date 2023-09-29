
The cornerness at p is given by the minimum squared difference between the patch centered at p and those centered at its 8 neighbors.
$$
C(p) = \min_{q \in N_8(p)} ||N(p) - N(q)||^2
$$
In situations with uniform regions or along the [[Edge detection|edges]] of an image, C is small. The gratest possible values for C can be found near the [[Corner detection|corners]] of the image.  