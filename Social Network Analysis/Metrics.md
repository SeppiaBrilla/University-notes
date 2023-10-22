## Binary scale 

The simplest and most popular kind of metrics. Conventionally, 1 indicates the
presence of a relationship and 0 indicates its absence. Being the “ground floor" of the information, it can always be obtained starting from another metric, defining a threshold value (cut-off point) below which all values are reported to 0 and above to 1. The information that is lost in this way is often compensated by the greater ease of analysis.

## Multi-category Nominal Scales

This metric indicates for each relation the “type” that it assumes, with respect to
multiple-choice list (example: lover, friend, colleague, enemy, ...).

## Ordinal Scales

The simplest ordinal metric refers to a three-value scale, of the type “-1 0 +1”,
where:
 - -1 means negative
 - 0 means neutral
 - 1 means positive

## Scalar Scales

Scalar metrics are useful when handling values representing either physical
quantities - like meters, kilograms, seconds, amperes, moles - or information
units and units of account - money, goods, services, assets, labor, income,
expenses.

## Degree

One of the simplest measures is the degree of a node. In an undirected network, the degree of a node is the number of edges connected to
it.

# Centrality

Centrality measures answer to the question: “Which are the most important or central nodes in a network?”

The easier way to measure centrality is by using the degree of a node. 

## Eigenvector Centrality

In many circumstances, a node’s importance in a network is increased by having
connections to other nodes that are themselves important.
Eigenvector centrality is an extension of degree centrality that takes this factor into
account. Instead of just awarding one point for every network neighbor a node has,
eigenvector centrality awards a number of points proportional to the centrality
scores of the neighbors.
$$
x_i = \alpha \sum_{j \in neighbors{i}} x_j
$$
where $\alpha$ is a proportionality factor. The equation above can be re-written as:
$$
k X = A X \Rightarrow X = k^{-1}A X
$$
Where k is an eigenvalue of A, X is an eigenvector of A. A a matrix of 1 and 0 where 1 if the two nodes are connected, 0 otherwise.

Many implementations give to all nodes a "free" influential factor $\beta$ to a void having nodes with 0 in centrality that do not contribute to the network.

Other implementation "split" the amount of centrality each node can give to others by dividing its centrality value by its degree.

## Closeness Centrality

Differently from the previous centrality measures, based on nodes’ degree, closeness centrality uses the shortest paths in networks, measuring the mean distance from a node to other nodes.

## Betweenness Centrality

Betweenness centrality, also based on shortest paths, measures the extent to
which a node lies on paths between other nodes. The assumption here is that
paths lying on “trafficked” shortest paths have a more central role in the
network, as gateways favored by their closeness to (reach) the other nodes.


# Groups of Nodes

## Cliques

A clique is a set of nodes within an undirected network such that every member of the set is connected by an edge to every other. Cliques can overlap, meaning that they can share one or more of the same nodes.

## Cores

By contrast with a clique, where each node is joined to all the others, a k-core is a connected set of nodes where each is joined to at least k of the others. Thus, in a 2-core, for instance, every node is joined to at least two others in the set.

## Components and K-components

A useful generalization of this concept is the k-component. A k-component (sometimes also called a k-connected component) is a set of nodes such that each is reachable from each of the others by at least k node-independent paths (paths that do not share any node but the source and the target ones).

### N-cliques
Generalization of cliques that replace the strong constraint of the complete and maximum subgraph with the existence of a relationship between all the actors through a path of maximum length N.

### N-clans
a restriction of N-cliques through the constraint that the longest path in the group is less than or equal to N. It corrects a defect in N-cliques that can form spurious groups by including “neighbouring” members that are (literally) closer to other groups.

### K-plexes 
another generalization of cliques that accepts as a member of the group any node that has at least links with the other nodes, where is the total number of nodes that make up the group.

##  Transitivity and Clustering Coefficients

A relation $R$ is transitive if $a \, R \, b \wedge a \, R \, b \rightarrow a \, R \, c$.
Perfect transitivity holds in a network when the network is a clique (and its graph is complete). Partial transitivity instead can indicate the tendency to extend that (missing) relation, e.g., if a and b are friends and b and c are friends, that does not guarantee that a and c are friends, however it makes it likely.

The clustering coefficient is the fraction of path of length 2 dividing the number of close path of length 2.

## Reciprocity

Reciprocity estimates how likely it is that two nodes point at each other. If there is a
directed edge from node i to node j in a directed network and there is also an edge from j to i, then we say the edges are reciprocated. Let m be the total number of edges in the network, reciprocity is:
$$
r = \frac{1}{m} \sum_{ij} A_{ij}A_{ji}
$$

# Similarity

Networks show patterns and repeated node configurations. The most basic repetition is that of nodes that have similar properties. Node similarity can answer to questions like “how unique a node is” and “what are the groups of similar nodes in the network”. Similarity can abstract from the network, e.g., match-making services match people by similarity using their (self-reported) interests, likes, and dislikes. When looking at similarity from a network perspective, we look at the information contained in the network structure and use that to measure how “distant” are two given nodes in the network. There are two fundamental measures of network similarity: structural equivalence and regular equivalence.

## Structural equivalence

Structural equivalence is a count of the number of common neighbors two nodes
have. In an undirected network, the number $n_{ij}$ of common neighbors of
nodes i and j is given by $n_{ij} = \sum_k A_{ij} A_{kj}$. However, focusing on the total number of
nodes penalizes nodes with low degree. Solution: use cosine similarity


## Regular Equivalence

Regular equivalence of two nodes is the count of neighbors that are themselves similar. E.g., two CEOs at different companies may have no colleagues in common, but they are similar in the sense that they have professional ties to their respective CFO, CIO, members of the board, company president, and so forth.

## Homophily and Assortative Mixing

Related to similarity and equivalence, homophily (also called assortative mixing) reports the tendency of nodes in the network to draw ties with other nodes that are similar/equivalent to them.