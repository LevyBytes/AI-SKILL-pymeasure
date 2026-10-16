# pymeasure.instruments.agilent.agilentB1500.SMU.ramp_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

ramp_source(*source_type*, *source_range*, *target_output*, *comp=''*, *comp_polarity=''*, *comp_range=''*, *stepsize=0.001*, *pause=0.02*)

Move from the configured value to a target output using the supplied step size.

A pause interval is inserted between successive steps.

Parameters:

- **source_type** (*str*) – Selected source type (`'Voltage'` or `'Current'`)

- **source_range** (*int** or **str*) – Output range index or range name

- **target_output** (*float*) – Target voltage or current at the output

- **comp** (*float*) – Compliance; defaults to the previous setting

- **comp_polarity** (*CompliancePolarity*) – Compliance polarity; defaults to auto

- **comp_range** (*int** or **str*) – Compliance range selection; defaults to auto

- **stepsize** (*float*) – Largest permitted step size

- **pause** (*float*) – Wait time in seconds between steps

## Related property contracts

- Open when checking pymeasure.instruments.agilent.agilentB1500.SMU.meas_range_current: [meas_range_current](meas-range-current.md).
- Open when checking pymeasure.instruments.agilent.agilentB1500.SMU.meas_range_voltage: [meas_range_voltage](meas-range-voltage.md).
