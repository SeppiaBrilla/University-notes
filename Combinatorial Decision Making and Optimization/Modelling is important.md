The domain space is exponential in size because, in order to get the full search space, we need to compute the cartesian product of every variable. Because of that, we need to define our model such that we can prune wrong solution as fast as possible. 

There are some tools we can use to improve our models like: 
- [[Auxiliary variables]]
- [[Implied constraints]]

## An example, the [Golomb ruler](https://en.wikipedia.org/wiki/Golomb_ruler):

We want to place m marks on a ruler such that the distance between each pair of marks is different and the length of the ruler is minimum.
__A naive approach__:
	- Variables: $[X_1, X_2, \dots, X_m]$, marks on the ruler
	- Domain: $\{0, 1, 2, \dots, 2^{(m - 1)}\}$
	- Constraints: $\forall i_1, j_1, i_2, j_2, i_1 \neq i_2 or j_1 \neq j_2, |X_{i_1} - X_{j_1}| \neq |X_{i_2} - X_{j_2}|$
	- Objective: minimize(max($[X_1, \dots, X_m]$))
	With this model the problem is $O(m^4)$.

__A better approach__:
	Introduce a new set of variables, $D_{i,j}$, representing the distance between the $i^{\text{th}}$ and the $j^{\text{th}}$ marks. To express the value of these variables, we must introduce a new set of constraints:
	- $\forall i< j, D_{i,j} = |X_i - X_j|$ 
	- $\text{alldifferent}([D_{1,2}, D_{1,3}, \dots, D_{(m - 1),m}])$
	The "alldifferent" constraint is an implied one while the Ds variables are auxiliary. This new model reduces the computational cost to $O(m^2)$ which is waaay better.

We should also keep in mind that there may be some problems when the order of the variable is non-significant. In those cases, we could have a [[Symmetry inc CSPs|symmetry problem]]