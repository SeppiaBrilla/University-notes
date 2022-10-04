The Machine precision of a [[Floating-Point number|Floating-point system]] (or precision) is denoted by   $\epsilon_{match}$
where:
- $\epsilon_{match} = \beta^{1 -t}$ with [[Rounding rules| rounding by chopping]]
- $\epsilon_{match} = \frac{1}{2}\beta^{1 -t}$ with [[Rounding rules| rounding to nearest]] 

Alternatively we can define $\epsilon_{match}$ as  the smallest number $\epsilon$ such as:
$$fl(1 + \epsilon) > 1$$
The maximum [[relative error]] in rapresenting a real number $x$ within a range of a [[Floating-Point number|Floating-point system]] is given by $$|\frac{fl(x) - x}{x}| < \epsilon_{match}$$