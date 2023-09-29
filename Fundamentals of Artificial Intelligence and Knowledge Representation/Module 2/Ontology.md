An Ontology is a formal, explicit description of a domain of interest.
__Definitions__:
- _formal_: described using a language with a clear, non ambiguous semantic
- _explicit_: the information should be available or derivable in a finite time
- _description_: it should provide information
- _domain_: such information should be related to some topic of interest.

# Categories and objects

Categories are groups with common characteristics. They can be very specific (e.g. people taller than 1.93 cm with brown long hairs that wear blue shoes on Saturday morning) or very general (e.g. people). Categories can also be organised hierarchically.
Objects are instance of categories. Some objects can belong to more than one category.

## Upper ontologies 

Are ontologies that focus on largest domain, and they correspond, more or less, with larger categories.

### Special purpose and general purpose ontologies

Special purpose ontologies can always be generaliseed into general purpose ones.
Also, general purpose / upper ontologies must have, at least, those two characteristics:
- they must be applicable to (almost) any special domain
- we should be able to combine different ontologies without having inconsistencies.

## Representation

In [[Proposition logic]] or [[First order logic]], we can use unique names to represent objects. But for categories it is more complicate and there are two ways to represent them: 
- __as predicates__: e.g. Car(abc123) means that the vehicle with plate abc123 is a car. Where "Car" is a category.
- __Through reification__: e.g. Member(abc123, Car) or abc123 $\in$ Car

## Properties

- __Membership__: abc123 $\in$ Car
- __Subclass__: Car $\subset$ Vehicle
- __Disjointness__: $\forall c_1,c_2 \; c_1 \in s \wedge c_2 \in s \wedge c_1 \neq c_2 \Rightarrow c_1 \cap c_2 = \emptyset$
- __Exhaustive decomposition__: $\forall i \in c \Leftrightarrow \exists c_2 \; c_2 \in s \wedge i \in c_2$
- __Partition__: disjoint + exhaustive decomposition

## Physical composition

Objects can be made of two or more objects. The relation between an object and its parts is called __meronymy__, the opposite is called __holonym__.

If there is a structural relationship of the sub-objects with the full one, we can describe it with the property __PartOf()__. The part of relationship is transitive and reflexive.

If there is no structural relationship of the sub-objects with the full one, we can describe it with the property __BunchOf()__. 

## Measures

Measures can be quantitative or qualitative.

## Thing or stuff

We use the word "_thing_" when we have an intrinsic property and "_stuff_" when we have an extrinsic property.
- __Intrinsic__: properties referred to the substance of the object
- __Extrinsic__: properties refered to the object, and to the object structure relation with its parts