# pymeasure.instruments.lecroy.LeCroyT3DSO1204.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*, ***kwargs*)

Send the command to the instrument via the adapter.

Note: if the previous command was issued less than WRITE_INTERVAL_S ago, this method waits for the remaining time, ensuring commands are not sent faster than 1/WRITE_INTERVAL_S Hz.

Parameters:

**command** - command string sent to the instrument
