Many AI problems can be solved by exploring the [[solution space]].
The solution is computed iteratively by examinating all the possible sequences of actions and then choosing **the best (or correct) one**. This process is called #search. The process could be immagined as a search tree whose nodes are states and branches are actions. 
The algorithm can take a problem as an input and return a sequence of actions as a solution, then the suggested actions can be perfomed and this process is called #execution.
The algorithm is an optimization problem so, it works in a similar way as [[Iterative algorithms]] used in mathematical function optimization.

## Keywords in solution searching
- #Expansion : starting from a state and applying all possible operations to the given state and generate new states
- [[Search strategies]] : at each step, choose what state expand
- #SearchTree : represents the expansion of all states. The leaves of the tree are solutions or dead ends 

