# pymeasure.instruments.lecroy.LeCroyT3DSO1204.trigger_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

trigger_setup(*mode=None*, *source=None*, *trigger_type=None*, *hold_type=None*, *hold_value1=None*, *hold_value2=None*, *coupling=None*, *level=None*, *level2=None*, *slope=None*)

Set up trigger.

Omitted parameters stay unchanged. Altering one parameter can affect others; consult the oscilloscope documentation and, if necessary, make consecutive trigger_setup and channel_setup calls.

Parameters:

- **mode** – trigger sweep mode [auto, normal, single, stop] (default: `None`)

- **source** – trigger source [c1, c2, c3, c4, line] (default: `None`)

- **trigger_type** - Waveform-acquisition trigger condition [edge,slew,glit,intv,runt,drop] (default: `None`)

- **hold_type** - Hold type; see page 172 of programing guide. (default: `None`)

- **hold_value1** - Hold value1; see page 172 of programing guide. (default: `None`)

- **hold_value2** - Hold value2; see page 172 of programing guide. (default: `None`)

- **coupling** - Input coupling for the selected trigger sources. (default: `None`)

- **level** - Trigger-level voltage for the active trigger source. (default: `None`)

- **level2** - Lower trigger-level voltage for the active trigger source (only slew/runt trigger). (default: `None`)

- **slope** - Trigger slope for the specified trigger source. (default: `None`)
