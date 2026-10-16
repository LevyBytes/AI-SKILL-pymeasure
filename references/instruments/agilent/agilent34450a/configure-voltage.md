# pymeasure.instruments.agilent.Agilent34450A.configure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

configure_voltage(*voltage_range='AUTO'*, *ac=False*, *resolution='DEF'*)

Prepare the instrument for voltage measurements.

Parameters:

- **voltage_range** – Voltage range to apply, in Volts. For DC, valid choices are 100E-3, 1, 10, 100, 1000, “MIN”, “MAX”, “DEF” (10 V), or “AUTO”. For AC, valid choices are 100E-3, 1, 10, 100, 750, “MIN”, “MAX”, “DEF” (10 V), or “AUTO”. (default: `'AUTO'`)

- **ac** – Use False for DC voltage and True for AC voltage (default: `False`)

- **resolution** – Requested resolution; valid choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), “MIN”, “MAX”, or “DEF” (1.50E-6). (default: `'DEF'`)
