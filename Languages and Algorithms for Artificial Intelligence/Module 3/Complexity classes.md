A complexity class is a set of tasks which can be computed, on a [[Turing machine]], within some prescribed resource bounds.

A language L is in the class DTIME(T(n)) iff there is a deterministic TM deciding L and running in time $c * T(N)$ for some constant c.

### P
Is the class of all languages decidable in polynomial time.

### FP
Is the same as P but for functions rather than languages.

## Exp
Is the class of all languages decidable in exponential time.

### FExp
Is the same as Exp but for functions rather than languages.


### NP
A language L is in the class NP iff there exist a polynomial p and a polynomial time TM M such that:
$$
L = \{x \in \{0,1\}^*| \exists y \in \{0,1\}^{p(|x|)}. M(\llcorner x, y\lrcorner) = 1\}
$$
M is called the "verifier" for L and y is the certificate. Any NP problem, can be computed in polynomial time with a [[NDT]].

## Reduction

The language L is said to be polynomial-time reducible to another language H iff there is a polytime computable function f s.t. $x \in L \text{ iif } f(x) \in H$. If a language is reducible to another language H, then H is as difficult as L. 

A problem H is said to be:
- C-Hard if $L \leq_p H \; \forall L \in C$
- C-complete if H is hard and $H \in C$.

A set of np-complete problems:
- SAT
- [[Linear programming|ILP]]
- 3SAT
- OL3SAT
- subsetSum