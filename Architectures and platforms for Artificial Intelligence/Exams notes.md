
# Loss functions

$$
\frac{1}{N} \sum_iL_i(f(x_i,W)y_i)
$$
- N is the number of datapoint
- L is the loss computed on the value x against the datapoint y
- W are the weights of the AI
### Some functions
- Crossentropy loss: $\sum_{x \in X} p(x) \log q(x)$
- Square loss: $\sum_i(y_i - f(x_i,W))^2$
The normalization factor is, sometimes, used to avoid overfitting.

### Softmax
$$\frac{e^{x_i - \max(x)}}{\sum{_j e^{x_j - \max{x}}}}$$
### Gradient 

Two ways of computing it:
- Numerically: slow, approximate, easy to write
- Analytically: fast, exact, error-prone.
In practice, you use the numerical gradient to check the analitycal one.

### Learning rate schedule
Sometimes it is useful not to have a fixed learning rate but a variable one. There are several ways to implement it, some are:
- cosine
- linear
- inverse sqrt
![[Pasted image 20240102213721.png]]

# Convolutions

$out = \frac{in + 2p - k }{s} + 1$
where:
- p is the padding
- s is the stride
- k is the kernel size

### Pooling
- overlapping (no stride) -> image of size W with pooling p -> out: W - p + 1
- non overlapping (stride) -> as for convolutions

### Spatially separable convolutions
split a kernel of size n into two kernels nx1 and 1xn

### Depth-wise separable convolutions
Instead of a convolution of n output channels, compute n convolutions of 1 channel and then sum them together with a 1x1 convolution.
### Grouped convolutions
A convolution looks only at a subset of the channels.

# ISA extensions

- post increment -> avoids incrementing the loop counter manually using a specialized counter. Works only if the number of iteration is known before starting the loop
- simd (single instruction, multiple data)
- dot product multiplier

# Gem-w convolutions

$$
\begin{align}
\text{kernel} &= \begin{bmatrix}00 & 01 & 02 \\ 10 & 11 & 12 \\ 20 & 21 & 22\end{bmatrix} \Rightarrow \begin{bmatrix}00\\01\\02\\10\\11\\12\\20\\21\\22\end{bmatrix}\\
\text{activation} &= \begin{bmatrix}
00 & 01 & 02 & 03 \\
10 & 11 & 12 & 13 \\
20 & 21 & 22 & 23 \\
30 & 31 & 32 & 33
\end{bmatrix} \\&\Rightarrow 
\begin{bmatrix}  
00 & 01 & 02 & 10 & 11 & 12 & 20 & 21 & 22 \\
01 & 02 & 03 & 11 & 12 & 13 & 21 & 22 & 23 \\
10 & 11 & 12 & 20 & 21 & 22 & 30 & 31 & 32 \\
11 & 12 & 13 & 21 & 22 & 23 & 31 & 32 & 33
\end{bmatrix}\\
\text{res} &= \begin{bmatrix}00 & 01 & 10 & 11\end{bmatrix} \Rightarrow \begin{bmatrix} 00 & 01 \\ 10 & 11\end{bmatrix}
\end{align}
$$

## Tiling

Compute the value of an element in a matrix multiplication can be very expensive in terms of memory. Therefore, to better utilize the memory accesses, we can do the operations in blocks.

### Multiprocessing
speedup:
$$
\begin{align}
&\frac{Nclycles_{sequential}}{Ncycles_{parallels}}\\
Ncycles_{parallel} &= \max(Nchuncks / processors) Ncycles / chunk \times cfork + cjoin
\end{align}
$$

## Quantization

Use fixed point instead of floating points for real numbers. Normally:
- 16 bit: no loss
- 8 bit: some losses but minimal.
- 4 bit there's a bit of overhead while packing / unpacking the operands
- 1 bit: extreme but useful in some occassions.

### Linear quantization
Affine mapping from real numbers to integers.
$r = (q -z) s$

where:
- r is the real number
- q is the integer number
- z is an integer value
- s is a floating point number 
range: $r_{max} = s(q_{max} -z)$, $r_{min} = s(q_{min} - z)$
$r_{max} - r_{min} = s(q_{max} - q_{min})$
s = $\frac{r_{max} - r_{min}}{q_{max}-q_{min}}$
z = $q_{min} - \frac{r_{min}}{s}$
to deal with non-centered distribution activation:
we may move the z value towards the middle by subtracting the max value of the activation to the min value, and we can divide by a delta value which is:
- $\frac{a_{max} - a_{min}}{2^N -1}$ for activations 
- $2 * \frac{a_{max} - a_{min}}{2^N -1}$ for weights

Usually, for the weights, we keep the z value at 0.
N is the number of bit representing the numbers and can be:
- fixed per net (fixed precision)
- fixed per layer (mixed precision)

### Non-uniform quantization
There are also non-uniform quantization strategies like
- log domain
- wight clustering

### Quantization strategies
- post training
- quantization-aware training
The latter can increase performance with more aggressive quantization strategies.
We can also increment the network quantization to better tune it. 
To train a quantized network we keep 2 versions of the same weights: the quantized one for inference and the non-quantized one for backpropagation. This is due to the fact that integer numbers are not diferentiable.

# Pruning
It's a strategy to save space by removing unused or redundant connections.
- Saliency pruning: prune weights with minimal impact on the functions
- Magnitude pruning: prune based on a threshold value
pruning schedule: gradually prune instead of doing it one-shot
### Unstructured pruning
prune where needed (slow and, most of the time, can slow down computation)

### Structured pruning
- block based: prune based on the underlying structure of the simd instructions
- node based: remove entire nodes (can be done by masking)

# Strassen

$$
\begin{align}
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix} \times
\begin{bmatrix}
e & f \\
g & h
\end{bmatrix} &= 
\begin{bmatrix}
ae + bg & af + bh  \\
ce + dg & cf + dh
\end{bmatrix} \Rightarrow \text{8 mul, 7 add}\\
p1 &= a(f-h)\\
p2 &= (a+b)h\\
p3 &= (c+d)e \\
p4 &= d(g-e) \\
p5 &= (a+d)(e+h) \\
p6 &= (b-d)(g+h) \\
p7 &= (a-c)(e+f) \Rightarrow \\
AB &= 
\begin{bmatrix}
p5+p4-p2p6 & p1+p2\\
p3+p4 & p1+p5-p3-p7 
\end{bmatrix}\Rightarrow \text{7 mul, 18 add}
\end{align} 
$$
can be applied recursevly: 7T(N/2) + O($N^2$) 
The result is cutting the complexity from $O(N^3)$ to $O(N^{2.8})$

# Winigrad

for convolutions.
out = $Z^T[(WwW^T) \dot (XxX^T)]Z$
where Z, W and X are transformation. For multiple channels we just sum the results. It can speed things up a lot but each filter size require a different computation.

# FFT
we can use fast furier transform and convert both filter and activations to frequency domains.