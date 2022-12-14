theta_p, theta_g and w are parameters that should be carefully choose  as they strongly influence the efficencyis a [[Consistency tecnique]] to find arc consistency.
It uses a queue of arcs and cycles untill is empty. At each step, if the values of a variable are reduced, all the arcs from and to it will be enqueued.

### pseudocode
```python 
def AC3(nodes)
queue = [nodes]
while len(queue) > 0
	current_node = queue.pop()
	has_been_value_removed = node.RemoveInconsistentValue()
	if has_been_value_removed:
		queue.append(node.neighbours())
```