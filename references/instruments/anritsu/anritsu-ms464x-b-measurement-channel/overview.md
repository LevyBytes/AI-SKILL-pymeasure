# pymeasure.instruments.anritsu.anritsuMS464xB.MeasurementChannel

*class *pymeasure.instruments.anritsu.anritsuMS464xB.MeasurementChannel(**args*, *frequency_range=None*, *traces=None*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Represents one channel of Anritsu MS464xB VNA.

Contains 4 `Port` instances (reachable through the ports dict or directly as pt_ + the port number) and up to 16 `Trace` instances (reachable through the traces dict or directly as tr_ + the trace number).

Parameters:

- **frequency_range** (*list** of **floats*) - specifies the number of installed ports (default=4). (default: `None`)

- **traces** (*int** (**1-16**) or **str** (**"auto"**) or **None*) - sets the assumed trace count for the channel (between 1 and 16); if omitted, the maximum number is assumed; with "auto", the instrument is queried for the trace count. (default: `None`)
