It is different from the [[imgs/Statistical and Mathematical Methods for Artificial Intelligence/Statistics/Correlation|Correlation]] but not that much.
The correlation of signal i(x,y) and h(x,y) is defined as:
$$
i(x,y) \circ h(x,y) = \int_{- \infty}^{+ \infty} \int_{- \infty}^{+ \infty} i(\alpha,\beta)h(x + \alpha, y + \beta) d\alpha \, d\beta
$$
it looks like [[Convolution]] but there is a + instead of a -. Thus is not linear and commutative. 