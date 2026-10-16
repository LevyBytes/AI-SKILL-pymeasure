# pymeasure.instruments.agilent.agilentE5270B.Display.engineering_format_enabled

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *engineering_format_enabled*: Any*

Select engineering data format versus scientific data format (bool).

Example:

- `True` (engineering): +123.456mA

- `False` (scientific): +1.234E-1A

Note

Calling [`reset()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.reset) changes the data format to scientific.
