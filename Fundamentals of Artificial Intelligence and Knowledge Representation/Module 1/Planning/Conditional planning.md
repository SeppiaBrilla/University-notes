[[Planning|planners]] oftnen works under the assumption that the world is fully described in the state, but this is, of course, not true. To mitigate this problem, we can add a "sensing action" to the possible ones to sense the world and clear the uncertanties.
A conditional planner is a [[Search strategies]] that generates various alternative plans for each source of uncertainty of the plan. It is constituted by:
- casual actions
- sensing actions for retrieving unknown information
- several alternative partial plans of which, only one will be executed depending on the result of the observations.

### Limitations
- explosion of the search tree with high number of alternative contexts
- a lot of memory consumed
- alternative context are not always known in advantage
-> often conditional planners are associated with probabilistic planners that plan only for the most probable contexts.