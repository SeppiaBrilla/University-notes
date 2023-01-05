High entropy means that the probability are similar, and we would have a flat histogram.
On the other end, low entropy means that some symbols have a much higher probability than others and the istograms will have some peaks.

Splitting a dataset in two parts changes the entropy that becomes the weighted sum of the entropies of the two parts:
$$
H(c| d: t) = H(c| d < t) * P(d < t) + H(c| d \geq t) * P(d \geq t) 
$$
with c the class attribute, t a threshold value on wich we split the dataset and d a real-valued attribute.
We can now define $IG(c|d : t) = H(c) - H(c|d :t)$ the information gained with the split
and $IG(c|d) = \max_t IG(c| d : t)$ the maximum possible information gained with a splitting.
It is often referred ad the [[Expected value]] of the [[Surprise]] ($\sum_jp(x_j)\log_2\left(\frac{1}{p(x_j)}\right)$).

## Entropy formula
$$
H(X) = - \sum_j p_j log_2(p_j)
$$
