
## Deterministic function model

Sometimes we may encounter an _[[overfitting]] problem_. To avoid this situation we add a regularization term on the [[empirical risk]] ($\lambda R(\Theta)$) where $\lambda$ is called the regularization parameter and the $R(\Theta)$ is called regularization. $R(\Theta) = ||\Theta||_2^2$.
The [[overfitting]] problem often occours (in the case of [[linear least-squares problem]]) when the [[Condition number]] of our data $X$ is really high (the data is ill-conditioned)

## Probabilistic model

In order to avoid [[overfitting]] we use [[MAP (maximum a posteriori)]]