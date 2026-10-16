# pymeasure.instruments.agilent.agilentN8975A.AgilentN8975AFrequency.mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *mode*: Any*

Sets how measurement frequencies are generated (str, strictly `sweep`, `fixed` or `list`).

- `sweep`: frequency values come from the `start`, `stop` and `number_of_points` parameters

- `fixed`: uses the `fixed_value` frequency

- `list`: takes frequencies from `list_data`
