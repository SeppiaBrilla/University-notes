It is a [[Supervised learning|supervised]] tecnique to evalutate a [[Clustering]] scheme.
We may have a set of data with some label already computed (in this case, the labes works as clusters names). We can use the clustering scheme we have computed to label the data and compare the actual label against the cluster label.
Sometimes it could be necessary a permutation of the labels' names in order to match the clustering ones. 
![[Pasted image 20221227171522.png]]
In this case a rename of 0 to 1 and to 1 to 0 is necessary but, in general, the clustering process was successfull.

### Some measures

$y_k(.)$ is the clustering scheme and $y_g(.)$ is the gold standard.
We can label any pair of objects as:
- SGSK if they belong in the same scheme both in $y_k(.)$ and $y_g(.)$
- SGDK if they belong in the same scheme in $y_g(.)$ but not in $y_k(.)$
- DGSK if they belong in the same scheme in $y_k(.)$ but not in $y_g(.)$
- DGDK if they belong in different schemes both in $y_k(.)$ and $y_g(.)$

__Rand score__ = $\frac{SGSK + DGDK}{SGSK + DGDK + SGDK + DGSK}$
Jaccard coefficient is the same but computed only in one label.