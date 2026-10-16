# pymeasure.instruments.keithley.keithley2182.Keithley2182Channel.setup_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

setup_voltage(*auto_range=True*, *nplc=5*)

Select the active channel and set that channel up for voltage measurement.

Parameters:

- **auto_range** – If True, enables auto_range; otherwise uses the set voltage range. (default: `True`)

- **nplc** – NPLC setting, expressed in power line cycles, allowed from 0.01 to 50/60. (default: `5`)
