# pymeasure.instruments.advantest.advantestR624X.SMUChannel.current_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

current_source(*source_range*, *source_value*, *voltage_compliance*)

For DC (constant current) measurement (`DI`), configure voltage compliance along with source range and source value.

Parameters:

- **source_range** (`CurrentRange`) – Specifying source range

- **source_value** (*float*) – Numeric source current setting

- **voltage_compliance** (*float*) – Numeric voltage compliance setting

Note

Voltage compliance is set for both polarities (+ and -), regardless of the polarity supplied. The instrument chooses the smallest voltage compliance range that contains the configured value.
