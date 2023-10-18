There can be two types of errors we may need to check:
- Non-word spelling, e.g. cst - cat
- Real word spelling correction, e.g. there - three

For both kind of errors, we can generate a list of alternatives by looking at our dictionary and pick the most probable alternatives given the context and the [[Word similarity|distance]] between the two words.

## The noisy channel model

In the noisy channel model, we imagine that the surface form we see is actually a “distorted” form of an original word passed through a noisy channel. The decoder passes each hypothesis through a model of this channel and picks the word that best matches the surface noisy word. 
Therefore, our estimation of a word w is: $\hat{w} = \text{argmax}_{w \in V} P(w|x)$ where $\hat{w}$ is our prediction and x is the "noisy" word.
Using the [[Bayes theorem]] we can:
$$
\begin{align}
P(w|x) = \frac{P(w|x)P(w)}{p(x)}\\
\hat{w} = \text{argmax}_{w \in V} P(w|x) =\\
\text{argmax}_{w \in V} P(x|w)P(w)
\end{align}
$$
And we can also restrict the search to a set of candidates computed with a distance function. This way we have that P(x|w) is our channel model and P(w) is our prior knowledge. The prior can be computed as the absolute probability of the appearance of a word or the relative value of its appearance given the context.

Since most of the error are just one letter errors, we can exploit this knowledge by using the Damerau-Levenshtein distance with distance 1 and then make a list of candidates using a score function based on some feature we know (e.g. the context)

The current state of the art of this model also uses some extensions like:
- Methods to prevent overcorrecting, such as black lists and larger thresholds for suggesting a correction
- Methods to decide whether to autocorrect or just flag
- Adapt to user input
- Weight language and error model differently
- Make better use of context
- Probabilities for multiple-letter transformation (e.g. ph - f)
- Letter-to-sound models
-  ...