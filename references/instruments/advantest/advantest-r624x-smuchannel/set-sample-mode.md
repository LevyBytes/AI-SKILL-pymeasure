# pymeasure.instruments.advantest.advantestR624X.SMUChannel.set_sample_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_sample_mode(*mode*, *auto_sampling=True*)

Configure channel-to-channel behavior for synchronous, asynchronous, tracking, or search measurement operation (`JM`).

Parameters:

- **mode** (`SampleMode`) – Sample Mode

- **auto_sampling** (*bool**, **optional*) – Controls auto sampling; defaults to True. If True, each trigger causes measurement data to be output automatically. If False, output occurs only when explicitly requested, for example with `FCH?`. (default: `True`)

Warning

In dual-channel synchronous modes such as `PULSED_SYNC` and `SWEEP_SYNC`, pass `auto_sampling=False`. If `auto_sampling=True` (the default), data returned through `select_for_output()` / `FCH?` reports the generated/source value instead of the measured result.
