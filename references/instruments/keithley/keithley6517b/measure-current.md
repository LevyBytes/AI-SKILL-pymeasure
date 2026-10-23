# pymeasure.instruments.keithley.Keithley6517B.measure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_current(*nplc=1*, *current=0.000105*, *auto_range=True*)

Configures the measurement of current.

Parameters:

- **nplc**: Power line cycle count (NPLC), from 0.01 to 10. (default: `1`)

- **current**: Upper current bound in Amps, from -21 mA to 21 mA. (default: `0.000105`)

- **auto_range**: Enables auto_range when True; otherwise the current_range attribute is used. (default: `True`)
