It's a better approach to [[SAT]] resolution.

## Clause learning
This approach tries to "learn" from a failure, the cause of it. The way it is done is by adding a clause, after a failure, that allows for a faster understanding of a "dead-end" in order to avoid useless searches.

### Implication graph
An implication graph 𝐺 = (𝑉, 𝐸) is a DAG that records the history of decisions and the resulting deductions derived with Unit-propagate.
- 𝑣 ∈ 𝑉 represents a decision or a derived literal (𝑙), or the conflict (κ) at a certain decision level (𝑑)
- An edge $v \rightarrow^{c_i} w \in E$ indicates that 𝑤 is derived with unit propagation from the clause $c_i$ with one of its literals being 𝑣.
With this graph we, after a failure, we can use the clause leading to the conflict to derive backwards (from the conflict to the literals' assignment causing it) the back-jumping clause.
It is easy to see that a good clause can be obtained by negating the literals assigned "by hand". A better approach is to take, from the clause derivated backwards from the graph, the 1UIP.


## Back-jumping
Based on the contradiction, skip the decisions that did not lead to conflict and backtrack to the "breaking" decision.
$$
Ml^dN \Rightarrow Ml'
$$
Where M is the set of variables decided up to the l one. l is the variable we're currently analyzing and N are the variable afte l that leads to a conflict. We would like to derive a clause to backjump at with this form:
$$
C' \vee l'
$$
Such that $M \models \neg C$ and $l'$ is not defined in M. This way, we can directly derive $l'$ from M and go on with the SAT solution search.


## Unit Implication Point

Any node in the implication graph, other than the conflict, that is on all paths from the current decision literal (𝑙@𝑑) to the conflict (κ@𝑑). 1UIP is the closest UIP to the conflict.



## Heuristics

A number of heuristics can be added to this approach to improve it, like: 
- learn clause up to a certain dimension
- learn a clause while it is either a unit clause or implies variable assignments, and delete a clause when # of unassigned literals > 𝑚.
- [[Restarting]]
- ...