# pymeasure.instruments.agilent.Agilent34450A.configure_frequency

[Owning PyMeasure class, adapter and connection contract](overview.md)

configure_frequency(*measured_from='voltage_ac'*, *measured_from_range='AUTO'*, *aperture='DEF'*)

Prepare the instrument for frequency measurements.

Parameters:

- **measured_from** – Select “voltage_ac” or “current_ac” (default: `'voltage_ac'`)

- **measured_from_range** – Range applied to measured_from. AC voltage ranges are 100E-3, 1, 10, 100, 750, plus “MIN”, “MAX”, “DEF” (10 V), or “AUTO”. AC current ranges are 10E-3, 100E-3, 1, 10, plus “MIN”, “MAX”, “DEF” (100 mA), or “AUTO”. (default: `'AUTO'`)

- **aperture** – Aperture time in Seconds; accepted choices are 100 ms, 1 s, “MIN”, “MAX”, or “DEF” (1 s). (default: `'DEF'`)
