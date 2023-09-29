It is a probabilistic [[Classification|classifier]] based on the Bayes theorem and the assumption that every attribute is indipendent from the others.

Let's say we have N feature and X labels,
$\forall i,j F_{i,j,v} = \frac{N_{j,v} \text{where appear label} X_i}{\text{total value of} X_i}$ 
Example:

| a   | b   | l   |
| --- | --- | --- |
| a1  | b1  | 1   |
| a2  | b2  | 2   |
| a1  | b2  | 1   |
| a2  | b1  | 1   |
| a1  | b2  | 1   |

-> $F_{a,1,a1} = 3/4$ 
Then, we compute the likelihood of a label $X_i$ as the product of all $F_{j,i,v_j}$ where j are all the feature and $v_j$ is the value for the feature j in the case we want to predict
Then we normalize:
$$
Pr(X_i) = \frac{\text{likekyhood} \; X_i}{\sum_k \text{likekyhood} \; X_k} * 100
$$
This is true because, from the [[Bayes theorem]] and the Independence of the variables we have:
$$
Pr(H|E) = \frac{Pr(E|H)P(H)}{Pr(E)} = \frac{Pr(e_1|H) \times Pr(e_1|H) \times \dots \times Pr(e_n|H) \times Pr(c)}{Pr(E)}
$$
Where E is the evidence and H the class / label we want to compute the probability of.

## Problems
If a probability is, in some cases, 0, the whole computation will be nullified.

### Laplace smoothing

smoothed frequency of 
$$
sf_{d = V_i, c} = \frac{af_{d = V_i, c} + \alpha}{af_c + \alpha V}
$$
where:
- $\alpha$ is the smoothing parameter, typical value is 1
- $af_{d = V_i, c}$ is the absolute frequency of value $v_i$ in attribute d over label c
- V is the number of attribute d in the dataset
- $af_c$ is the absolute frequency of the label c in the dataset


## Missing values
They are simply removed from the computation

## Numerical value
We cannot use frequency based methods. Then we assume that the values have a [[Gaussian (normal) distribution]] -> we compute mean and variance of each numeric attribute inside each class, then, for a given attribute and a given class we compute 
$$
f(x) = \frac{1}{\sqrt{2\pi\sigma}}e^{- \frac{(x- \mu)^2}{2\sigma^2}}
$$


## When the classifier fails

The main drowbacks of this classifier lie on the two big assumption we make: the indipendece of the variables and the normal distribution of the numerical values. When those two assumpion fails the classifier gives bad results.