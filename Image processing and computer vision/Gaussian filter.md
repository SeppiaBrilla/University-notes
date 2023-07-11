Like [[Mean filter]], Gaussian filter, is a [[Image filters]] that removes [[Noise]] from the image.
It is computed as a 2D [[Gaussian (normal) distribution|Gaussian function]] with 0 mean and constant covariance.
The higher the covariance, the strongest the smoothing.15

###  Choose of the dimension of the kernel

A rule of thumb for choosing of the kernel is:
$$
(2k + 1)\times(2k+1) \; \text{with} \; k = \lceil 3\sigma \rceil
$$

## Deploying separability

Since a 2D Gaussian is the product of two 1D Gaussian, we can deploy the separability property and chain two 1D convolutions. This speed up the computation from $O(k^2)$ to $O(k)$ 