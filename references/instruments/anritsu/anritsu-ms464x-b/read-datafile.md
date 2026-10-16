# pymeasure.instruments.anritsu.AnritsuMS464xB.read_datafile

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_datafile(*channel*, *sweep_points*, *datafile_freq*, *datafile_par*, *filename*)

Read a data file from the VNA.

Parameters:

- **channel** (*int*) – Channel Index

- **sweep_points** (*int*) - integer number of sweep points

- **datafile_freq** (*DataFileFrequencyUnits*) – Data file frequency unit

- **datafile_par** (*DataFileParameter*) – Data file parameter format

- **filename** (*str*) - full path for the file to be saved
