
# [[Proposition logic]]

We can have:
- symbols 
- connectives ($\vee, \wedge, \rightarrow, \neg, \leftrightarrow, \bot$)

Atomic proposition are symbols and $\bot$.

## Backus-Naur Form
BNF (or Backus-Naur Form) is a logical proposition written in the following way:
$$
\begin{align}
< \text{formula} > &::= \text{atomic proposition} \\
&| \neg< \text{formula} > \\
&| < \text{formula} > \wedge < \text{formula} > \\
&| < \text{formula} > \vee < \text{formula} > \\
&| < \text{formula} > \rightarrow < \text{formula} > \\
&| < \text{formula} > \leftrightarrow < \text{formula} > \\
&| (< \text{formula} >)
\end{align}
$$
![[Pasted image 20230628201114.png]]

### Interpretation
Given a propositional formula G, let $\{A_1, \dots, A_n\}$ be the set of atoms which occur in it, an __interpretation__ I of G is an assignment of truth values to $\{A_1, \dots, A_n\}$
Given a formula G and an interpretation I, if G is true under I, we say that I is a model for G, and we can write $I \models G$.
If a formula is true for every interpretation is valid / a tautology, if it is false for every interpretation is inconsistent.

### Normal form
Two kinds:
- CNF (conjunctive normal form) : $F_1 \wedge \dots \wedge F_n$ where $F_i$ are conjunction of literals. 
- DNF (disjunctive normal form) : $F_1 \vee \dots \vee F_n$ where $F_i$ are disjunction of literals, and it is in NNF.

NNF: if negation appears only in front of atoms

### Logical consequence
Given a set of formulas F and a formula G, G is a logical consequence of F if, for every possible interpretation, $G \Rightarrow F$. 

## Natural deduction

$$
\begin{align}
\begin{prooftree}
\AxiomC{A \; B}
\RightLabel{(Introduction of and)}
\UnaryInfC{A and B}
\end{prooftree}
\;\;\;\;
\begin{prooftree}
\AxiomC{A \; B}
\RightLabel{(Elimination of and)}
\UnaryInfC{A}
\end{prooftree}
\\
[A]\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;
\\
\begin{prooftree}
\AxiomC{B}
\RightLabel{(Introduction of implication)}
\UnaryInfC{A -> B}
\end{prooftree}
\;\;\;\;
\begin{prooftree}
\AxiomC{A \; A -> B }
\RightLabel{(eliminatio of implication)}
\UnaryInfC{B}
\end{prooftree}
\\
[\neg A]\;\;\;\;\;\;\;\;\;\;\;\;
\\
\begin{prooftree}
\AxiomC{bottom}
\RightLabel{(bottom)}
\UnaryInfC{A}
\end{prooftree}
\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;
\begin{prooftree}
\AxiomC{bottom}
\RightLabel{(RAA)}
\UnaryInfC{A}
\end{prooftree}
\end{align}
$$

## Resolution

Resolution works by contradiction: in order to prove that A is true, it proves that $\neg$A is false.


# [[First order logic]]

It is composed by a signature $\Sigma = (P,F)$ of a first-order language:
- P is a finite set of predicate symbols each with arity $n \in \mathbb{N}$
- F is a finite set of function symbols each with arity $n \in \mathbb{N}$

A well-formed formula is composed of atomic formulae, negation of formulae, conjunction/disjunction/implication of formulae and quantifiers.
FOL also uses variables (with quantifiers or free) to denote things.
A sentence (formulae connected together) can be:
 - valid: true for every interpretation
 - satisfiable: true for some interpretations
 - falsifiable: not true for some interpretation
 - unsatisfiable: always false
An interpretation is the same as for Proposition logic

## Herbrand Interpretation

A formula is valid if there exists a variable assignment that, for every interpretation, make the formula true.


## Calculus

### Negation normal form
As for Proposition logic, a formula is in NNF if:
- there is no implication
- in every sub-formula with $\neg F$, F is atomic

