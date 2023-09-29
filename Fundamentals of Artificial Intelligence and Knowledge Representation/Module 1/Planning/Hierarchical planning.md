It is a planner that find a plan by managing the plan at different level of abstraction by considering the simpler problems after finding a solution for the most complex ones.
We now need a language to differentiate atominc operators from macro operators and then use a sub planner ([[Strips]]-like / [[Non-linear planning - Partial order planning (POP)|partial order]]-like) to resolve them.
An hierarchical algorithm must be able to:
- organize high (meta-level)
- expand abstract plan in to concrete plans

## Abstrips
An hierarchical planning algorithm that works on top of [[Strips]]. The planner procedes at different levels of abstraction and, at each level, it considers true the lower level preconditions.

## Hierarchical Pop
The hierarchical version of [[Non-linear planning - Partial order planning (POP)]]  is very similar to the normal one but, at each iteration, the algorithm chooses between the normal Pop execution or the expansion of a macro step in to his atomic steps.
### Constraints of the decomposition
If the macro action A has effect on X and it is expanded in the plan P:
- X must be the effect of at least one of the actions of the decomposition of A and it should be protected until the end of the plan P
- each precondition of the actions in P must be achieved by one of the previous actions in P or must be precondition of A
- The sobstituition of A with P must not threat any causal link