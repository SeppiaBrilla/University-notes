We can use entropy to find the better split over our dataset and test on the choosen thrashold:
1) choose the attribute giving the highest IG
2) partition the dataset according to the choose attribute
3) choose as a class label of each partition the majority
4) recursevely repeat the process for each subset untill the minority is non-empty

In some cases, we cannot find a split that gives us more information. In those cases, we can mark that node as a leaf with labeled as are the majority of the elements in the dataset.