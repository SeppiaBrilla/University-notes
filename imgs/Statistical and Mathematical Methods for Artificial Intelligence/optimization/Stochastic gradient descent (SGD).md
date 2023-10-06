Often we have that the function f is the sum of n functions ($f(x) = \sum_i^n f_i(x)$ ) and so the [[Gradient]] of f is the sum of the gradients in all the functions composing f. 
In order to speed up the [[Gradient method]] we can approximate the value of the gradient of f by computing only one of the gradients of the functions (or a subset of them in case of the mini- batch version of this algorithm) (the function composing the approximated gradient are choose randomly)

## problems 
- the direction could be not a descending one since the value of the gradient is approximated
- under suitable hypotesis the algorithm converge "in expecation" to a local minimum (but not always)