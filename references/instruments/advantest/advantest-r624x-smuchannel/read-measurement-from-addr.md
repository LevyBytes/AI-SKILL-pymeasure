# pymeasure.instruments.advantest.advantestR624X.SMUChannel.read_measurement_from_addr

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_measurement_from_addr(*addr*)

Return one measurement from this channel's measurement data buffer at the specified memory address (`RMM?`).

Parameters:

**addr** (*int*) – Address to read.

Returns:

float Measurement data

Note

See `AdvantestR624X.output_format()` for the output format. Reading a memory address with no stored measurement data returns 999.999E+99.
