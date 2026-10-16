# pymeasure.instruments.keithley.KeithleyDMM6500.measure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_current(*max_current=0.01*, *ac=False*)

Set up current measurement using a maximum current for range selection and a boolean choice for DC versus AC.

Parameters:

- **max_current** — Current value in Volts used to select the current range (default: `0.01`)

- **ac** — False selects DC current, and True selects AC current (default: `False`)
