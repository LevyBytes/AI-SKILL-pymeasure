# pymeasure.instruments.keithley.Keithley2000.measure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_voltage(*max_voltage=1*, *ac=False*)

Set up voltage measurement, using the maximum voltage for range selection and the boolean flag to select DC or AC.

Parameters:

- **max_voltage** — Voltage in Volts used to set the voltage range (default: `1`)

- **ac** — False selects DC voltage, True selects AC voltage (default: `False`)
