The condition number of a matrix A ($K(A$)) is a number that measure the [[Inherent error]] of A. 
$$
K(A) = ||A||*||A^{-1}|| 
$$
Demonstration:
let $\Delta b$ be a change in the result $b$ such as the $b$ in our data is $b = b + \Delta b$,
the system becomes $A(x + \Delta x) = b + \Delta b$ with $\Delta x$ [[Inherent error]].
let's subtract $Ax = b$ to the "new" system: 
$Ax + A \Delta x - Ax = b + \Delta b - b \Rightarrow A \Delta x = \Delta b \Rightarrow \Delta x = A^{-1} \Delta b$.
Then we have:
$||\Delta x|| = ||A^{-1} \Delta b|| \leq ||A^{-1}|| ||\Delta b||$ 
And:
$||Ax|| = ||b|| \Rightarrow ||b|| = ||Ax|| \leq ||A|| ||x|| \Rightarrow ||x|| \geq ||\frac{b}{A}||$ 
And so we have:
$||\frac{\Delta x}{x}|| \leq ||A^{-1}|| * ||A|| * ||\frac{\Delta b}{b}|| = K(A) ||\frac{\Delta b}{b}||$


