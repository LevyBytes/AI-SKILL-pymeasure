# pymeasure.instruments.ni.virtualbench.VirtualBench.PowerSupply.tracking

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *tracking

Turns tracking between the positive and negative 25V channels on or off. When tracking is enabled, configuration changes on the positive 25V channel are mirrored to the negative 25V channel, while writes to the negative 25V channel are ignored.

Parameters:

**enable_tracking** (*bool*) – Enable/Disable tracking
