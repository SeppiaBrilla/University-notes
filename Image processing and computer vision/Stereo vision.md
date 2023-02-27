We would like to infer 3d data from a 2d image. Getting from 3d to 2d is rather easy 
([[Perspective projection]]) but the opposite is quite hard. 
In order to solve this problem we need to use stereo vision: basically use more 2d images to infer 3d dimensions of objects. 
![[Pasted image 20230224174816.png]]

we can now compute the values as:
$$
\begin{align}
v_L &= v_R = y\frac{f}{z}\\
u_L &= X_L \frac{f}{z}\\
u_R &= X_R \frac{f}{z}\\
u_L - u_R &= b \frac{f}{z} = d\;\;\text{(disparity)}\\
d &= b \frac{f}{z}\\
z &= b \frac{f}{d}\\
\end{align}
$$

How to infer data between the two points when we are not in optimal conditions?
[[Stereo geometry]]