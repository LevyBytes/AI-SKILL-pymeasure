# pymeasure.instruments.agilent.Agilent34450A.configure_resistance

[Owning PyMeasure class, adapter and connection contract](overview.md)

configure_resistance(*resistance_range='AUTO'*, *wires=2*, *resolution='DEF'*)

Prepare the instrument for resistance measurements.

Parameters:

- **resistance_range** – Resistance range to apply, in Ohms: 100, 1E3, 10E3, 100E3, 1E6, 10E6, 100E6, “MIN”, “MAX”, “DEF” (1E3), or “AUTO”. (default: `'AUTO'`)

- **wires** – Wire count for the measurement, either 2 or 4. (default: `2`)

- **resolution** – Requested resolution; valid choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), “MIN”, “MAX”, or “DEF” (1.50E-6). (default: `'DEF'`)
