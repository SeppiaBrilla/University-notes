A data manifold is a small set of items, in a large space, that have regularities. The probability of picking an item from a manifold at random should be 0. Since, for most data science application, the interesting data is a manifold (e.g. usefull images are just a small portion of the possible ones) moving the datapoint (slightly changing its values) toward another class is an easy task.

## Data compression

We can exploit the manifold characteristics to compress the data, scraping out the "regular" part of the datapoint and keeping only the interesting parts. (like in [[PCA]]) This process is data-specific and a neural network trained on a particular dataset will perform poorly on different data.