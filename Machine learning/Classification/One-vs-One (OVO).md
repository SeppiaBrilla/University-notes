It is a method that transform a binary [[Supervised classification|classifier]] in a multi-class classifier.
Consider the classes and create a series of classifier binay based on them:
Example:
Classes = A, B, C
Classifiers = 
A/B
A/C
B/C

-> $\frac{C *(C-1)}{2}$ (with C = number of classes) classifier will be generated

## Classification process

The input is put against all the classifiers and the output will be the most present class among the results