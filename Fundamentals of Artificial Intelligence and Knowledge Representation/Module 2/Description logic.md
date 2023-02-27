A kind of [[Logic]] that focus on the description of terms.
Siymbols we can use:
- punctuation
- positive integers
- __ALL, EXISTS, FILL, AND__
- connectives ($\subset, \rightarrow, \dots$)
- Atomic concept (Person, Father, ...)
- Roles (height, age, ...)
- constants

Complex concepts can be expressed with concatenation of atomic concept:
- \[ALL r d\] all objects r-related of class d
- \[EXISTS n r\] objects r-related to at least n other individuals
- \[FILL r c\] objects r-related to the individual identified as c
- \[AND $d_1, \dots, d_n$\] anything described by $d_1, \dots, d_n$

## A box

Portion of knowledge containing notions about the individuals

### Reasoning on the A box 

W.r.t. S, can a constant c satitisfy d? In other words: S ⊨ (c → d)?
This can be computed using subsumption.

## T box

Portion of knowledge containing the terminology

### Reasoning on the ABox
- A concept _d_ is __satisfiable__ w.r.t. S if exists an interpreation of S such that I\[d\] is non-empty
- A concept _d_ is subsumed by a concept d’ w.r.t. S if I\[d\] ⊆ I\[d’\] for each interpretation
of S
- Equivalence: Two concepts d, d’ are equivalent w.r.t. S if I\[d\]=I\[d’\]
- Disjointness

# Extending DL

An arbitrary number of operators can be added, e.g.:
- \[AT-MOST n r\] individuals r-related to at most n individuals
- \[ONE-OF $c_1, \dots, c_n$ \] is a concept satisfied only by $c_i$ used in conjunction with ALL
- \[EXIST n r d\] individuals r-related to at least n individuals instances of d

If we add this kind of rules / operator, to denote our logic we must simply add the related letter to the name.