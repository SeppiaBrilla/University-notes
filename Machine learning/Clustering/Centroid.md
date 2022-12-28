The centroid is a physics concept that indicates the center of gravity of a set of points of equal mass. In machine learning is used in [[Clustering]] to compute the "center" of a certain cluster. For each cluster k and dimension d the d cordinate of the centroid is:
$$
centroid_d^k = \frac{1}{|x_i : clust(x_i) = k|}
\sum_{x_i : clust(x_i) = k} x_{id}
$$
and the centroid k is:
$$
centroid^k = [centroid_1^k, centroid_2^k, centroid_3^k, \dots, centroid_D^k]
$$
