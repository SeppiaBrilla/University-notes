It is a paradigm made for dealing with big data. Information are described using a language, temporal information and a duration for the events.
We can distinguish between __simple__ and __complex__ events: they are represented in the same way but, the second one, allows for a better answer to a business question. The CEP is built to reason upon simple events in order to derive more complex ones. 
[[Rule-based systems|Drools]] has a "_Fusion_" version that implements CEP: events are facts with a timestamp attached and [[Event calculus|Allen logic]] can be used to reason on them. 

## Reasoning about the state of the system
CEP allow reasoning about events. In order to reason about the state of a system, we need to use Event Calculus Framework.