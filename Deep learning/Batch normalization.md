It is used to increase stability and speed in training. It also increase indipendence between layers.
At each training iteration, the input is normalized according to batch statistics. Subtracting the mean and dividing by standard deviation. Then, an opposite transformation is applied based on $\gamma$ learned paramiter and $\beta$ (center):
$$
BN(x) = \gamma \times \frac{x - \mu^B}{\sigma^B} + \beta
$$
