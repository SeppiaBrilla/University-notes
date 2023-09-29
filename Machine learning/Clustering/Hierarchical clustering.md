
It is a [[Clustering]] techniques that generate a nested clustering structure.
It can be:
- Agglomerative (bottom up)
	At the starting point each element is a cluster, then, at each step, the less separated clusters are merged together. (It is needed some kind of separation measure between clusters)
- Divisive (top down)
	At the starting point there is only a cluster then, at each step, the cluster with the lower [[Cohesion]] is split. (It is needed some kind of separation measure between clusters and a split procedure)

## Single linkage 

It is a bottom up Hierarchical clustering technique.

### Pseudocode
```python
def SL():
	clusters = objects
	distances = distance_matrix(objects, distance_tecnique)
	while(len(clusters) > 1):
		c1, c2 = lessDistanced_clusters(clusters, distances)
		remove(clusters, [c1, c2])
		new_cluster = cluster(c1,c2)
		cluster.append(new_cluster)
		remove(distances, (c1, c2))
		add_and_update(distances, new_cluster)
```

The complexity is $O(N^3)$ in time but could be reduced, with some indexing, at $O(N^2\log(N))$ while in space is$O(N^2)$

The final clustering scheme could be computed by stopping the procedure at the desired level.


## Conclusions

Depending on the distance technique used ([[Single link]], [[Complete link]], [[Average link]]) the generated cluster could be more or less compact.
The scaling is poor due to complexity, the decision is always local and greedy and cannot be undone, but the generated tree (dendogram structure) helps interpretation a lot and, often, the result is good.