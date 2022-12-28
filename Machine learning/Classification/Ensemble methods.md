It is a [[supervised classification|classifier]] that tries to limit the classification error by using a number of different classificator under the hood.

### An example

Let's consider 25 classifiers each with an error rate of 0.35. The ensemble classifier will output the result of the majority of the prediction (>= 13).
The classifiers will have an error rate of:
$$
\epsilon_{\text{ensemble}} = \sum_{i=13}^{25} \binom{25}{i} \epsilon^i(1 - \epsilon)^{25 - i} = 0.06
$$
The ensemble classifier will improve the classification result for classification with $\epsilon < 0.5$ and if the classifier an indipendent from eachother.

## Classifier indipendence

What can we do to ensure the indipendence of the classifiers? 
- Work on the training set: we can manipulate the trianing set in order to train the classifiers on different data and get different results. [[Bagging]], [[Boosting]], [[Adaboost]]
- Work on the features: we can manipulate the feature that a certain classifier can reach in order to train different classifiers on different features. [[Random forest]]
- Work on the labels: we can regrup the classes into two classes and train a classifier on that then, repeat the process n times. At testing time every time a subset is selected the corrisponding classes will get a point and the class with more points wins.