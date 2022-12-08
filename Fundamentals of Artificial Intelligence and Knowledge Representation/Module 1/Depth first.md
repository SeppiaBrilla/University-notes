The depth first search is a [[Non informed strategies]] to find a solution to a given problem.
It expands the deepest nodes first. The strategy is efficient memory wise because it must store only a node in memory at the time.
This strategy is:
- non complete for infinite depth problems and can diverge for spaces with loops. But can be modified to avoid repeated states.
- $O(b^m)$ with b = maximum tree branching and m = maximum depth of the state space (time)
- $O(bm)$ in space
- Non optimal
