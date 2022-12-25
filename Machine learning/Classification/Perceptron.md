It is a probabilistic [[Classification|classifier]] that compute the classification as a linear combination of weighted inputs.

The weight represents a hyperplane in a linear equation on the data attributes. There are none or infinite hyperplanes such:
$$
w_0 * 1 + w_1 * x1 + w_2 * x_2 + \dots + w_n * x_n = 
\begin{cases}
> 0 \Rightarrow \text{positive} \\
< 0 \Rightarrow \text{negative}
\end{cases}
$$

### pseudocode
```python
def learn():
w = [0 for i in N]
while(train_set.IsNotTotalyClassified)
	for(el in train_set):
		if not classify(el):
			if el.class == "Positive":
				w += el.dataVector
			else 
				w -= el.dataVector
```

The algorithm converges if the dataset is linearly separable, if not, we must assign an upper bound for the iterations.


## Maximum margin Hyperplane
The Perceptron will accept any separation of classes but, some are better than others.
The best one is the maximum margin hyperplane that ensures the maximum separation between labels.

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