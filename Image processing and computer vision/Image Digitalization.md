After the [[Perspective projection|analogical/geometrical]] part of the image capture process, a digitalization procedure is needed.
Normally, the image plane of a camera consist of a polar sensor which convert the irradiance in electricity. For this reason, we get a continuos value for each point of the image that we need to discretize and then convert to numeric. The whole process looks like this:
![[Pasted image 20230302183418.png]]

## Sampling 
The planar continuous image is sampled along both the horizontal and vertical directions to pick up a 2D array (matrix) of N×M samples known as pixels:
$$
f(x,y) \Rightarrow 
\begin{bmatrix}
I(0,0) & I(0,1) & \dots & I(0,M-1)\\
\vdots & \vdots & \ddots & \vdots \\
I(N - 1,0) & I(N - 1,1) & \dots & I(N - 1,M-1)\\
\end{bmatrix}
$$

## Quantization

The continuos range is quantized in $l = 2^m$ discrete levels (gray-scale).
m is the number of bits used to represent a pixel.

## Example
![[Pasted image 20230302185127.png]]
In the second image we used less pixel than needed, in the $3^{th}$ one we used fewer bits than needed.

# Camera sensor

It's a 2d array of photodetectors that convertlight into a proportional charge.
There are two main type of sensor:
- CCD (Charge Coupled Devices): More precise, less prone to nose and with a higher Dynamic range and better uniformity.
- CMOS (Complementary Metal Oxide Semiconductor): cheaper and smaller. 

## Color

The camera sensor cannot percieve color. In order to obtain it we need to put a filter on top of the lens that convert a pixel in red, green and blue. The nuber of green pixel are doubles the others to mimic the human eye. Through this process, the resolution gets lover due to the interpolation of pixel to obtain color.
![[Pasted image 20230302190257.png]]

## Dynamic range 

Measures the range on which the sensor can operate. The DR of a sensor is defined as: $\frac{E_{max}}{E_{min}}$
The higher, the better. HDR (high dynamic range) is obtained by capturing 3 photos: overexposed, normal and underexposed. The 3 combined get the most possible amount of information.