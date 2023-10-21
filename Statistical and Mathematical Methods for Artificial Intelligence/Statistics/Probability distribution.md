Consider two [[Random variable]] $X,Y$ where $X$ has 5 possible values and $Y$ has 3 possible values. We denote $n_{i,j}$ the number of events with state $X = x_i, Y = y_j$ and we call $N$ the total number of events. 
Then we can denote with $c_i$ the sum of the individual frequences on the i-th column such as $c_i = \sum_{j = 1}^3 n_{i,j}$ and $r_j$ the sum of the individual frequences on the j-th row such as $r_j = \sum_{i = 1}^5 n_{i,j}$ 
![[table_probability.jpg]]

Now we can compute the [[Probability]] of the value of each [[Random variable]]
$P(X = x_i) = \frac{c_i}{N} = \frac{\sum_{j = 1}^3 n_{i,j}}{N}$ and $P(Y = y_j) = \frac{r_j}{N} = \frac{\sum_{i = 1}^5 n_{i,j}}{N}$.
Then the [[Conditional distribution]] is given by:
$P(X = x_i| Y = y_j) = \frac{n_{i,j}}{r_j}$ and $P(Y = y_j|X = x_i) = \frac{n_{i,j}}{c_i}$ 
