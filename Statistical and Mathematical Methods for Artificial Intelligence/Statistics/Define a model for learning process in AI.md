A model in artificial intelligence is a function that given some data predicts an outcome.
A model could be:
- A deterministic function
- A probabilistic model

The creation of a model is divided in two steps:
- __Training step__: where we train our model on the data we have and tune it to predict on that data
- __Testing step__: where we use some other data to test ohw good is our predicting model on unseen data
Generally, we split our dataset in two dataset: _Train_ and _Test_ each used in the respective step

## Deterministic functions

When the model is a deterministic function often it looks like: $f: \mathbb{R}^D \rightarrow \mathbb{R}$ because we may have D features and we often want to give them a label which is one dimensional.
Here an example of a linear function as a deterministic model:
$$
f(x): \Theta^T x + \Theta_0
$$
Where the values $\Theta$ and $\Theta_0$ are the parameters.

## Probabilistic model

When the model is probabilistic based it is based on a probabilistic distribution like [[Poisson distribution]] or [[Gaussian (normal) distribution]].
Here an example of a probabilistic model: 
Lets' define $\epsilon_n$ as $\epsilon_n = y_n - \hat{y}_n$. We want $\epsilon_n$ to be a [[Gaussian (normal) distribution]] centered in 0 and $\sigma^2$ variance ($\epsilon_n = N(0,\sigma^2)$). And the model is a function exactly as in the deterministic case. Which means that, for each pair ($y_n,x_n$) we want:
$$
p(y_n|x_n \Theta) = N(y_n| x_n^T \Theta, \sigma^2)
$$
