Hill climbing is a [[Local search]] strategy to find a solution to a problem. The idea is to iterate untill a local optimal solution has been found. At each step the algorithm move to the next state only if it is a better solution to the problem than the current one.
## Main problems:
- __Local optima__: the state is the better of all neighbours but not the better in general
- __Plateau__: a flat area where all the states have the same value. In which direction to move?
- __Ridges__: It's an higher area adiacent to those where we should go, but we cannot go there directly. 