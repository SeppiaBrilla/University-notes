In two words, a convolution is: __rotation + translation__.

It is a [[linear mapping]] translation-equivariant.

##### Tranlsation-equivariant means:
$$
T\{i(x - x_0, y - y_0)\} = o(x - x_o, y - y_0)
$$
A convolution is:
$$
o(x, y) = T\{i(x,y)\} = \int_{- \infty}^{+ \infty} \int_{- \infty}^{+ \infty} i(\alpha, \beta)h(x - \alpha, y - \beta)d\alpha \, d\beta
$$
If you really want to understeand why this shit is usefull [3b1b]([https://youtu.be/KuXjwB4LzSA](https://youtu.be/KuXjwB4LzSA "https://youtu.be/KuXjwB4LzSA")) knows his shit.


## Convolution in image processing

In image processing we not work with continue values but with descrete ones. In practice, then, we compute a convolution multiplying a matrix (kernel) with all the values in the image.
![[Pasted image 20230306180344.png]]
$$
O(i,j) = \sum_{m = - k} ^ k \sum_{n = - k} ^ k K(m,n)I(i - m, j - n)
$$

But we can do this only if we are not in the edges, otherwise we would not have enough values for the convolution computation. In order to solve this problem, we can:
- crop the image and discard the edges
- replicate the pixel in the edges so that we can now compute the convolution
- reflect the pixel in the edges
- add zeros to the edges 
- ...

