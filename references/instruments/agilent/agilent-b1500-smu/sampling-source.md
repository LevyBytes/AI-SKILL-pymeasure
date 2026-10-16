# pymeasure.instruments.agilent.agilentB1500.SMU.sampling_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

sampling_source(*source_type*, *source_range*, *base*, *bias*, *comp*)

Configure the DC current or voltage source used for sampling measurement. (`MV` or `MI`)

`force()` commands on this channel replace the sampling source setting.

Parameters:

- **source_type** (*str*) – Source type (`'Voltage','Current'`)

- **source_range** (*int*) – Source range index

- **base** (*float*) – Base voltage/current

- **bias** (*float*) – Bias voltage/current

- **comp** (*float*) – Compliance value
