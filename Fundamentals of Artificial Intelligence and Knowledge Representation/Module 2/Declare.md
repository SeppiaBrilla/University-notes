Delcarative open process modelling is based on the declarative approach ([[Business Process Management]]).
There can be unary constraints (atomic activities, existance, existance_n, absence) and binary constraints that connect activity and impose a temporal ordering. The number of line in the connection change the meaning of that connection:
- Two lines: no repetition of the triggering activity before the constraint is satisfied
- Three lines: no other activities allowed before the constraint is satisfied

### Properties that can be verified

- Enactment of a process model
- conformance checking: given a log, check if it respects all the constraints
- interoperability: combinig different system built via DECLARE methods