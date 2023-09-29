EUF = Equality with Uninterpreted Functions theory, is a way to reason over problems without assuming what the functions do. It is useful when we are dealing with functions very difficult to compute.
Example:
$$
a * (f(b) + f(c)) = d \wedge b * (f(a) + f(c)) \neq d \wedge a = b
$$
In this case we do not need arithmetic theory to understand that this is unsatisfiable.
It is a problem we can solve with [[Satisfiability Modulo Theory (SMT)]].

## Congruent closure procedure

Conjuctions of literals can be decided in polynomial time with congruence closure procedures:
1) Add a fresh $c$ and replace each $p(t_1, \dots, t_k)$ with $f_p(t_1, \dots, t_k) = c$
2) Partition the input literals into equalities (E) and disequalities (D)
3) Let E* be the congruent closure of E, i.e., the smallest equivalence relation $\equiv_E$ over the terms of E such that:
	- $t_1 = t_2 \in E \Longrightarrow t_1 \equiv_E t_2$
	- $\forall f(s_1, \dots, s_k),f(t_1, \dots, t_k) \; \text{occurring in E,} \; \forall i \in \{1, \dots, k\} s_i \equiv_E t_i \Rightarrow f(s_1, \dots, s_k) \equiv_e f(t_1, \dots, t_k)$ (congruence property)
4) Then $\phi$ is satisfiable iff $\forall t_1 \neq t_2 \in D, t_1 \not\equiv t_2$ 