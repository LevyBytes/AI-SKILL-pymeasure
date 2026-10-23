# pymeasure.instruments.keithley.KeithleyDMM6500.measure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_voltage(*max_voltage=1*, *ac=False*)

Set up voltage measurement using a maximum voltage for range selection and a boolean choice for DC versus AC.

Parameters:

- **max_voltage**: Voltage in Volts used to select the voltage range (default: `1`)

- **ac**: False selects DC voltage, and True selects AC voltage (default: `False`)
