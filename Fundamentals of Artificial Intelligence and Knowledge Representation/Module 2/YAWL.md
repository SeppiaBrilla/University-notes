YAWL (Yet Another Workflow Language) is a language based on [[Workflow nets]].
They have arcs that connect transitions, cancellation region defined, tokens on
transations for the activity instance duration and tasks that can generate multiple instances.

We have several symbols: xor split/join, and split/join, or split/join. And 2 special symbol
indicating the start and the end of a process instance. Task and activities are represented via blocks indicating: atomic tasks, multiple instance atomic tasks, condition and composite (and multiple instance composite) tasks