# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.query_analog_pulse_width_trigger

[Owning MixedSignalOscilloscope contract](overview.md)

query_analog_pulse_width_trigger(*trigger_instance*)

Reports analog pulse width trigger configuration for the specified instance.

Returns:

Trigger source, trigger polarity, trigger level, comparison mode, lower limit, upper limit

Return type:

(str, enum, float, enum, float, float)
