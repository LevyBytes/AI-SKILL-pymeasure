# pymeasure.instruments.agilent.agilentB1500.SMU.force

[Owning PyMeasure class, adapter and connection contract](overview.md)

force(*source_type*, *source_range*, *output*, *comp=''*, *comp_polarity=''*, *comp_range=''*)

Immediately source DC current or voltage from the SMU. (`DI`, `DV`)

Parameters:

- **source_type** (*str*) – Source type (`'Voltage','Current'`)

- **source_range** (*int** or **str*) – Output range index or range name

- **output** (*float*) – Value sourced at the output in A or V

- **comp** (*float*) – Compliance value; defaults to the previous setting

- **comp_polarity** (*CompliancePolarity*) – Compliance polarity; defaults to auto

- **comp_range** (*int** or **str*) – Compliance range selection; defaults to auto
