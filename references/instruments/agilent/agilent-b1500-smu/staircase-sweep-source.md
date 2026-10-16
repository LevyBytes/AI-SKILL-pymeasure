# pymeasure.instruments.agilent.agilentB1500.SMU.staircase_sweep_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

staircase_sweep_source(*source_type*, *mode*, *source_range*, *start*, *stop*, *steps*, *comp*, *Pcomp=''*)

Configure staircase sweep source parameters. (`WV` or `WI`)

Parameters:

- **source_type** (*str*) – Source type (`'Voltage', 'Current'`)

- **mode** (*SweepMode*) – Sweep mode

- **source_range** (*int*) – Source range index

- **start** (*float*) – Sweep start value

- **stop** (*float*) – Sweep stop value

- **steps** (*int*) – Sweep step count

- **comp** (*float*) – Compliance value

- **Pcomp** (*float*) – Power compliance; defaults to not set
