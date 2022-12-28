It is a [[Clustering]] tecnique.
There are two main solutions:
- grid based: divide the Hyperspace in grids and connect together object in the same grid
- object-centered: define a radius of each object and connect together object whose radius collide.

# DBSCAN

Density based spatial clustering of application with noise

p is a border point if, in his radius, there are less than a certain trashold points.
If p is not border then it is core.
Define the neighbour of p all the point in his radius.
p is directly density reachable from q if:
- q is core
- q is in the neighbour of p (and viceversa)
The viceversa is not always true.
A point p is density reachable from q if:
- q is core
- there is a sequence of directly densitive reachable points from q to p

Two point are desity connected if there is at least a point s such as both p and q are density reachable from s (Symmetric).

## Cluster generation

A cluster is a maximal set of points conneced by density. Border point not connected by density are noise.

## Parameters selection 

The trashold selection to define a point as border or core is a parameter that is very hard to find. Often, a set of trial and error is required, but a good starting guess is 2 * Number of dimensions.
Choosing the radius is more difficult, but we can start from considering the distance from the k-nearest neighbours with k = trashold and choose a k-distance starting from there. Often, where there is a change of slope in the k distance plot there is a good epsilon value.

## Conclusion on DBSCAN

It finds clusters of every shape, and it is very noise-robust. It can also be problematic with clusters with widely varying densities. And could have a high complexity $O(N^2)$ that can be reduced to $O(N\log(N)$ with spatial indexes are available. It is also very sensitive to his parameter.


# Kernel density estimation (DENCLUDE)

It is a statistic based tecnique that describe the data distribution with a function and the overall density functions is the sum of the influence functions (or kernel functions) of each point.
The kernel function must be symmetric and monotonically decreasing.


### Denclude procedure

1) Derive a density function for the space occupied by the datapoints
2) Identify the local maxima 
3) Associate each point with the nearest density attractor
4) Define a cluster as a set of points associated with a particular density attractor
5) Discard clusters with a density attractor whose density is less than a given trashold 
6) Combine clusters that are connected by a path of points with density higher than the trashold.

## Conclusion on DENCLUDE

It has a strong theoretical foundation on statistics, very good at dealing with noise and different-shaped clusters. But it is very complex $O(N^2)$ and has truble with cluster with different densities and high dimensional data.

