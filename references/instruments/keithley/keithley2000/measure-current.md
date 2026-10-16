# pymeasure.instruments.keithley.Keithley2000.measure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_current(*max_current=0.01*, *ac=False*)

Set up current measurement, using the maximum current to choose range and the boolean flag to select DC or AC.

Parameters:

- **max_current** — Current in Volts used to set the current range (default: `0.01`)

- **ac** — False selects DC current, True selects AC current (default: `False`)
