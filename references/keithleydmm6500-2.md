# Keithleydmm6500 (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

When the current active mode lacks autorange support, this command waits until the adapter's timeout and then raises -113 "Undefined header" error.

 disable_filter(*mode=None*)

Turn off the averaging filter on the active mode, or specify another mode by name.

Parameters:

**mode** - Supply a valid `mode` name, or pass None to use the active mode (default: `None`)

Returns:

A filter status value returned by the instrument

 enable_filter(*mode=None*, *type='repeat'*, *count=1*)

Turn on the averaging filter on the active mode, or specify another mode by name.

Parameters:

-

**mode** - Supply a valid `mode` name, or pass None to use the active mode (default: `None`)

-

**type** - Averaging filter type; accepted choices are `REPeat`, `MOVing`, or `HYBRid`. (default: `'repeat'`)

-

**count** - Number of averages; allowed values range from 1 to 100 (default: `1`)

Returns:

A filter status value returned by the instrument

 *property *mode*: Any*

Set the measurement configuration mode. Use `current` for DC current; `current ac` for AC current; `voltage` for DC voltage; `voltage ac` for AC voltage; `resistance` for 2-wire resistance; `resistance 4W` for 4-wire resistance; or `diode`, `capacitance`, `temperature`, `continuity`, `period`, `frequency`, and `voltage ratio`.

 *property *nplc*: Any*

Set integration time as a count of power line cycles (NPLC). Valid values are 0.0005 to 15 for 60Hz, with 12 as the upper value for 50Hz or 400Hz. This command applies only to `voltage`, 2-wire ohms, and 4-wire ohms.

Note

NPLC setting is supported only in these modes: `voltage`, `current`, `resistance`, `resistance 4W`, `diode`, `temperature`, and `voltage ratio`. When the current active mode lacks NPLC support, this command waits until the adapter's timeout and then raises -113 "Undefined header" error.

 *property *range*: Any*

Set the measuring range for the currently active mode. For measurements of `frequency` and `period`, `range` refers to the signal's input voltage rather than its frequency.

 write(*command*)

Send a command to the instrument.
