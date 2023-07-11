[[Lazy approach to solve SMT|Lazy]] [[Satisfiability Modulo Theory (SMT)|SMT]] solvers can be seen as a collection of theory solvers.
A theory solver must have the following characteristics:
- __Incrementability__: the T -solver incrementally checks new literals with a cost proportional to the size of the addition
- __Backtrackability__: the solver can undo steps and return to a previous state efficiently
- __Literal deduction__: the solver can perform deductions of literals not yet assigned in the input formula
- __Explanation generation__: when a conflict involving a literal $l$ is found, is necessary to have a (possibly short) explanation $l_1 \wedge \dots \wedge l_n \rightarrow l$ for performing conflict analysis and determine how far to backtrack.

## Theory combination

Often, a formula may involve more than a theory and, in order to solve it, we need to combine different theories:
1) __purification__: first, we divide the literals in groups, one for each theory
2) __Check and exchange__: then we solve the theories indipendently and, if all of them are SAT, we exchange information between them to combine the solutions

Example:
$$
\begin{align}
\text{formula:}& \; f(f(x) - f(y)) = a \wedge f(0) = a + 2 \wedge x = y \\
\text{purified formula:}& \\ 
&e_1 = e_2 - e_3, e_4 = 0, e_5 = a + 2 \;(\text{LA}), \\ 
&f(e_1) = a, e_2 =f(x), e_3 = f(y), f(e_4) = e_5, x = y  \;(\text{EUF}) \\
\text{solve and exchange}: & \\
&\text{EUF:} \; \{x = y, f(x) = e_2, f(y) = e_3\} \models e_2 = e_3\\
&\text{LA:} \; \{e_2 - e_3 = e_1, e_4 = 0, e_2 = e_3\} \models e_1 = e_4\\
\Rightarrow &\text{EUF:} \{f(e_1) = a, f(e_4) = e_5, e_1 = e_4\} \models e_5 = a\\
\Rightarrow &\text{LA:} \{e_5 = a + 2, a = e_5\} \models \bot
\end{align}
$$

### Nelson-Oppen procedure

Let $\sum_1, \sum_2$ be signature and $T_1, T_2$ their theories, if $T_1, T_2$ are:
- signature-disjoint: $\sum_1 \cap \sum_2 = \emptyset$ 
- stably-infinite: $\sum$-Theory $T$ of sort $\sigma$ is stably infinite if every $T$-staisfiable $\sum$-formula has a model interpreting $\sigma$ as an infinite set
- convex: foreach set of $T_i$-literals S we have: $S \models_{T_i} a_1 = b_1 \vee \dots \vee a_n = b_n \rightarrow S \models a_k = b_k \text{ for some } k \in \{1, \dots, n\}$  
Then we can chek ($T_1 \cup T_2$)-atisfiability with the deterministic Nelson-Oppen algorithm

pseudocode:
```python
NOp(S):
	S1, S2 = purify(S)
	if not solve(S1) or not solve(S2):
		return "UNSAT"
	x, y = solve(S1)
	if (x = y) and in E - S2:
		if Solve(S2 + [(x = y)]):
			return "SAT" 
	x, y = solve(S2)
	if (x = y) and in E - S1:
		if Solve(S1 + [(x = y)]):
			return "SAT" 
```

If we cannot rely on the convex property, we will need to use the non-deterministic Nelson-Oppen procedure which works through arrangements of shared constants, basically doing  
case splitting $x = y \vee x \neq y$ between pairs of shared constants x, y, but it is exponential in the worst case scenario.


### Extension
There are several extensions and enhancements to the SMT  
framework. Hierarchical approach: the problem is stratified in layers L1, L2, ... of increasing complexity, solved by solvers of increasing expressiveness.
![[Pasted image 20230428152325.png]]

### Case splitting
Sometimes it is easier to proceed "per case" and splitting the formula in different cases to solve indipendently.