a system of floating point numbers $F(\beta, t, L, U)$ depends on:
 - $\beta$: base
 - t: precision
 - \[L, U\] exponent range

Any floating point number $x \in F(\beta, t, L, U)$ has the form:
$$x = \pm (d_1\beta^{-1} + d_2\beta^{-2} + ... + d_t\beta{-t})^{p}, L \leq p \leq U $$
where $d_i$ is an integer s.t. 
$$ 0 \leq d_i \leq \beta - 1, i = 0,...,t $$
$m = (d_1 ... d_t)$ is called mantissa 
$p$ is called exponent or characteristic

Smallest floating-point number is $UFL = \beta ^{L-1}$
Greatest floating-point number is $OFL = \beta^U(1 - \beta^{-t})$
