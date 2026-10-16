# pymeasure.instruments.keithley.KeithleyDAQ6510.measure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_voltage(*nplc=1*, *voltage=1000*, *auto_range=True*)

Configure the measurement of voltage.

Parameters:

- **nplc** – Power line cycle count (NPLC); accepted settings start at 5E-4 and top out at 15 for 60 Hz or 12 for 50 Hz or 400 Hz. (default: `1`)

- **voltage** – Voltage upper limit in Volts: 100E-3 through 1000 V for DC, or 100E-3 through 750 V for AC. (default: `1000`)

- **auto_range** – Boolean that enables auto_range when `True`; otherwise the configured voltage is used. (default: `True`)
