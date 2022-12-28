We can perform some kind of transformation on our [[Data]]. That may allow us to use algorithms that can work only a specific type of data or to better understand it.
Types of transformation:
- Transformation on [[Nominal data type]]: Any one-to- one corrispondence (SSN / codice fiscale can be reassigned)
- Transformation on [[Ordinal data type]]: any order preserving transformation (good, mid, bad -> 3, 2, 1)
- Transformation on [[Interval data type]]: any linear function
- Transformation on [[Ratio data type]]: any matematical function


## Scaling

Sometimes we may have numerical values with different scales and this could alterate the result of some algorithms (like [[Gradient method]]).
Some attribute transformation methods:
- Mapping the entire dataset to a new set according to a function ($x^k,\log(x),e^x,|x|,\dots$). This process could alter the distribution value
- standarditzation: $x \rightarrow \frac{x - \mu}{\sigma}$ this will bring any [[Gaussian (normal) distribution|Gaussian distributed]] dataset to have a standard gaussia with 0 mean and 1 variance. This translates and strech/shrink the data but do not alter the distribution
- MinMax scaling: domain are mapped to standard ranges $x \rightarrow \frac{x - x_{min}}{x_{max} - x_{min}} \in [0,1]$ or $x \rightarrow \frac{x - \frac{x_{max} + x_{min}}{2}}{\frac{x_{max} + x_{min}}{2}} \in [-1,1]$. This translates and strech/shrink the data but do not alter the distribution.