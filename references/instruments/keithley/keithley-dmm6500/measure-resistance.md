# pymeasure.instruments.keithley.KeithleyDMM6500.measure_resistance

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_resistance(*max_resistance=10000000.0*, *wires=2*)

Set up resistance measurement using the maximum resistance to choose the range.

Parameters:

- **max_resistance** (*float*) — Resistance in Ohms used to select the resistance range (default: `10000000.0`)

- **wires** (*int*) — `2` selects normal resistance, and `4` selects 4-wires resistance (default: `2`)

Returns:

None
