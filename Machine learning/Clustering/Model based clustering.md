Model based are [[Clustering]] techniques that use statistics in order to build a model that captures the meaning of the data.
The main technique uses the mixture model that view the data as a mixture of different probability distribution summed together.
As a base model, usually, a multivariate [[Gaussian (normal) distribution]] is used and the estimator is usually made with [[Maximum likelihood estimation]]. An important assumption on the data is that every variable must be independent of the others, like in [[Naive Bayes classifier]].

# Gaussian mixture (EM)

Gaussian mixture, or Expectation maximization, is an algorithm used to find the best distribution mixture to describe the data.

### Pseudocode 

```python
def EM():
	parameters = get_initia_model()
	while(get_parameters_change(parameters) >= trashold):
		expectation = [compute_probability_belonging(parameters, x) for x in dataset]
		parameters = maximizeLikelihood(parameters, x)

	return parameters
```