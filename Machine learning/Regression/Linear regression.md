It is a [[Regression]] method.
Let's consider a dataset with N rows, D columns and a response vector Y with N values, the goal is to train a set of parameter w such that $y_i \approx w^t \times x_i \; \forall i \in [1, \dots N]$.

The objective function to minimize is the [[linear least-squares problem]] with gradient $2X^T(Xw^T-y)$ and linear equation solution $X^TXw^T = X^Ty$ => $w = (X^TX)^{-1}X^Ty$.


## $R^2$ parameter

Mean of the observed data = $y^{avg} = \frac{1}{N} \sum_i y_i$
Sum of squared residual = $SS_{res} = \sum_i(y_i - y_i^f)^2$
Total sum of squares = $SS_{tot} = \sum_i(y_i - y^{avg})^2$
__Coefficient of determination $R^2$__ = $1 - \frac{SS_{res}}{SS_{tot}}$ 
It compares the fitness of the model with the one of a straight line. With a perfect model the value is 1. The value of $R^2$ can be negative with a model that does not follow the trend of the data.