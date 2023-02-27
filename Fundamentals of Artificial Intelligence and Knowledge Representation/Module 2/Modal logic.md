A type of [[Logic]] built upon [[First order logic]] that adds the concept of "known" (a fact we know) and "belived" (a fact we have no certains)

## K operator

The K operator is used to indicate that an agent knows something:
$K_a P$ means that the agent a knows a fact P

## A bit of formality

Given a set of primitive propositions $\phi$, a kripke structure is defined as $M = (S,\pi, K_1, \dots, K_n)$. Where:
- S is the set of states of the world
- $\pi: \phi \rightarrow 2^S$ specifies, for each primitive, the set of states at which the proposition hold
- $K_1, \dots, K_n$ are binary relations over S. Meaning: $(s,t) \in K_i$, if agent i consider the world t possible from s