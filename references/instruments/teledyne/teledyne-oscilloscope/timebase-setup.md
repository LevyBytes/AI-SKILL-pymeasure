# pymeasure.instruments.teledyne.TeledyneOscilloscope.timebase_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

timebase_setup(*scale=None*, *offset=None*)

Configure the timebase while leaving omitted parameters unchanged. Changing one value can also alter related values. Consult the oscilloscope documentation, and call timebase_setup repeatedly when staged adjustments are required.

Parameters:

- **scale** – seconds between the trigger event and reference position. (default: `None`)

- **offset** – horizontal seconds/div scale. (default: `None`)

## Related property contracts

- Open when checking pymeasure.instruments.teledyne.TeledyneOscilloscope.trigger: [trigger](trigger.md).
