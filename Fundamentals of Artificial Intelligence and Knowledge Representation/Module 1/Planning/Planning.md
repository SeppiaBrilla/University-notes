Automated planning is an important problem to solve activites on which a series of actions are needed to go from an initial state to a goal. 
An __automated planner__ is an agent that operate in a certain domain described by:
1) a representation of the initial state
2) a representation of the goal
3) a formal description of the executable actions (operators)

## a formal definition:
__planning is a process for deciding the steps ([[actions]]) that solve a problem__ 

### a planning problem is:
- non decompostable: sub goals may interact between each other
- reversible: the choices are backtrackable

### a planning is:
- complete if it always find a solution if it exists
- correct if the solution actually works

## execution of a planning
Is:
- irreversible
- non deterministic (the world cannot be perfectly expressed in the planning phase so, each action may have different effects from we expect)ù


## planning techniques
- [[Deductive planning]]
- [[Planning as a search]]
- [[Linear planning]]
- [[Non-linear planning - Partial order planning (POP)]]
- [[Hierarchical planning]]
- [[Conditional planning]]
- [[Graph-based planning]]
- [[Generative planning]]
- [[Strips]]
- [[Fast forward]]