# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope

[Owning PyMeasure class, adapter and connection contract](../virtualbench-virtual-bench/overview.md)

*class *MixedSignalOscilloscope(*virtualbench*, *reset*, *vb_name=''*)

Bases: `VirtualBenchInstrument`

Models the Virtual Bench device Mixed Signal Oscilloscope (MSO) Module. It measures oscilloscope data from analog and digital channels.

pyvirtualbench methods not yet implemented in pymeasure:
- `enable_digital_channels`

- `configure_digital_threshold`

- `configure_advanced_digital_timing`

- `configure_state_mode`

- `configure_digital_edge_trigger`

- `configure_digital_pattern_trigger`

- `configure_digital_glitch_trigger`

- `configure_digital_pulse_width_trigger`

- `query_digital_channel`

- `query_enabled_digital_channels`

- `query_digital_threshold`

- `query_advanced_digital_timing`

- `query_state_mode`

- `query_digital_edge_trigger`

- `query_digital_pattern_trigger`

- `query_digital_glitch_trigger`

- `query_digital_pulse_width_trigger`

- `read_digital_u64`
