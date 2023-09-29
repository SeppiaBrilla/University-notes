We can forecast each element of the test set like in a Bernulli experiment process:
- Good prediction -> success
- Bad prediction -> failure
The empirical frequency of an error is $\frac{S}{N}$ where N is the number of independent experiment made (number of elements of the test set).
The deviation of the empirical frequency from the true frequency is due to noise.
Noise is assumed to have a normal distribution around true probability

### Confidency level
We choose the confidency level as:
$$
P\left(Z_{\frac{\alpha}{2}} \leq \frac{f - p}{\sqrt{\frac{p(1 - p)}{N}}} \leq Z_{1 - \frac{\alpha}{2}}\right) = 1 - \alpha
$$
The probability that the true frequency of success is below the pessimistic frequency that we will compute.
Z depends on the desired confidence level of $\alpha$, and it represents the abscissa delimitating the area 1 - $\alpha$ for the normal distribution.

## Example on [[Decision tree]] pruning

The C4.5 strategy:
Consider a subtree near the leaves, compute the maximum error $e_i$ as the weighted sum of the maximum error of the leaves and the maximum error of the root leaf $e_r$. 
If $e_r \leq e_i$ then, prune the tree. With pruning the frequency error of the tree will increase but the number of the records in the node will increase as well and this could result in a lower maximum error.

