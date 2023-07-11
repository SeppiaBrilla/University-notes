 Is a problem we can solve with [[Satisfiability Modulo Theory (SMT)]].  
 Consider LRA = Linear Real Arithmetic theory, having signature $\sum_{LRA} = (\mathbb{Q}, +, -, *, \leq)$ and linear multiplications only.
 We could decide LRA-literals with Fourier-Motzkin elimination:
 - Replace $t_1 \neq t_2$ with $t_1 \vee t_2$ and $t_1 \leq t_2$ with $t_1 < t_2 \vee t_1 = t_2$
 - Eliminate equalities and apply [Fourier-Motzkin elimination](https://en.wikipedia.org/wiki/Fourier%E2%80%93Motzkin_elimination) to all variables to determine its satisfiability