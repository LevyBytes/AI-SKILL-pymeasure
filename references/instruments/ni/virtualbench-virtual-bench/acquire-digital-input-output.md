# pymeasure.instruments.ni.virtualbench.VirtualBench.acquire_digital_input_output

[Owning PyMeasure class, adapter and connection contract](overview.md)

acquire_digital_input_output(*lines*, *reset=False*)

Opens communication with the DIO module. Call this once per session.

Parameters:

- **lines** (*str*): Lines to acquire; all lines can be read

- **reset** (*bool**, **optional*): Whether to reset DIO module, defaults to False (default: `False`)
