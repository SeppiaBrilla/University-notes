It's a better approach to [[SAT]] resolution.
Ideally, we would like to inspect a clause only when all but one literal have been assigned. In a real world scenario, this is impossible, but we can use an approximate approach:
- watch two unassigned literals in every clause in preparation of unit propagation.
- Examine the clause only when one of them is assigned 𝐹.
- For each literal, maintain a watch list containing the clauses it is currently watched by.