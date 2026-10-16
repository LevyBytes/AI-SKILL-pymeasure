# pymeasure.instruments.teledyne.TeledyneOscilloscope.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*, ***kwargs*)

Send the command to the instrument using the adapter.

Note: when the preceding command was issued less than WRITE_INTERVAL_S ago, this method waits out the remaining interval so command frequency never exceeds 1/WRITE_INTERVAL_S Hz.

Parameters:

**command** – command string sent to the instrument
