Is a [[Planning]] strategy proposed in 1995 that creates a graph called __Planning graph__ while planning. It is correct, complete and one of the most efficient planner.
It returns either the shortest possible path or an inconsistency. It inherits early commitment from [[Linear planning]] (e.g. action A is executed at step 2) but also inherit from [[Non-linear planning - Partial order planning (POP)|non linear planning]] the ability to create a partially ordered set of actions.
Actions are like in [[Strips]], objects have a type and there is an action No-op that does nothing to resolve the frame problem ([[Deductive planning]]). States are represented as true predicate in that state.
The graph is leveled: every node has a level, and arcs connect nodes in adjacent levels.
There are two type of levels:
- Proposition level: where nodes represent propositions
- Action level: where nodes represent actions

At level 0 there is the initial state (proposition level) and arcs are divided into:
- Precondition arcs (proposition -> action)
- Add arcs (action -> proposition) (a new proposition holds)
- Delete arcs (Action -> proposition) (a proposition gets deleted)


During the graph creation, incosistencies between actions or prepositions may occour but. They may appear together in the same level, but they will not appear on the same plan.

Once the graph has been build, we need to extract a valid plan out of it.
Valid plan features:
- Action on the same level can be executed in any order
- Proposition at the same step must be not mutually exclusive
- The last level contains all literals that are not mutually exclusive 

### Theorems
- if there is a valid plan then this is a subgraph of the planning graph
- A valid plan with mutually exclusive propositions at the same level does not exist
- In a planning graph two propositions are mutually exclusive in a level if they are inconsistent.