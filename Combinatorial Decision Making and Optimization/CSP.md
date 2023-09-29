Note: this is an extension on the [[Fundamentals of Artificial Intelligence and Knowledge Representation/Module 1/Costraints/Constraint satisfaction problem|constraints]] notes taken for module one of FAIKR course. It is more in depth but cover more or less the same things.  

A Costraint satisfaction problem, also called CSP, is a triple $<X,D,C>$ where X is the set of variable to fill, D is the variable domain, C is a set of constraints.
A solution to a CSP problem is a variable assignement with domain values that respect the constraints.
A CSP problem could also have additional optimization criterion like maximise or minimize some parameters (e.g. costs, profit, ...), so we can extend our CSP definition with a new value $f \Rightarrow <X,D,C,f>$ where f is the optimization criterion (a function to minimize / maximise).

### Example of a CSP, the N-Queens problem:

| Q   |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- |
|     |     |     |     |     |     | Q   |     |
|     |     |     | Q   |     |     |     |     |
|     |     |     |     |     | Q   |     |     |
|     |     |     |     |     |     |     | Q   |
|     | Q   |     |     |     |     |     |     |
|     |     |     |     | Q   |     |     |     |
|     |     | Q    |     |     |     |     |     |

Place n queens on an $n \times n$ board. 
We can model the CSP as follows:
- Variables, X: one for each row $[X_1, \dots, X_n]$, this way we can ensure they don't attach each other row-wise
- Domain values, D: $[1, \dots, n]$ a value for each column, in this case if we assign values j at variable $X_i$ we will have a queen on row i at column j.
- Constraits: 
	1) $\text{alldifferent}([X_1, \dots, X_n]) \rightarrow \; \text{no column attack}$
	2) $\forall i < j: |X_i - X_j| \neq |i - j| \rightarrow \; \text{no diagonal attack}$


Here you can find a more in depth view on how to model constraints: [[Constraints]]