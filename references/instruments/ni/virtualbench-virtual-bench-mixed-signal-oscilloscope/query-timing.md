# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.query_timing

[Owning MixedSignalOscilloscope contract](overview.md)

query_timing()

Reports the MSO timing configuration. Call it right before measurement to capture the actual timing configuration and store it in the matching class variables; this is needed to interpret measurement data because no time information is included.

Returns:

Sample rate, acquisition time, pretrigger time, sampling mode

Return type:

(float, float, float, enum)
