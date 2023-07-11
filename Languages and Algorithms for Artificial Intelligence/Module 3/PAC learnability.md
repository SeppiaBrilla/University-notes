Every [[Supervised learning|learning]] problem can be seen as a [[The standard paradigm|task]] taking as input data and giving as output a string representation of a [[Classification]] algorithm.
The problem can be assumed to work with an instance space X that contains the encoding of the instances we want to classify. 
X can be generated with a given (unknown) distribution D that we want to learn.
A concept class C is a collection of concepts, namely a subset of P(X). These are the concepts which are sufficiently simple to describe, and that algorithms can handle. The target concept $c \in C$ is the concept the learner wants to build a classifier for.

The interface of any learning algorithm A can be described as follows:
![[Pasted image 20230524161447.png]]

Where:
- $\delta$ is a confidence parameter
- $\epsilon$ is an error parameter
- EX(c,D) is an "oracle" that produces an element x from D correctly classified.

The error of any $h \in C$ can be defined as:
$$
error_{D,c} = Pr_{x \sim D}[h(x) \neq c(x)]
$$
### PAC learnable definition
Any concept class C over the instance space X is PAC learnable iff there is an algorithm A s.t. 
$$
\begin{align}
\forall c \in C, \forall D, \forall \epsilon,  0 < \epsilon < \frac{1}{2}, \forall \delta,  0 < \delta < \frac{1}{2}:\\
Pr[error_{D,c}(A(Ex(c,D),\epsilon,\delta)) < \epsilon] > 1 - \delta
\end{align}
$$

If the time complexity of A is bounded by a polynomial in $\frac{1}{\epsilon}$ and $\frac{1}{\delta}$, we say that C is efficiently PAC learnable.