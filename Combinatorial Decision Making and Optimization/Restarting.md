It is a technique to avoid [[Heavy tail behaviour]] in [[Constraint solver]] algorithms.
It restarts the search in a different branch after a certain amount of resources has been used.
There are several ways to implement restart:
- Constant (after L resources)
- Geometric (after $\alpha^*$L resources, where * increases each time)
- Luby: restarts after sL resources were consumed. s is the [Luby sequence](http://www.cs.cmu.edu/~mheule/publications/rapid.pdf).  