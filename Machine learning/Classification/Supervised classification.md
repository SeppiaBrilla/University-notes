A set of [[Supervised learning]] tecnique for [[Classification]]: we have a train set with all the properties and the label and, from there, the algorithm finds correlations and try to guess the unkown labels from them.

| label | p1  | p2  | p3  | p4  | ... | pn  |
| ----- | --- | --- | --- | --- | --- | --- |
| x1    | x11 | x12 | x13 | x14 | ... | x1n |
| x2    | x21 | x22 | x23 | x24 | ... | x2n |
| x3    | x31 | x32 | x33 | x34 | ... | x3n |
| x4    | x41 | x42 | x43 | x44 | ... | x4n |
| ...   | ... | ... | ... | ... | ... | ... |
| xy    | xy1 | xy2 | xy3 | xy4 | ... | xyn |

### Developing a classification model

The developement of a classification model can be divided in 3 steps:
- choose the learning algorithm
- let the algorithm learn its parametrization
- asset the quality of the model
Then the model will be used by a classification algoritm with the developed parametrization.

A classifiation function, given a data element x with an unknown label y(x) makes a prediction as:
$$
\mathcal{M}(x,\theta) = y(x)_{\text{prediction}}
$$
where $\theta$ is a set of parameters for the decision function.
The supervised learning for the algorithm gives to $\mathcal{M}$ a set of x with their corresponding y in order to determine $\theta$ by reducing the prediction error as much as possible ([[Gradient method]] ndr)
([[Vapnik-Chervonenkis Dimension]], [[Define a model for learning process in AI]])



## Workflow
1) Learning the model for a given set of classes: we need a training set with all the lables, the set should be as much representative as possible.
2) Estimate the [[accuracy]] of the model: with a test set with given labels, we use the model to guess the labels of the test set, and then we check the correctness of the guess.
3) Use the model on new individuals


### Flavours of classificator

There are two kinds of classificator:
- __Crisp__: the classifier assign a label to each individual, like [[Decision tree]], [[Perceptron]], [[Neural networks]], [[K nearest classifier]], [[Ensemble methods]].
- __Probabilistic__: the classifier assign a probability for each possible label, like [[Naive Bayes classifier]]
We can [[Transform a probabilistic classifier into a crisp classifier]]

## From binary to multiclass classifiers

Most of the classifiers works better with two classes (like the [[Perceptron]] based ones) and so, we need to find a good way to transform the two-way classification into a multi-way classification. Two main methods:
- [[One-vs-One (OVO)]]
- [[One-vs-Rest (OVR)]]

[[OVO vs OVR]]