One important aspect of machine learning is the data on which we are going to train our algorithms. We can describe our by:
- [[Type]]: What type of data we have both in a "computer science" sense (integers, booleans, strings...)  and in a more meta-level sense (Nominal, ordinal, ...)
- [[Quality]]: The quality of our data that can influence a lot the result: garbage in → garbage out. Often, to improve the quality of the data, a pre-processing activity is performed before the machine learning algorithm.


## Other data characteristics

Often we have asymmetric attributes in our data (e.g. students may have passed different exams and the other ones won't have a value) -> we must have a null value to assign. Binary asymmetric attributes are often relevant in discovery of association rules.

### Dimensionality

The difference between having a small or large set of attributes is qualitative

### Sparsity

A lot of 0 or null values. Sometimes we may find a special value / 0 in place of missing data. This can have great influence on the result of our computation, and we must be aware of it.
