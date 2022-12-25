We want to design an algorithm that finds and evaluate patterns in our data in order to better divide our data when we're building the decision tree.
There are several methods:
- [[Information theory]] --> [[Information theory for decision trees]]
- [[Gini index]]
- [[Misclassification error]]

## Methods comparison

![[Pasted image 20221224194803.png]]
The [[Misclassification error]] behaviour is linear, therefore an error in the frequency is transfered into the impurity computation. The derivate of the Gini and Entropy function are more robust and limit the propagation of the error on frequenciesis