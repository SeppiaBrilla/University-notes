It is a [[Modal logic]] built on atomic proposition whose truth value can change over time. It uses [[Temporal logic]]. It is linear (single next future), qualitative (time relation between propositions), point based (point in time), discrete and future-tense (events in the future).

## LTL model

Let P the set of all atomic propositions. An LTL model is a triple $(K, \succ, v)$ where $v: P \rightarrow 2^K$ is a function mapping each proposition in P to the set of time instants at which the proposition holds.


## LTL execution trace

Given a set L of atomic proposition (representing possible events) an LTL execution trace is a LTL model having $(N,<)$ as time structure and L as atomic propositions. In particular, $T = (N, <, v_{acc})$.

In [[Business Process Management]], differently from LTL, execution trace are finite and events cannot happen simultaneously.

In addition to classic operators, in LTL we have temporal operators:
- $\bigcirc$ next time
- $U$ until
- $\diamond$ eventually
- $\square$ globally
- $W$ weak until

![[Pasted image 20230211202008.png]]

We can check properties in an LTL because the system is represented as a formula. We can negate the formula, build two different automata for both formulas (negate and non) and check for deadlock or liveness property