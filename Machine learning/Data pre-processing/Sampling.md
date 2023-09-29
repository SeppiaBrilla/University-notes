It is a [[Data pre-processing]] strategy.
Sampling is useful both for a preliminary investigation and a final data analysis.
A sample, often, is as effective as the entire dataset ___if the set is representative___.

## Type of sampling
- Simple random: a simple random choice of an object with a given probability distribution
- With replacement: like simple random but with multiple repetition of independent extraction
- Without replacement: Like with replacement but, at each extraction, the element is removed from the possible one
- Stratified: the data is separated in different partition according to some criteria and the random sample are draw from each partition. This guarantee representativity.

A trade-off between data reduction and precision must be made.


## Missing classes
The probability of sampling at least one element of each class is independent from the size of the dataset but is very important to have a representative sampling in order to properly train the machine learning model.
If there is a high number of classes with low representativity, it could be difficult to get a good test/train or [[Cross validation]] sampling.

