It is a kind of [[Logic]] built upon [[Proposition logic]].
Given this, we can define FOL as: 
- The set of constants (always true or always false)
- The set of function symbols (e.g. appear_on(film) $\equiv$ TV)
- The set of variables 
- The set of predicate symbols
- The set of logical connectives (as in proposition logic but with $\exists \; \text{and} \; \forall$ included)

# Way of reasoning

We now need a way to decide if a formula is true or not. In order to do so, we can introduce the concept of __engine__.

### Engine
an engine is a method of reasoning on a logic formula in order to assing to that formula a value (T o F).
We write $F_1 \wedge \dots \wedge F_n \dashv^E G$ to denote that the formula G is deducible from $F_1 \wedge \dots \wedge F_n$ with the engine E.

### Sound
A method E is said to be sound if holds: $\Gamma \dashv^E \varphi \Rightarrow \Gamma \models \varphi$.

### Complete
A method E is said to be sound if holds: $\Gamma \models \varphi  \Rightarrow \Gamma \dashv^E \varphi$.

## Reasoning by deduction

__Theroem__: Given a set of formulas $\{F_1, \dots, F_n\}$ and a formula G, $F_1 \wedge \dots \wedge F_n \models G$ if and olny if $\models (F_1 \wedge \dots \wedge F_n) \rightarrow G$.
The proof procede by absurd, prooving that  $F_1 \wedge \dots \wedge F_n \wedge \neg G$ is inconsistent.