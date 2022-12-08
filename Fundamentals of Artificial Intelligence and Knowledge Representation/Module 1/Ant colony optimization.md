Ant colony optimization is a [[Swarm Intelligence]] algorithm. 
Any individual leave behind him some sort of "pheromon" that the other individuals will follow.
Uses a probabiistic parametrized model ([[Define a model for learning process in AI|here some notes on probabilistic models]]) to model pheromon trails and the solution is build in an incremental way with stocastics steps in a fully connected graph called _construction graph_ G = (C,L) with C being vertexes / solution components, L arcs / connections and States being path on G.

Pseudocode:
```python
def ACO():
	initializePheromonesValues()
	while termination_conditions:
		for ant in ants:
			solution_a = buildSolution(pheromones, heuristic)
		applyOnlineDelayedPheromoneUpdate()
```

We also save in memory the past paths in order to avoid loops. Starting from node I we chose probabilistically the next consistent node to visit. 
The probablisitic choice depends on:
- pheromone trails $\tau_{ij}$ 
- heuristic $\eta_{ij} = \frac{1}{d_{ij}}$
$$
p_{ij} =
\begin{cases}
 &\frac{\tau_{ij}^\alpha * \eta_{ij}^\beta}{\sum_k feasible \tau_{ij}^\alpha \eta_{ij}^\beta} & \text{if j is consistent}
\\&0 & \text{otherwise}
\end{cases}
$$
$\alpha$ and $\beta$ weight the importance of the pheromones and the heuristics.
The pheromone is updated with the following rule:
$$
\begin{align}
&- \; \; \tau_{ij} = (1 - p)\tau_{ij} + \sum_{k = 1}^{m}\Delta\tau^k_{ij} \; \text{(p: evaporization coefficient)}\\
&- \; \; \Delta\tau_{ij} = 
\begin{cases}
\frac{1}{L_k} & \text{if ant k used arc ij}\\
0 & \text{otherwise}
\end{cases}\\
&- \; \; L_k = \text{lenght of the path followed by ant k}
\end{align}
$$

Some "_demon actions_" can be applied to alter the standard execution of the algorithm like leave additional phermones or [[Local search]] procedure on a state to improve it.