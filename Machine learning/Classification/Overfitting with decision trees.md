A [[Decision tree]] can be defined as a set of _hypotesis_ (h) of the relationship between the predictor attributes and the class. 
A decision tree [[overfitting|overfits]] with a set of hypotesis when we can find a new set of hypotesis (h') such as:
$$
\begin{align}
\text{error}_{\text{train}}(h) &< \text{error}_{\text{train}}(h')\\
\text{error}_{\mathcal{X}}(h) &> \text{error}_{\mathcal{X}}(h')\\
\end{align}
$$