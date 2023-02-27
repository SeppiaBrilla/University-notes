It is a [[Deductive planning]] tecnique that aims at resolving a [[Planning]] problem as a [[First order logic]] deduction.
It maps the world in [[State|states]] and the first one is called __situation__.
In order to resolve the Frame problem, we add to each state an extra axiom:
$F^{t+1} \Leftrightarrow Action^t \wedge (F^t \wedge \neg \text{actionthatcausesnotF})$
