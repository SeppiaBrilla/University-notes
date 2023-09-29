Computer programming can take two different approaches:

## Imperative programming
Where the programmer takes care both of the definition of a solution and the definition of the steps the computer must take to reach the solution. Imperative programming languages are python, c#, c++, etc...

## Declarative programming
In this kind of programming approach, the programmer only defines the kind of solution he/she wants to obtain, and the computer take cares of the search. This kind of approach requires the language to be interpreted and a program that performs the search. It is, tho, much more desirable for a lot of problems like [[CSP|Constraint satisfaction problems]] where we need to find an optimal solution and not just a solution. Moreover, it is very interesting from a theoretical point of view and can avoid the need to define an optimized program to search a solution (thus, we can avoid relying on those terrible engineers who cannot write decent code). A downside is that, searching for a solution in the general case, remains a np-complete problem and, even tho we have very efficient solver, in some cases the search can be very long and take exponential time.
Other types of declarative languages are Lisp, Ocaml, Prolog.



## EBNF

EBNF stands for Extended [[Logic deduction and formulation|Backus-Naur Form]] and it is defined as:
$$
\text{Name} : G, H::= A|B, \text{condition} 
$$
where,
- capital letters are syntactical entities
- symbols G and H are defined by the rule with name Name.
- if Condition holds, then G and H can be of the form A or B.

## Refined calculus

A refined calculus is a triple $(\Sigma, \equiv, T)$, where:
- $\Sigma$ is a signature for a [[First order logic]] language
- $\equiv$ is a congruence relation on states
- $T$ is a transition system 

The congruence is used to identify states which are considered equivalent for the purpose of computation.

The transition rules for propositional logic are the following:
- __Resolvent__: if $R \vee A$ e $R' \vee \neg A$ $\in S$, then $S \mapsto S \cup \{F\}$ where $F = R \vee R'$ is a resolvent
- __Factor__: if $R \vee L \vee L \in S$, then $S \mapsto S \cup \{F\}$ where $F = R \vee L$ is a factor

The same two rules can be applied also when $\sigma(f)$ is the most general unifier of two atoms and f is the resolvent/factor formula.