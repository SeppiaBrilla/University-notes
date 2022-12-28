K-means is a [[Clustering]] tecnique that tries to find k clusters (with k as parameter) with an iterating tecnique.
At first, the algorithm set the [[Centroid|centroids]] of the clusters at random. Then, at each iteration, each point finds his nearest center and each center finds the centroid of its points. Then, the centroid move in the center of its points.
The distance is computed with a [[Similarity and dissimilarity|distance]] function.

## Distortion

given a dataset $\{x_1,dots,x_N\}$, an encoding function $encode: \mathbb{R}^D \rightarrow [1,\dots,k]$ and a decoding function: $decode: [1,\dots,k] \rightarrow \mathbb{R}^D$ we define distortion as:
$$
\text{Distortion} = \sum_{i = 1}^N(x_i - decode(encode(x_i)))^2
$$
Minimizing the distortion we get the best clustering possible because:
- $x_i$ must be encoded with the nearest center
- The partial derivative of the distortion function is 0 and so the function is either at a maximum or a minimum

### Termination of the k-means algorithm

The algorithm always converges, after a finite number of steps, to a local minimum of the ptimization function -> a "good solution".
The reasons:
- there is only a finite number of ways to partition N object into k groups
- the number of configurations where a centroid is the center of the points he owns is finite
- at each step the state changes only if the distortion is reduced, therefore the state is always a never seen before state and we cannot have loops.
- Sooner or later all the states will be visited and the algorithms must end.


The algorithm uses functions like [[Gradient method]] so it can converge to a local minimum. Therefore, the starting guess is important and a re-run of the algorithm with different starting poinst could improve the result.

It, sometimes, could happend that a centroid owns an empty set of clusters. This would reduce the number of cluster and erase the k cluster objective. To fix the situation, the solution is to move the centroid near the cluster with the highest SSE (sum of squared errors).
Where:
$$
\begin{align}
c_j &= decode(encode(x_j))\\
SSE &= \sum_{j = 1}^k \sum_{i \in OwnedBy(cj)} (x_i - c_j)^2
\end{align}
$$

## Outliers

There may be points very far from their centroids with a high ccontribution tothe SSE value. It may be a good idea to remove them.

## Complexity

- T number of iterations
- K numer of clusters
- N number of datapoints
- D number of dimensions
The complexity is:
$$
O(TKND)
$$

## Pro and cons

Pro:
- it is very efficient

Cons:
- require a k parameter (but it can be found with some generate ad test cycles)
- Very sensitive to outliers
- does not deal with noise
- do not work with non-convex cluster
- can only be computed when a [[Similarity and dissimilarity|distance]] function is aviable.