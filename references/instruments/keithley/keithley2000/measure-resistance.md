# pymeasure.instruments.keithley.Keithley2000.measure_resistance

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_resistance(*max_resistance=10000000.0*, *wires=2*)

Set up resistance measurement, using the maximum resistance for range selection and the chosen wire count.

Parameters:

- **max_resistance**: Resistance in ohms used to set the resistance range (default: `10000000.0`)

- **wires**: Number of wires employed, either 2 or 4 (default: `2`)
