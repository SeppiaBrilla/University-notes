It is a [[Deductive planning]] technique that aims at resolving a [[Planning]] problem as a [[First order logic]] deduction. The main difference with [[Situation calculus]] is that uses a green-like formulation to describe the word.

## Event calculus keywords
- __HoldsAt(F, T)__: the fluet F is true at time T
- __Happens(E, T)__: the event E (e.g. execution of an action, ...) happens at time T
- __Initiates( E, F, T)__: event E causes fluent F to hold at time T (used in domain-dependent axioms…) 
- __Terminates( E, F, T)__: event E causes fluent F to cease to hold at time T (used in domain-dependent axioms…) 
- __Clipped( T1, F, T )__: Fluent F has been made false between T1 and T(used in domain-independent axioms), T1< T 
- __Initially( F )__ : fluent F holds at time 0
- __Initially(F)__: the fluent F holds at the beginning 
- __Initiates(Ev, F, T)__: the happening of event Ev at time T makes F to hold; it can be extended with many (pre-)conditions 
- __Terminates(Ev, F, T)__: the happening of event Ev at time T makes F to not hold anymore.


# Allen's logic

Often, reason on instants is not good enough because, most of the things take time to happend. The allen's Logic introduce the notion of intervals. Intervals have a beginning nad and end (Begin(i), Ends(k)).
To reason on intervals those axioms are necessary:
- __Meet(i,j)__ ⇔ End(i) = Begin(j) 
- __Before(i, j)__ ⇔ End(i) < Begin(j)
- __After(j, i)__ ⇔ Before(i, j) 
- __During (i, j)__ ⇔ Begin(j) < Begin(i) < End(i) < End(j)
- __Overlap(i, j)__ ⇔Begin(i) < Begin(j) < End(i) < End(j) 
- __Starts(i, j)__ ⇔ Begin(i) = Begin(j) 
- __Finishes(i, j)__ ⇔ End(i) = End(j) 
- __Equals(i, j)__ ⇔ Begin(i) = Begin(j) AND End(i) = End(j)