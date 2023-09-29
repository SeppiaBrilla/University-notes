It is a [[Ensemble methods]]. 
Combines techniques specifically designed for [[Decision tree|trees]].
Each tree in the ensemble is built from a sample drawn with replacement (i.e., a [[Bootstrap]] sample) from the training set furthermore, when splitting each node during the construction of a tree, the best split is found either from all input features or a random subset of size max_features.
The prediction is the average of the individual classifiers.
The porpuse of this method is to reduce variance in the forest estimator because individual trees tend to overfit but, inserting randomness in the trees creations, while the individual error encrease, the average error gets lower. 