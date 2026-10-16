# pymeasure.instruments.agilent.agilent4156.Agilent4156.data_variables

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *data_variables

Return a string list containing data variables with available measured data.

Searches for variables stored by `save()` and `save_var()` and returns them. Useful when building dataframe headers.

Returns:

List

```python
header = instr.data_variables

```
