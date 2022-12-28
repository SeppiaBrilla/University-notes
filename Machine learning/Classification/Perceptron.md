It is a crisp [[Classification|classifier]] that compute the classification as a linear combination of weighted inputs.

The weight represents a hyperplane in a linear equation on the data attributes. There are none or infinite hyperplanes such:
$$
w_0 * 1 + w_1 * x_1 + w_2 * x_2 + \dots + w_n * x_n = 
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

## Methods to find the separation
The Perceptron will accept any separation of classes but, some are better than others.
Here are some options:
- [[Maximum margin Hyperplane]]
- [[Soft margin]]
- [[Non-linear class boudaries]]

## Complexity

All the methods above relies on the support vectors method described on the [[Maximum margin Hyperplane]] note (with the necessary adjustements). For this reason, they all have the same complexity that may scale from $O(D * N^2)$ to $O(D * N^3)$ with D number of features and N elements. The complexity is heavly influenced by the data with more sparse data that reduces the computational cost. 

## Conclusions
This method has a slower learning process than simpler methods like [[Decision tree]] and it is also very influenced by his parameters, but it can be very precise.