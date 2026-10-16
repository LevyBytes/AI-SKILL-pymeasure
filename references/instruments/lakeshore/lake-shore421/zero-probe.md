# pymeasure.instruments.lakeshore.LakeShore421.zero_probe

[Owning PyMeasure class, adapter and connection contract](overview.md)

zero_probe(*wait=True*)

Resets the probe value to 0. Normally this is done with a zero gauss chamber, but an open probe can also be used to cancel the Earth magnetic field. Use relative mode instead when cancelling larger magnetic fields.

Parameters:

**wait** (*bool*) - after issuing the command, wait for 20 seconds so the reset can finish.
