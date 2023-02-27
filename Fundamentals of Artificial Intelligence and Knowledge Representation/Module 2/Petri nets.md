Are graphs used to represent [[Business Process Management]] or process languages in general. They use places (circle), transitions (labelled rectangle) and connections (arcs allowed only between places and transitions).
Tokens are used to control and change the state of the net. Transition are allowed only if the rules of the transition are met => only if all the places connected with the transition have a token. Then the tokens are removed from the places connected with the transition and added to the places the transition is connected with. 
Petri Net represent the process model. The transitions are the activity model. The instances
are the tokens. Firing a transition is an activity execution. If there is at least a token, it is a
process instance.

Advantage: formal semantic, graphical representation, tool independence
Problems: token cannot be distinguished, they can host a single process instance at a time.

## Type of nets

- __Condition events nets__: at each point, a place, can only have one token
- __Place transition nets__: a place can host more token and arcs can have a weight (number of
   token to be consumed or produced) but still tokens cannot be distinguished
- __Coloured Petri Nets__: tokens have colour (value attached to them) with a domain an allowed operation. Transitions depends also on the base of the colour. Problem: similar to [[First order logic|FOL]] so, undecidable.