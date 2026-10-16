# pymeasure.instruments.keithley.Keithley2000.enable_filter

[Owning PyMeasure class, adapter and connection contract](overview.md)

enable_filter(*mode=None*, *type='repeat'*, *count=1*)

Turn on the averaging filter for the active mode, or for another mode selected by name.

Parameters:

- **mode** — Valid `mode` name, or None to target the active mode (default: `None`)

- **type** — Averaging filter type, either “repeat” or “moving”. (default: `'repeat'`)

- **count** — Number of averages; accepted values run from 1 to 100 (default: `1`)
