Is a [[Swarm Intelligence]] algorithm for solution optimization.
The idea is to build a swarm of particles that influence each other in the solution search: each particle moves toward the best solution found so far (exploitation) but also search for a better one (exploration). 
An important concept in this algorithm is the "proximity" concept: individuals are effected by actions of other individual in the same group. Each particle belongs in more than one group so that information spread. The groups are decided a priori and are not related to physical proximity.

### Pseudocode

```python
def PSO(theta_g,theta_p, w, particles_number):
	S = particles_number
	g = 0 #best global solutio
	#initialization
	for i in range(S):
		particles[i].x = uniform_random_vector() #x is the position of particle i
		particles[i].p = particles[i].x #p is the best solution found by the particle sofar
		if f(particles[i].p) <= f(g): #f is the function to optimize
			g = particles[i].p
		particles[i].v = uniform_random_vector(-max_search_space_step,max_search_space_step) #the velocity of the particle
		#execution 
	while not terminal_conditions: #max number of cycles or adequate fitness foud
	for i in range(S):
		r_p, r_g = random()
		particles[i].v = w * particles[i].v + theta_p * r_p * (particles[i].p - particles[i].x) + theta_g * r_g * (g - particles[i].x)
		particles[i].x = particles[i].x + particles[i].v
		if f(particles[i].x) <= f(particles[i].p):
			particles[i].p = particles[i].x
		if f(particles[i].p) <= f(g):
			g = particles[i].p
```

theta_p, theta_g and w are parameters that should be carefully chosen as they strongly influence the efficiency theta_p, theta_g and w are parameters that should be carefully chosen as they strongly influence the efficiency
