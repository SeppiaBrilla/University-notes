Is a [[Non informed strategies]] to find a solution for a given problem.
It assign a depth value to each node: the depth value will be the parent depth + 1. 0 if the node is the root.
This stragegy always expands the less deep tree nodes firsts.
The number of nodes expanded is very high and this can cause memory problems but the algorithm is guarantee to find the min-cost solution if the performing cost is equal to the deep value (all the steps cost 1).
The strategy is:
- Complete if the number of nodes is finite
- exponential on depth in time complexity
- exponential on depth in space complexity
- optiman only if the cost of each step is 1