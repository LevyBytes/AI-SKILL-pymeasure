# pymeasure.instruments.hcp.TC038D.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*)

Send a command to the device.

Parameters:

**command** (*str*) - Comma separated string containing the function, read ('R'), write ('W'), or 'echo'; the address to write, for example '0x106' or '262'; the comma separated values to write; or the number of elements to read, defaulting to 1.
