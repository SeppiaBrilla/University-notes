Often, after a variable assignement is choosen, the domain of other variables shrinks because of the constraits taking in place. We can exploit this by propagating the constraints before even choose a variable assignement. This way there will be less possible branching, and we could also reason over the "new" domains in order to choose the next variable to assign.

## Local consistency

A form of inference which detects inconsistent partial assignments. It looks only at constraints over a single variable (therefore local).

## Generalized arc consistency (GAC)

A constraint $C(X_1, \dots, X_k)$ defined over k variables, is consistent iff $\forall X_i \in \{X_1, \dots, X_k\}, \forall v \in D(X_i), \; \text{v belongs to a support}$.
At k = 2 we have __arc consistency__. A [[Combinatorial Decision Making and Optimization/Constraint satisfaction problem|CSP]] is GAC iff all its contraints are GAC

(This thing is also been explained in [[Consistency tecnique]])

## Bound consistency

A bound support is a tuple $(d_1, \dots, d_k) \in C$ where $d_i \in [\min(X_i),\max(X_i)]$. $C(X_1, \dots, X_k)$ is BC iff $\forall X_i \in \{X_1, \dots, x_k\}, \min(X_i) \wedge \max(X_i) \; \text{belong to a bound support}$.
It is defined only for totally ordered domains (e.g. integers).
It is cheaper to obtain than GAC, it is enough for monotonic constraints, but it could not detect all GAC inconsistencies in general.


# Propagation algorithm

A generic propagation algorithm cannot work better than $O(n^2)$. We must then use better and specialized algorithms / constraits to work with a lower computational cost.

## Specialized Propagation

We can build a specialized propagation algorithm for each of our constraints in order to exploit the semantics of them. This is very good computationally speaki, butut it is impractical because of the number of algorithms necessary.

## Global constraints

Capture complex, non-binary and recurring combinatorial substructures arising in a variety of applications.
Embed specialized propagation which exploits the substructure.
(Some)Types of global constraints:
- [[Counting contraints]]
- Alldifferent constraint (self-explanatory)
- [[Global cardinality constraint|GCC]]
- [[Among constraint]]
- [[Sequencing constraints]]
- [[Sequence constraint]]
- [[Scheduling constraints]]
- [[Disjunctive resource constraint]]
- [[Cumulative resource constraint]]
- [[Lexicographic ordering constraint]]

The global constraints can be propagated via specialized algorithms (already written by someone else <3) or via decomposition: decompone the constraint in smaller, easier to propagate constraints. 