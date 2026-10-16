# pymeasure.instruments.teledyne.TeledyneOscilloscope.trigger_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

trigger_setup(*mode=None*, *source=None*, *trigger_type=None*, *hold_type=None*, *hold_value1=None*, *hold_value2=None*, *coupling=None*, *level=None*, *level2=None*, *slope=None*)

Set up trigger.

Omitted parameters are left as-is. Updating one parameter can affect others. Use the oscilloscope documentation, and make multiple trigger_setup and channel_setup calls when stepwise configuration is necessary.

Parameters:

- **mode** – trigger sweep mode [auto, normal, single, stop] (default: `None`)

- **source** – trigger source [c1, c2, c3, c4, line] (default: `None`)

- **trigger_type** – waveform acquisition trigger condition [edge,slew,glit,intv,runt,drop] (default: `None`)

- **hold_type** – hold type (refer to page 172 of programing guide) (default: `None`)

- **hold_value1** – hold value1 (refer to page 172 of programing guide) (default: `None`)

- **hold_value2** – hold value2 (refer to page 172 of programing guide) (default: `None`)

- **coupling** – coupling used for the selected trigger sources (default: `None`)

- **level** – voltage level for the active trigger source (default: `None`)

- **level2** – lower trigger voltage for the active trigger source, only with slew/runt trigger (default: `None`)

- **slope** – slope setting for the specified trigger source (default: `None`)
