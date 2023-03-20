Another well-known non-linear edge preserving smoothing [[Image filters]]. The key idea is that the similarity among patches spread over the image can be deployed to achieve [[Noise]] reduction. 
![[Pasted image 20230309192419.png]]
$$
\begin{align}
O(p) = \sum_{q \in S} w(p,q)I(q)\\
w(p,q) = \frac{1}{Z(p)}e^{-\frac{||N_p - N_q||_2^2}{h^2}}\\
Z(p) = \sum_{q \in I}e^{\frac{||N_p - N_q||_2^2}{h^2}}\\
\end{align}
$$