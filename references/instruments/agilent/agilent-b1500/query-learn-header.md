# pymeasure.instruments.agilent.agilentB1500.AgilentB1500.query_learn_header

[Owning PyMeasure class, adapter and connection contract](overview.md)

query_learn_header(*query_type*, ***kwargs*)

Fetch instrument settings. (`*LRN?`)

Return a human-readable settings dict suitable for debugging output or file headers. Optional arguments follow the underlying `QueryLearn.query_learn_header()` definition.

Parameters:

**query_type** (*int** or **str*) – Query category, using the manual's numeric code

Return type:

dict
