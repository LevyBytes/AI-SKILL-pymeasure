# pymeasure.instruments.agilent.agilentB1500.AgilentB1500.data_format

[Owning PyMeasure class, adapter and connection contract](overview.md)

data_format(*output_format*, *mode=0*)

Choose the data output format; see parameter documentation. (`FMT`)

Call this once during a session so later measurement values read from the instrument can be parsed with the selected data format.

Currently implemented are format 1, 11, and 21.

Parameters:

- **output_format** (*str*) – Output format string, e.g. `FMT21`

- **mode** (*int*) – Data output mode; defaults to 0, returning only measurement data

## Related property contracts

- Open when checking pymeasure.instruments.agilent.agilentB1500.AgilentB1500.parallel_meas: [parallel_meas](parallel-meas.md).
