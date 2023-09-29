Is a [[Population based search]] inspired by evolution with three key components:
- Adaptation: organism are suited to their habitats
- Inheritance: offspring resemble their parents
- Natural selection: new types of organisms emerge and those that fails to change adequately are subject to extinction

--->

- the fittest individuals have high chance of having numerous offspring
- the children are similar, but not equal, to their parents
- the traits characterizing the fittest individuals spread across the population, generation by generation


### Genetic operators
- **Crossover**: combination of two chromosomes
- **Mutation**: each gene has probability pM to be flipped
- **Proportional selection**: the probability of an individual to be chosen is proportional to his fitness
- **Generation replacement**: the new generation completely replace the old one. This approach is very simple, easy to compute and easier to analize, but it might lose good solutions lost on the new generation. To solve this problem is possible to keep the best ns individuals of the old generation

### Pseudocode
```python
def GeneticAlgorithm():
	population = initializePopulation()
	evaluatePopulation(population)
	while not Termination_conditions: # Execution time, satisfactory soltion(s), stagnation
		new_population = []
		while not new_population_completed:
			parent1, parent2 = getParents(population)
			individuals = mating(parent1,parent2)
			individuals = applyCrossover(individuals)
			individuals = mutation(individuals)
			new_population.append(individuals)
		population = new_population
		evaluatePopulation(population)
```

The crossover function combines the good parts from good solutions (not guarantee)
The mutation introduces diversity and the selection move the population towards high fitness