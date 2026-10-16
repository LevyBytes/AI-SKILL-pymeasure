# pymeasure.instruments.agilent.agilentB1500.QueryLearn.to_dict

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *to_dict(*parameters*, *names*, **args*)

Build a dict of named parameters from values returned by `query_learn()` plus an ordered list of matching parameter names and an optional function.

Parameters:

- **parameters** (*dict*) - Parameters for a single command returned by `query_learn()`

- **names** (*list*) - ordered names list, or ordered (name, function) tuples

Returns:

Parameter name and (processed) parameter

Return type:

dict
