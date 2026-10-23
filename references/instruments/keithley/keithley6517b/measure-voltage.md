# pymeasure.instruments.keithley.Keithley6517B.measure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_voltage(*nplc=1*, *voltage=21.0*, *auto_range=True*)

Configures the measurement of voltage.

Parameters:

- **nplc**: Power line cycle count (NPLC), from 0.01 to 10. (default: `1`)

- **voltage**: Upper voltage bound in Volts, from -1000 V to 1000 V. (default: `21.0`)

- **auto_range**: Enables auto_range when True; otherwise the voltage_range attribute is used. (default: `True`)
