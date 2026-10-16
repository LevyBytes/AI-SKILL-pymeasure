# pymeasure.instruments.teledyne.TeledyneMAUI

*class *pymeasure.instruments.teledyne.TeledyneMAUI(*adapter*, *name='Teledyne Oscilloscope'*, ***kwargs*)

Bases: `TeledyneOscilloscope`

Base class for MAUI-style Teledyne oscilloscopes.

This base class is usable immediately. Some attributes, especially channel count, may need adjustment for the connected instrument.

The API is documented in “MAUI Oscilloscopes Remote Control and Automation Manual” ([link](https://cdn.teledynelecroy.com/files/manuals/maui-remote-control-and-automation-manual.pdf)).

This Teledyne oscilloscope family can also receive direct VBS commands. See `vbs_ask()` and `vbs_write()`.
