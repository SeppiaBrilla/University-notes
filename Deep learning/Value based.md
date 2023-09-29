It is a model free approach to [[Reinforcement learning]]. We try to evaluate each state s with a value function.

Each state is as good as the best reward an action can give at that given state. We can, then, compute the value of a state knowing the expected outcome of each action. But, knowing that expected value, would make this a model based technique.
So, we need to approximate that value. We can approximate the expected outcome by exploring the world randomly and saving the obtained outcome at each given state and given action. The value get saved in a table called Q table.

### Pseudocode

```python
def Q_learning():
	Q_table = new_qtable()
	replay_buffer = []
	random_step = 1
	for _ in range(episodes):
		s = state()
		while not s.finished():
			if random(0,1) > random_step:
				a = Q_table.get_max(s)
			else:
				a = Q_table.get_random(s)
			r, s1 = perform_action(a,s)
			D.append([s,a,r,s1.finished(),s1])
			mini_batch = get_random(D)
			for transition in mini_batc 
				if transition.T: # T indicates if the state is a terminal one
					R = r
				else:
					R = r + gamma * Q_table.get_max_reward(s1)
				Q_table.reward(s,a) += learning_rate(R - Q_table.reward(s,a)) 
			s = s1
		random_step -= decrease_value
```


## Deep Q-learning

The previous algorithm is very inefficient for large environments with a lot of actions and states, thus, impossible to use in most of the cases. A solution is to use deep learning in order to approximate more efficiently the Q_table. 
The loss function would be the difference between the expected outcome and the real one. 

To compute the value of the q table of a given state, we need to get the maximum possible outcome from that state. So, since to compute the loss function we also need the "real" maximum outcome of an action, we must use the network also to compute the outcome of the next state, then we can compute the loss and update the weights. But, doing so, not only the current value of the q table will be updated but also the value of the next state. This can bring instability to the training process. To fix this, we can copy the current weights of the net we are training in another identical network and use that to compute the q table value of the next state. The weights of the second network will be copied periodically from the first one.   