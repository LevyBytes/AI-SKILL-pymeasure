# pymeasure.instruments.lecroy.LeCroyT3DSO1204.timebase_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

timebase_setup(*scale=None*, *offset=None*, *hor_magnify=None*, *hor_position=None*)

Configure timebase values without changing omitted parameters. Changing one parameter can affect others; consult the oscilloscope documentation and, when needed, call timebase_setup several times in sequence.

Parameters:

- **scale** - Seconds interval from trigger event to reference position. (default: `None`)

- **offset** - Horizontal scale in seconds/div for each division. (default: `None`)

- **hor_magnify** - Zoomed-window horizontal scale, in seconds/div. (default: `None`)

- **hor_position** - Zoomed-window horizontal position, in seconds. (default: `None`)

## Related property contracts

- Open when checking pymeasure.instruments.lecroy.LeCroyT3DSO1204.trigger: [trigger](trigger.md).
