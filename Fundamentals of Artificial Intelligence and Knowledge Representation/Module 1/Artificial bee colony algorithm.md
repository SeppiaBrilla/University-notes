Is a [[Swarm Intelligence]] algorithm. Each "bee" can be:
- an __employed bee__ that is associeted with a specific "nectar source" (good solution for the problem)
- an __onlooker__ that observe emplyed bees and choose a "nectar source" accordingly
- a __scout__ that discover new food source

At the initial stare the food (solutions) is discoverd by scout bees that then consume the food source (becoming enployes) and, as soon as the food is exausted the bees in that source become scout again. The food quantity is represented by the fitness of the solution.

## Pseudocode
```python
def ABC():
	initializationPhase()
	while !max_cycle_reached and !max_cpuTime_reached:
		employedBeePhase()
		onlookerBeePhase()
		scoutBeePhase()
		sol = BestSolutionSoFar
	return sol
```

### initializationPhase
A seto of food source position are randomly selected by the bees and their food amounts are determinated. Each solution $X_m$ is composen by n variables subjected to an upper and lowe bound initialized to:
$$
X_{mi} = Ibi + rand(0,1)(ubi-Ibi)
$$
### employedBeePhase
after sharing the information about the nectar amount every employed bee goes to the food source and then choose a new source by selecting in the neighbour of the present one.
We compute the fitnes of the solution as:
$$
ftn(X_m) = 
\begin{cases}
\frac{1}{(1 + obj(X_m))} & obj(X_m) \geq 0\\\\
1 + |obj(X_m)| & obj(X_m) < 0 
\end{cases}
$$
where obj is the objective function.

### onlookerBeePhase
An onlooker bee choses a food source depending on the probability value associeted with that food source:
$$
p_m = \frac{ftn(X_m)}{\sum_{i = 1}^{Npopol} ftn(X_i)}
$$
this is a positive feedback.

### scoutBeePhase
a scout choose a nectar source at random. An employed bee becomes a scout when it can not improve a solution after a given number of attempts.
this is a negative feedback