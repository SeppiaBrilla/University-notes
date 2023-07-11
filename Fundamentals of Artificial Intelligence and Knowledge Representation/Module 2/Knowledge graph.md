A graph that stores information in nodes and link them via arcs. It does not use any [[Fundamentals of Artificial Intelligence and Knowledge Representation/Module 2/Logic|logical]] formula (looks a bit like [[Semantic networks]]).
We can evaluate it by checking the coverage, the correctness of the information and freshness of the informations. It is used in semantic web.

## Graph Embedding
Triplettes in the shape of (h,r,t): head, tail and relation. A KG is a set S={(h,r,t)}
We can represent entities and relation into a vectorial space.
Then we can both:
- try to learn the relation function: input (h,t) and rh and t ⇒ output a ANN able to predict r given
- try to predict some entity: input (h,r) and t r ⇒ output a ANN able to predict t, given h and

We have to choose a representation space, a scoring function and learn a representation
function.