# pymeasure.instruments.agilent.Agilent34450A.configure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

configure_current(*current_range='AUTO'*, *ac=False*, *resolution='DEF'*)

Prepare the instrument for current measurements.

Parameters:

- **current_range** – Current range to apply, in Amps. For DC, valid choices are 100E-6, 1E-3, 10E-3, 100E-3, 1, 10, “MIN”, “MAX”, “DEF” (100 mA), or “AUTO”. For AC, valid choices are 10E-3, 100E-3, 1, 10, “MIN”, “MAX”, “DEF” (100 mA), or “AUTO”. (default: `'AUTO'`)

- **ac** – Use False for DC current and True for AC current (default: `False`)

- **resolution** – Requested resolution; valid choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), “MIN”, “MAX”, or “DEF” (1.50E-6). (default: `'DEF'`)
