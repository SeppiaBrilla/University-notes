Reinforcement Learning is about learning behaviors: taking actions and decisions in an automatic way in response to a mutable external environment.
At each given moment, we want to decide what is the best action to do in order to maximize not the instant but the cumulative reward.

__Markov's property__: Current state completely characterizes the state of the world: future actions only depend on the current state.
The current state is defined by a tuple $(S,A,R,P,\gamma)$:
- $S$: set of possible states
- $A$: set of possible actions
- $R$: reward probability given
- $P$: transition probability to next state given (state, action) pair
- $\gamma$: discount factor

We want to model a policy that maximize the probability of getting a big reward.

## Model free and model based models

The transition from a state to another is not always determinstic, but governed by some probability. If the model need to learn that probability, it is called model based.
If the probability is left implicit and the model base its action only on past outcomes, it ls a model free model.

Example of model based: [[A*]]


## Model free approach

Reinforcement learning requires acquisition of experience interacting with the environment.
All techniques have to deal with the exploration/exploitation trade-off.

__Exploration__ is finding more information about the environment, usually requiring randomization.

__Exploitation__ is taking advantage of the available information to direct and possibly improve the exploration.

There are two main techniques:
 - [[Value based]]: We try to evaluate each state s with a value function.
 - Policy based: we directly try to improve the current policy, hopefully optimizing it.