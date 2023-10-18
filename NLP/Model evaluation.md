Each language model is evaluated as any other [[Evaluation of a classifier|ML model]]. But, as an extra step, we can evaluate it in an extrinsic or intrinsic way.

### Extrinsic evaluation
It is a way to compare a model with the respect to another one. We put each model in a task and see which one performs the better. The downside of this approach is the fact that running this kind of evaluation is, often, very costly.

### Intrinsic evaluation
It is a way to measure the improvement of a model based on a probabilistic metric called [[Perplexity]]. It is, in general, a bad approximation of the real word performance of the model however, it can also be a useful metric.