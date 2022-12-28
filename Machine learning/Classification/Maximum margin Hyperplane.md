It is a method to find a separation between class for the [[Perceptron]]
The maximum margin hyperplane method ensures the maximum separation between labels.

#### Convex hull
Is the tightest enclosing convex polygon of a set of points (the convex hull of two linearly separable classes do not intersect)

The maximum margin hyperplane is as far as possible to from both hulls and perpendicular to the shortest line connecting the hulls.
In general, is sufficient a subset of the points of the hull. Thise points are called support vector.
The support vectors and the maximum margin hyperplane could be find solving a class of constrained quadratic optimization problems:
$$
\begin{align}
\max_{w_0,w_1,\dots,w_n} &M \\
\sum_{j = 1}^n w_j^2 &= 1\\
c_i(w_0 + w_1 x_{i,1} + \dots& + w_n x_{i,n}) > M \forall i = 1, \dots D
\end{align}
$$


