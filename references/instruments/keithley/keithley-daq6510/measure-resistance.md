# pymeasure.instruments.keithley.KeithleyDAQ6510.measure_resistance

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_resistance(*nplc=1*, *resistance=100000000.0*, *auto_range=True*)

Configure the measurement of resistance.

Parameters:

- **nplc** – Power line cycle count (NPLC); accepted settings start at 5E-4 and top out at 15 for 60 Hz or 12 for 50 Hz or 400 Hz. (default: `1`)

- **resistance** – Resistance upper limit in Ohms: 10 through 100E6 for 2-wire, 1 through 100E6 for 4-wire with OCOM off, or 1 through 10E3 for 4-wire with OCOM on. (default: `100000000.0`)

- **auto_range** – Boolean that enables auto_range when `True`; otherwise the configured resistance is used. (default: `True`)
