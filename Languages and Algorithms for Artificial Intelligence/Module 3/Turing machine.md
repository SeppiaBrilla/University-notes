Turing Machine (TM for short) working on k tapes is described as a triple $(\Gamma, Q ,\delta)$ containing:
- $\Gamma$: a finite alphabet, always including two character $\rhd, \Box$ representing respectively initial and blank characters and 0,1 
- $Q$: a fine set of possible states including two special states which indicates the initial and final states.
- $\delta: Q \times \Gamma^k \rightarrow Q \times \Gamma^k \times \{L,S,R\}^k$: a transition function


A configuration, C, contains: the current state q, the content of the k tapes and the position of the k tape heads.