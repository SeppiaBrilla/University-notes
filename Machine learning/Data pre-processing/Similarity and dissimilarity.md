### Similarity

A numerical value of how-alike data object are with value between 0 and 1 with 1 completely identical, 0 totally different.

## Dissimilarity 

Opposite of similarity

## Computation
![[Pasted image 20221226233732.png]]

## Euclidean distance

$$
dist = \sqrt{\sum_{d=1}^D(p_d-q_d)^2}
$$
with a standardization / regularization process for different scaled dimensions.

### Minkowski distance

Is the [[Norm|p-norm]].

## Mahalanobis distance

The mahalanobis distance decreses if, keeping the same Euclidean distance, the segment is streched along the direction of grater variation of data. The distribution is described by the [[Covariance]] matrix of th dataset
$$
\begin{align}
\Sigma_{ij} = \frac{1}{N - 1} \sum_{k = 1}^{N} (x_{ki} - \bar{x}_{i}) (x_{ki} - \bar{x}_{j})\\
dist_m = \sqrt{(p - q) \Sigma^{-1} (p-q)^T}
\end{align}
$$


### Covariance matrix

- Measure the variation of pairs of random variables
- The summation is over all the observation
- The main diagonal contain the [[variance for discrete random variables|variance]]
- The value is positive if two variables grow together
- A diagonal matrix means that the variables are non-correlated
- The diagonal contains ones if the variables are standardized

## vector similarity

- $M_{00}$ the number of attributes where both p and q have zeros
- $M_{01}$ the number of attributes where the first is 0 and the second 1
- $M_{10}$ he number of attributes where the first is 1 and the second 0
- $M_{11}$ the number of attributes where both p and q have 1

### Simple matching coefficent
$$
SMC = \frac{\text{number of matches}}{\text{number of attributes}} = \frac{M_{00} + M_{11}}{M_{00} + M_{01} + M_{10} + M_{11}}
$$
### Jaccard coefficient
$$
JC = \frac{\text{number of 11 matches}}{\text{number of non zero attribute}} = \frac{M_{11}}{M_{01} + M_{10} + M_{11}}
$$

## Cosine similarity
$$
\cos(p,q) = \frac{p * q}{||p||||q||}
$$

### Extended Jaccard coefficent
$$
T(p,q) = \frac{p*q}{||p||^2 + ||q||^2 - p*q}
$$

### [[Statistical and Mathematical Methods for Artificial Intelligence/Statistics/Correlation]]


### Correlation in [[Nominal data type]]

$$
U(p,q) = 2\frac{H(p) + H(q) - H(p,q)}{H(p) + H(q)} \in [0,1]
$$
 Where H is the [[Information theory|entropy]] and H(,) is the joint entropy computed from the joint probabilities


