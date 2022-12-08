It is a set of [[Meta heuristics]] rules to improve [[Iterative improvement - hill climbing]] search. It allows moves in states that represent a worse solution to the current one but with decreasing probability of doing so during search. Normally:
$$
p(down-hill \; move) = e^{\frac{(-(f(s')-f(s)))}{T}}
$$
The T value is called temperature and can be varied in different ways:
- Logaritmic: $T_{k+1} = \frac{\Gamma}{log(k + k_0)}$. It converge always to the optimal solution but is very slow
- Geometric: $T_{k+1} = \alpha T_k$ where $\alpha \in ]0,1[$ 
- Non monotonic: the T value is decreased (intensification is favored), then increased again (to increase diversification)