Let's consider a node p with $C_p$ classes. Foreach class j the frequency of j in p will be $f_{j,p}$, while the frequency of other classes will be $1 - f_{j,p}$. The probability of a wrong assignment will, then, be: $f_{j,p} * (1 - f_{j,p})$. The GIni index is the total probability of wrong classifications: 
$$
\sum_j f_{j,p} * (1 - f_{j,p}) = \sum_j f_{j,p} - \sum_j f_{j,p}^2 = 1 - \sum_j f_{j,p}^2 
$$
The maximum Gini index value will be $1 - \frac{1}{C_p}$, when all the records are uniformly distributed and the minimum value will be when all the records belongs to the same class: 0

## Gini index for [[Decision tree|decision trees]]
When we want to use the Gini index for [[Pattern finding and evaluation]] of decision trees we will:
- split the node p in ds descendants ($p_1, \dots, p_{ds}$)
- choose the split giving the maximum reduction of the Gini index:
	$$
	\text{GINI}_{\text{split}} = \text{GINI}_{p} - \sum_{i = 1}^{ds}\frac{N_{p,i}}{N_p}\text{GINI}(p_i) 
	$$
	With $N_{p,i}$ the number of records in the $p_i$ and $N_p$ the number of records in p