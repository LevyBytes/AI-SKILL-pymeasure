# pymeasure.instruments.keithley.Keithley6517B.measure_resistance

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_resistance(*nplc=1*, *resistance=210000.0*, *auto_range=True*)

Configures the measurement of resistance.

Parameters:

- **nplc**: Power line cycle count (NPLC), from 0.01 to 10. (default: `1`)

- **resistance**: Upper resistance bound in Ohms, from -210 POhms to 210 POhms. (default: `210000.0`)

- **auto_range**: Enables auto_range when True; otherwise the resistance_range attribute is used. (default: `True`)
