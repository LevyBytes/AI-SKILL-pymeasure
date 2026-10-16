# pymeasure.instruments.keithley.KeithleyDAQ6510.measure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_current(*nplc=1*, *current=3*, *auto_range=True*)

Configure the measurement of current.

Parameters:

- **nplc** – Power line cycle count (NPLC); accepted settings start at 5E-4 and top out at 15 for 60 Hz or 12 for 50 Hz or 400 Hz. (default: `1`)

- **current** – Current upper limit in Amps: 10E-6 through 3 A for DC, or 100E-6 through 3A for AC. (default: `3`)

- **auto_range** – Boolean that enables auto_range when `True`; otherwise the configured current is used. (default: `True`)
