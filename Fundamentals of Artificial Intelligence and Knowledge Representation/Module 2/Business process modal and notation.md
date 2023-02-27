BPMN is a model and notation to represent the logical behind [[Business Process Management]].
Like flowcharts but with more metamodel rules, event-trigger descriptions and a way to capture collaborations. It uses [[Logic]] in ordert to forecast what to do next.
Problems: no method on how to make a good model and no styling guide, useful in order to
disambiguate models, have a complete model, understanding similarity and dissimilarity
between models.
We have several Graphical elements(organized in families) such as flow objects, data,
connecting objects and other elements, swimlanes that organize grouping of modelling
elements, artifacts that have additional info.
We have different modelling levels: descriptive process modelling (traditional flowchart),
analytic process modelling (expansion of previous with reactive behaviours and exception
handling), executable BPMN (enable process execution)
In BPM an activity is a unit of work performed in the process by a performer. Each activity is
either a task (atomi unit of work labelled using a verb-noun form) or a subprocess (compound unit of work, new child BPMN process).
BPMN includes gateway of two types: split (one control flow splits into many) and join
(viceversa). It also include xor split/join, and gateway, a start and an end event.