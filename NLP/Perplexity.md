It is a metric that measure the ability of a given model to predict the next word given a sentence. It can be computed as:
$$
PP(w_1^N) = P(w_1^N)^{\frac{1}{N}} = \sqrt[N]{\prod_i \frac{i}{P(w_i| \dots)}}
$$
Where N is the length of the sentence.
