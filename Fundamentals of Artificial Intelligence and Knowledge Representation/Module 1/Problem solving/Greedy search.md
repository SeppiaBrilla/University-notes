Greedy is a special case of [[Best-First]] search algorithm.
It runs as follow:
```python
def Greedy(initial_node, goal):
	L = [initial_node]
	path = []
	while len(L) > 0:
		n = L.pop(0)
		path.append(n) # n should be added only if part of the true path but i don't want to write a recursive function that would allow such a check so imagine it.
		if n == goal:
			return path
		ordered_insert(L, n.childs()) # this function insert the elements in L in order of distance from the desidered goal.
	return "Path not found"
```