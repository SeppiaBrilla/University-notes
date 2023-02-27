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
