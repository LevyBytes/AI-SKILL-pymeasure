# pymeasure.instruments.agilent.agilentB1500.QueryLearn.query_learn

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *query_learn(*ask*, *query_type*)

Send `*LRN?` (learn) to the instrument to read configuration, returning a dictionary of commands with set values.

Parameters:

**query_type** (*int*) - Query type as defined by the programming guide

Returns:

Dictionary containing commands and set values

Return type:

dict
