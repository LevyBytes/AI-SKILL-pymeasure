# pymeasure.instruments.agilent.agilentB1500.Ranging

*class *pymeasure.instruments.agilent.agilentB1500.Ranging(*supported_ranges*, *ranges*, *fixed_ranges=False*)

Bases: `object`

Possible output and measurement range settings for SMU current/voltage.

Converts available voltage/current range names to indices and back.

Parameters:

- **supported_ranges** (*list*) - Supported ranges, represented as a list of range indices

- **ranges** (*dict*) - Complete range-name mapping `{Name: Indices}`

- **fixed_ranges** (*bool*) - Include fixed ranges (negative indices); defaults to False
