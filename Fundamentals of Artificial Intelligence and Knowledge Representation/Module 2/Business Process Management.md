It helps with business decisions.
There are different possible business prospective.

### High level prospectives

- Organizational (describe I/O, expected outcomes and dependecies) vs operational (activities are specified, implementation is disregarded)
- Intra (all activities are executed within the business boundaries) vs Iner organization (part of the activities executed somewhere else)

## Activity model and instances

An activity instance is the work conduced during the execution of the business instances. Events in an instance are temporarily ordered. An activity model is a set of similar instances.

Process modelling can be divided in 3 key components:
- __Control flow__ that describes the process and order the activities in it. It can be _procedural_ (order of the steps) or _declarative_ (focus on the properties that should hold during the execution) also _open_ (specifies allowed and forbidden activities) or _closed_ (activities get executed only if the process specifies so)
- __Data__ produced and analyzed by the instances
- __Resources__ and structure that enable the execution of the BPs

## Control flow pattern

The control flow is described by:
- __Sequence__: state of the ordering activities
- __And/parallel split__: the activities are split in multiple ones executed concurrently
- __And/parallel join__: multiple, concurrent, activities are joined in one
- __Xor split/and xor join__: only one of the several branches is chosen when splitting
- __or join__: same as and join, but we don't necessarily need to wait all activities to be completed in order to proceed
- __multiple merge__: multiple threads of control join without synchronization
- __discriminator__: waits for one of the incoming branches to complete and trigger the
   subsequent activity (then wait for the other branches and ignore them)
- __n out of m__: wait for N out of M (n≤m) branches to be completed (and ignore the
   remaining)
-  __arbitrary circles__: introduce loop using xor split/join
- __multiple instances__: concatenation of several instances
   