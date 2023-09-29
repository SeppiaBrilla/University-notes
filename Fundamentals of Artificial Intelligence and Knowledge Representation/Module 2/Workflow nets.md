They are particular types of [[Petri nets]]. They use places as conditions and transition as activity instances. Tokens are colored, and they represent process instances (with an identifier). They have only a starting place (i) with no arc ongoing and only a final place (o) with no arcs outgoing.
We have control flow patterns with their own semantic (up to the designer): and split/join,
xor split/join.
We have automatic, user, external and time triggers.

## Structural soundness

A net is structural sound if there is only a start and only an end place, and each inner place is in a path from the initial to the final place.
This property still allows having deadlocks, livelocks and remaining tokens.

## Sound

It is like structural soundness but without the bad things.
Let $PN = (P,T,F)$, a net and
$$
\begin{align}
&i, o \in P \; \; \text{with i and o initial and final places}\\
&\text{i, o are the only places with a token}\\
&M, M': \text{markings}\\
&M \geq M' \Leftrightarrow \forall_{p \in P} M(p) \geq M'(p)\\
&M > M' \Leftrightarrow M \geq M' \wedge \exists_{p \in P} M(p) > M'(P)\\
\end{align}
$$
a [[Workflow nets]] (PN,i) is said to be sound if:
- for every state M reachable from i there exist a firing sequence leading from M to o
- the state o is the only reachable state from i with at least one token place in o
- there are no dead transition in the workflow net in state i.

Soundness can be checked via reachability analysis using a reachability graph.

__Theorem__:
A workflow net PN is sound iif PN' = PN but with an extra node t* that connect i and o, is live and bounded.

[[Petri nets]] are live if for each transition there is a firing sequence from i to t.
A place in [[Petri Nets]] is k-bounded if it does not contain more than k tokens in all reachable
markings. It is safe if it is 1-bounded. It is bounded if it is k-bounded for some k.