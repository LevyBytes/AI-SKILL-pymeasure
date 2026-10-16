# Main Classes

Instrument communication classes:

- `AgilentB1500`: Main instrument class

- `SMU`: Created by the main instrument class for each SMU

- `SPGU`: Created by the main instrument class for each SPGU

- `SPGUChannel`: Created by SPGU for every channel

- `CMU`: Created by the main instrument class for CMU

Query commands produce settings as human-readable dict objects. Use them for debugging, logging, or file headers rather than as inputs for paired setting commands.
