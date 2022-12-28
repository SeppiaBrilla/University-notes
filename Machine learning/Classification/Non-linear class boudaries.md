Sometimes is impossible to have a linear separation of classes with the [[Perceptron]].
One method to deal with those cases is to apply a non-linear transformation on them:
![[Pasted image 20221226120044.png]]

## The kernel trick
The separation hyperplane computation requires a series of operations that will encrease the complexity of the algorithm.
But there is a particular family of mapping functions that do not need explicit computation and will keep the complexity down. These functions are called __kernel functions__ or, simply, __kernel__, and they are:
- linear: $<x, x'>$
- polinomial: $(\gamma<x, x'> + r)^{dg}$
- rbf: $-\gamma ||x- x'||^2$
- sigmoid: $\tanh(<x, x'> + r)$ 

Where <,> is the [[Dot product]] and $\gamma, dg, r$ are parameters.
#### Rule of thumb
Start with the easier one and then try the more complex ones.