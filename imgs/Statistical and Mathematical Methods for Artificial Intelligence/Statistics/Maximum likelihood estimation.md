 Given $x_1,\dots,x_n$ events we can define a Likelihood function as:
$$
L_x(\sigma) = \log \prod_{i = 1}^N p(x_i|\sigma)
$$
We want to compute $\sigma^*$ such as:
$$
\sigma^* = \max_\sigma L_x(\sigma)
$$
or, since it is computationally better:
$$
\sigma^* = \min_\sigma -L_x(\sigma)
$$
