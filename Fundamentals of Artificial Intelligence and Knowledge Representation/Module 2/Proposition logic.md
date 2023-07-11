It is a kind of [[Fundamentals of Artificial Intelligence and Knowledge Representation/Module 2/Logic]]. In proposition logic, each symbol can be either true or fals, and they are called propositions or atoms or atomic formulas or Pi.
Pi can be connected together with connectives:
$\wedge, \vee, \rightarrow, \neg, \leftrightarrow, \perp$    
An __well-formed__ formula is:
- an atomic formula Pi
- if A, B are well-formed formulas then: $A \wedge B, A \vee B, A \rightarrow B, \neg A$ Are also well-formed formulas

### Tautologies
formulas that, no matter how we assing the value of the Pi, it will always be true 
(e.g. $A \vee \neg A$)

### Inconsistent formulas
formulas that, no matter how we assing the value of the Pi, it will always be false 
(e.g. $A \wedge \neg A$)

## Logical equivalences
$$
\begin{align}
(A \wedge B) &\equiv (B \wedge A)\\
(A \vee B) &\equiv (B \vee A)\\
((A \wedge B) \wedge \gamma) &\equiv (A \wedge (B \wedge \gamma))\\
((A \vee B) \vee \gamma) &\equiv (A \vee (B \vee \gamma))\\
\neg(\neg A) &\equiv A\\
A \Rightarrow B &\equiv \neg A \Rightarrow \neg B\\
A \Rightarrow B &\equiv \neg A \vee B\\
A \Leftrightarrow B &\equiv (A \Rightarrow B) \wedge (B \Rightarrow A)\\
\neg (A \vee B) &\equiv \neg A \wedge \neg B\\
\neg (A \wedge B) &\equiv \neg A \vee \neg B\\
(A \wedge (B \vee \gamma)) &\equiv (A \wedge B) \vee (A \wedge \gamma)\\
(A \vee (B \wedge \gamma)) &\equiv (A \vee B) \wedge (A \vee \gamma)\\
\end{align}
$$

### Logical consequence

Let $\Gamma = F_1, \dots, F_n$ a set of sentences, F is a consequence of $\Gamma$, written $\Gamma \models F$ if in any interpretation where $\Gamma$ is true, F is also true.