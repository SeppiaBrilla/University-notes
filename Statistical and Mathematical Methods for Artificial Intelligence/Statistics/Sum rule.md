The sum rule for [[Probability]] on [[Random variable]] state that:
$$
P(x) = \sum_{y \in Y} p(x,y)
$$ if $x,y$ are descrete and 
$$
P(x) = \int_y p(x,y) \; dy
$$ if $x,y$  are continuos

This rule is also known as the _marginalization property_.
It can be also generalized for $x = [x_1,\dots,x_d]$ as:
$$
p(x_i) = \int p(x1,\dots,x_d) \; dx_{\backslash i}
$$
where $x_{\backslash i}$ means everything ecept $x_i$.