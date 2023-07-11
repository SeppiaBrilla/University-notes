The denoising network implements the inverse of the operation of adding a given amount of noise to an image. It takes as input: 
- a noisy image 
- a signal rate expressing the amount of the original signal remaining in the noisy image

And it tries to remove noise from it.
If we start from pure noise, the network will generate new images. 