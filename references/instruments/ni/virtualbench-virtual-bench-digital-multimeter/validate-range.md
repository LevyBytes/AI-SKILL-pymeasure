# pymeasure.instruments.ni.virtualbench.VirtualBench.DigitalMultimeter.validate_range

[Owning DigitalMultimeter contract](overview.md)

*static *validate_range(*dmm_function*, *range*)

Validates `range` against the selected `dmm_function`

Parameters:

- **dmm_function** (*int*) – DMM Function

- **range** (*int** or **float*): Range value, for example the maximum measurable value

Returns:

Range value supplied to instrument

Return type:

int
