# pymeasure.instruments.agilent.agilentB1500.QueryLearn.query_learn_header

[Owning PyMeasure class, adapter and connection contract](overview.md)

*classmethod *query_learn_header(*ask*, *query_type*, *smu_references*, *single_command=False*)

Send `*LRN?` (learn) to the instrument to read configuration, then convert the information into human-readable values for debugging or file headers.

Parameters:

- **ask** (*Instrument.ask*) - instrument ask method

- **query_type** (*int** or **str*) - Programming Guide number

- **smu_references** (*dict*) - SMU references keyed by channel

- **single_command** (*str*) - return only one command when requested; defaults to False

Returns:

Read configuration

Return type:

dict
