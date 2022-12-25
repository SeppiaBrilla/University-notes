Let's discuss the complexity of building a [[Decision tree]] with D attributes and N instances in X:

1) the height of the tree is $O(\log N)$
2) each tree level requires the consideration of all the dataset and all nodes requires the consideration of all attributes ->overall cost is  $O(DN\log N)$ 
	- the split of attributes costs $O(N\log N)$, the pruning requires the consideration of each node (2N - 1 at most) and pruning requires to consider globally all instances at each level -> $O(N\log N)$ all of this does not encrease complexity

Finding the best [[Decision tree]] is a NP-complete problem, but the heuristic with the greedy algorithm allows for a "fast" construction of a suboptimal, good, tree.
The runtime use of the classifier is very efficient: $O(h)$ where h is the height of the tree and, with a good pruning, the classifier associated is robust.
The impurity measure ([[Pattern finding and evaluation]]) has a low impact on the final result, while pruning strategies [[Overfitting with decision trees]] have a high impact on the final result. 
