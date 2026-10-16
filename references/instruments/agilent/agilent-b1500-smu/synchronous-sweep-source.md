# pymeasure.instruments.agilent.agilentB1500.SMU.synchronous_sweep_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

synchronous_sweep_source(*source_type*, *source_range*, *start*, *stop*, *comp*, *Pcomp=''*)

Configure the synchronous staircase sweep source, current or voltage, and its parameters. (`WSV` or `WSI`)

Parameters:

- **source_type** (*str*) – Source type (`'Voltage','Current'`)

- **source_range** (*int*) – Source range index

- **start** (*float*) – Sweep start value

- **stop** (*float*) – Sweep stop value

- **comp** (*float*) – Compliance value

- **Pcomp** (*float*) – Power compliance; defaults to not set
