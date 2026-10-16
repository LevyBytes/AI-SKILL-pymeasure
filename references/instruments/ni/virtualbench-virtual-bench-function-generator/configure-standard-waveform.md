# pymeasure.instruments.ni.virtualbench.VirtualBench.FunctionGenerator.configure_standard_waveform

[Owning FunctionGenerator contract](overview.md)

configure_standard_waveform(*waveform_function*, *amplitude*, *dc_offset*, *frequency*, *duty_cycle*)

Sets a standard waveform output on the instrument. Refer to the instrument manual for load-dependent maximum ratings.

Parameters:

- **waveform_function** (*int** or **str*) — Waveform function choice (`"SINE", "SQUARE", "TRIANGLE/RAMP", "DC"`)

- **amplitude** (*float*) – Amplitude in volts

- **dc_offset** (*float*) — DC offset value in volts

- **frequency** (*float*) – Frequency in Hz

- **duty_cycle** (*int*) — Duty cycle expressed in %

## Related property contracts

- Open when checking pymeasure.instruments.ni.virtualbench.VirtualBench.FunctionGenerator.filter: [filter](filter.md).
