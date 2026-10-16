# pymeasure.instruments.advantest.advantestR624X.SMUChannel.output_all_measurements

[Owning PyMeasure class, adapter and connection contract](overview.md)

output_all_measurements()

Return every measurement stored in this channel's measurement data buffer (`RMM?`).

Note

See `AdvantestR624X.output_format()` for the output format. Reading a memory address with no stored measurement data returns 999.999E+99.
