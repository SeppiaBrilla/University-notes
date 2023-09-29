As for [[CSP|CSP]], with [[Satisfiability Modulo Theory (SMT)]] we can [[Theory solvers|solve them]] or even optimize their solution.
We can find two main approach to SMT optimizer:
- offline: search of optimal solution as an upper instance of the normal solver
- inline: search during normal solver execution

Offline pseudocode method:
![[Pasted image 20230428153722.png]]