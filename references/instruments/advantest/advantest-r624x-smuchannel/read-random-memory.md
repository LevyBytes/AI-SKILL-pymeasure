# pymeasure.instruments.advantest.advantestR624X.SMUChannel.read_random_memory

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_random_memory(*address*)

Read random sweep memory at a specified address (`RMS?`).

Parameters:

**address** (*int*) – Address identifying the memory location.

Returns:

Values set at the specified address location are returned by the device.

Return type:

str
