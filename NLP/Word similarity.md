A standard algorithm for word similarity is Minimum Edit Distance: we can find the least amount of changes we need to do in order to get from a starting string to a target string

![[Pasted image 20231004203440.png]]

This can be seen as a search problem, therefore, dynamic programming is the best solution.
We can see the transformation as a graph where each edge represent a transformation and each node represent the current state of the word. Then, we can find the smallest path from the starting word/node to the target one.
