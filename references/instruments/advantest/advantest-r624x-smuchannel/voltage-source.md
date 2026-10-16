# pymeasure.instruments.advantest.advantestR624X.SMUChannel.voltage_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

voltage_source(*source_range*, *source_value*, *current_compliance*)

For DC (constant voltage) measurement (`DV`), configure current compliance along with source range and source value.

Parameters:

- **source_range** (`VoltageRange`) – Specifying source range

- **source_value** (*float*) – Numeric source voltage setting

- **current_compliance** (*float*) – Numeric current compliance setting

Note

The instrument applies current compliance to both polarities (+ and -), regardless of the polarity supplied. It also selects the smallest current compliance range that can contain the configured value.
