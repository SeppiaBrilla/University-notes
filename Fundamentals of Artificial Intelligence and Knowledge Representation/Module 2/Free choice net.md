A [[Petri nets|Petri net]] is a free choice iif for $t_1, t_2 \in T, \cdot t_1 = \cdot t_2 \vee \cdot t_1 \cap  \cdot t_2 = \emptyset$. Where
the point means the places that are input (or output) of $t_i$ if it is before (after) $t_i$

## Soundness criteria

- __P1 Termination__: any process instance starting from i will terminate in o
- __P2 Proper termination__: o is the only state reachable from i with a token in the final place
- __P3 No dead transition__: eache transition contribute to, at least, one process instance
- __P4 Transition Participation__: each transition participates to at least one process instance starting from i and ending in o

We have:
- Soundness with P1, P2, P3
- Weak soundness with P1, P2
- Relaxed soundness with P4

