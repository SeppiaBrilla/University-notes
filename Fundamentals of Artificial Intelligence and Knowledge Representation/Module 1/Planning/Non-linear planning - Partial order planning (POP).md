It is an alternative to [[Linear planning]]: instead of searching in the state space, this kind of algorithms search in the  plan space. Each node is a partial plan and operators are plan refinement operations.
A non linear planner is represented by:
- a set of actions
- a (non exhaustive) set of ordering between actions
- a set of casual links

The initial plan is an empty plan with two fake actions: 
- __start__: No preconditions. It's effect match the initial state
- __stop__: No effects. It's preconditions match the goal state
- ordering: start < stop

At each step the either the set of operators or the set of orderings or the set of causal links are updated until all goals are met. If an ordering isn't needed it will not be set.
At the end we will have a set of partially specified and partially ordered operators and then the partial order will be linearized to one of the possible total order.

### Causal links
A causal links is a triple <Si, Sj, c>. Si and Sj are two operators and c is a sub-goal that is a consequence of Si and a condition to be met for Sj.
A __threat__ is an action Sk that, as effect, negates c and no ordering constraint exists to prevent Sk to be ordered between Si and Sj.
Possible solutions:
- __Demotion__: Sk < Si is imposed
- __Promotion__ Sj < Sk is imposed

## Pseudocode
```python 
def POP(inital_state, goal, operators):
	plan = new Plan([GetInitialAction(initial_state), getFinalAction(goal)])
	while true:
		if isSolution(plan):
			return plan
		Sn, C = selectSubgoal(plan)
		chooseOperator(plan, operators, Sn, C)
		resolveThreats(plan)

def selectSubgoal(plan):
	Sn, C = selectActionWithUnsolvedPrecondition(Plan)
	return (Sn, C)
def ChooseOperator(plan, operators, Sn, C)
	S = chooseActionWithEffect(plan,operators,C)
	if S is None:
		raise NotExistingPlanException(f"No action satisfies precondition {C}")
	plan.addCausalLink((S, Sn, C))
	plan.addOrderingConstraint(S,Sn)
	if S.isAction():
		plan.AddSteps(S)
		plan.addOrderingConstraintAfterStart(S)
		plan.addOrderingConstraintBeforeEnd(S)
def resolveThreats(plan):
	for threat in plan.threats:
	S_threat, Si, Sj = threat.components()
	action = choosePromotionOrDemotion(S_threat, Si, Sj)
	if(action == "promotion"):
		plan.addOrderingConstraint(S_threat,Si)
	if(action == "demotion"):
		plan.addOrderingConstraint(Sj,S_threat)
	if plan.notConsisten():
		raise NotConsistenPlanException(f"plan {plan} not consistent")
```

## Modal truth criterion

Often __promotion__ and __demotion__ are not enough to ensure the completeness of the planner, and we have to use other methods to resolve conflicts. MTC is a construction process that guarantees planner completeness:
- __Establishment__: open goal achievement by means of: (1) a new action to be inserted in the plan, (2) an ordering constraint with action already in the plan or simply (3) of a variable assignment.
- __Promotion__: as before
- __Demotion__: as before
- __White knights__: insert a new operator or use one already in the plan to establish the needed precondition
- __Separation__: insert a _noncode design constraint_ between variables of the negative effect and the threatened precondition to avoid unification.