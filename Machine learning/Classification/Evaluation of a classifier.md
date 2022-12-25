We want to evaluate the performance of a [[Classification|classifier]].

## Train set problems
In supervised learning, the training set perfomance is overoptimistic. Supervides tests are usually scarse and we need to split them between train, test and, sometimes, validation to tune parameters.
We need a lower bound for performance obtained from indipendent tests, evaluate how much the theory fits the data and evaluate how much an error will cost.

## Meaning of the test error

We always suppose that the test set is a good representation fo the all dataset.
We can evaluate the error at different levels:
- general: the whole performance of the classifier
- local: the performance of a component of the classifier (e.g. a node of a [[Decision tree]])
If we have a test set error of x, what error we should expect from a runtime execution?
x + ??? ---> [[Confidence interval in error estimation]]

## Hyperparametrization

Every machine learning algorithm has one or more paramiters that influence its behaviour ([[Parameter tuning]]). Several loops and tests are needed to find the best hyperparameters value according to the problem needs (highy reliable estimate of the runtime perfomance, ...)

### Testing strategies
In each step, we want the data to be representative of the data we will have at run time, possible tecniques:
- [[Holdout]]:
	- splitting data in training / test
	- splitting data in training / test / validation: usefull to tune the parameters with the validation set without using the test set
- [[Cross validation]]: repeat the test with different splits
- [[Leave one out]]
- [[Bootstrap]]

## Performance measure of a classifier

Success rate = $\frac{\text{correct prediction}}{N_{\text{test}}}$. Error rate = 1 - Success rate.

But accuracy is not the only possible performance indicator:
- Velocity
- Robusteness
- Scalability
- Interpretability

Also, a classifier error could have different cost / consequences depending on the individuals -> sometimes we may perfer to have some false postive, other times some false negative.

### Summary of measures
- Precision = True positive / (True positive + False positive) rate of positive among positive classifications
- Recall = True positive / (True positive + False negative) rate of positive that I can catch (aka sensitivity)
- Specificity = True negative / (True negative + False positive) the rate of negative I can catch
- Accuracy = Recall * $\frac{\text{Positive}}{N}$ + Specificity * $\frac{\text{Negative}}{N}$
- F-meausure = $2\frac{\text{precision * recall}}{\text{precision + recall}}$ the armonic mean of precision and recall (Aka F1 score or balacned F_score)

### Correctness by chance
Let's consider a classifier for two classes: a and b. a has a 2% of chance to appear, while b a 98%. A classifier that forall possible values gives y(x) = b will have a 98% of correctenss, but would also be useless. How to know if the classifier is correct "_by chance_"? 
We can generate a random classifier Cr and compare its resoult with our classifier C.
We then compute the improvement of C over Cr by comparing the correct guess of C over the correct guess of Cr. Then we do the same for the perfect classifier, with correct number of guess = total guess.
We now compute the general improvement of the classifier K(C) as Improvement of C / improvement of perfect classifier.

### K statistics
Evaluates the concordance of two classifications (in this case between two classifications).
- Pr(c) = $\frac{TP_a * TP_b TP_c}{N}$ probability of concordance
- Pr(r) = $\frac{T_a*P_b + T_b*P_b + T_c*P_c}{N^2}$ probability of random concordance
- k is the ration between the concordance exceeding the random component and the maximum surplus possible:
$$
-1 \leq k = \frac{Pr(c) - Pr(r)}{1 - Pr(r)} \leq 1
$$
1 for perfect agreement, -1 for total disagreement

## Cost of errors
Making mistakes has a cost. We can reduce the cost of sensitive errors with two tecniques:
- duplicate the examples on which the classifier error is higher so that the classifier can become more able to classify them (also usefull to encrease the frequencies of rare events)
- add weights to classes so that the one with higher weights will be choosen more frequently.