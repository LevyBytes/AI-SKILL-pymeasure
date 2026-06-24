# Lecroyt3Dso1204 (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) - Callable that receives the candidate value together with the valid-value group; it returns an accepted value or raises an exception (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

-

**values** (`TypeVar`(`Vs`)) - Valid choices supplied as a list, tuple, range, or dictionary; when `map_values` is True, the entries may also map inputs to outputs. (default: `()`)

-

**map_values** (`bool`) - Boolean switch indicating whether `values` should be treated as a mapping (default: `False`)

-

**set_process** (`Callable`[[`Any`], `Any`]) - Callable applied to the incoming value before value mapping; it returns the processed value (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

-

**check_set_errors** (`bool`) - Enables or disables error checking after a set operation (default: `False`)

-

**dynamic** (`bool`) - Indicates whether instances or subclasses are expected to alter the property parameters. For a usage example, see `control()`. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]

 shutdown()

Moves the instrument into a stable, safe state

Return type:

`None`

 single()

Triggers one acquisition of data on the instrument.

Equivalent to pressing the front-panel Single key.

 *property *status*: Any*

Read the status byte together with the Master Summary Status bit.

 stop()

Halts acquisition, matching the front-panel Stop key behavior.

 *property *timebase

Return the timebase setup as a dict with these keys:

-

`timebase_scale`: seconds/div horizontal scale (float)

-

`timebase_offset`: seconds between the trigger and reference position (float)

-

`timebase_hor_magnify`: zoom-window horizontal scale in seconds/div (float)

-

`timebase_hor_position`: zoom-window horizontal position in seconds (float)

 *property *timebase_hor_magnify*: Any*

Adjust the zoomed (delayed) window horizontal scale, in seconds/div.

The allowable range comes from the main sweep scale.

 *property *timebase_hor_position*: Any*

Set the horizontal position for the zoomed (delayed) view of the main sweep.

The valid range depends on both the main sweep range and main sweep horizontal position. The chosen value must leave the zoomed view window inside the main sweep range.

 *property *timebase_offset*: Any*

Set the seconds offset between the trigger event and the reference position, which defaults to the screen center.

 *property *timebase_scale*: Any*

Set the main-window horizontal scale in seconds, expressed as units per division (float).

 timebase_setup(*scale=None*, *offset=None*, *hor_magnify=None*, *hor_position=None*)

Configure timebase values without changing omitted parameters. Changing one parameter can affect others; consult the oscilloscope documentation and, when needed, call timebase_setup several times in sequence.

Parameters:

-

**scale** - Seconds interval from trigger event to reference position. (default: `None`)

-

**offset** - Horizontal scale in seconds/div for each division. (default: `None`)

-

**hor_magnify** - Zoomed-window horizontal scale, in seconds/div. (default: `None`)

-

**hor_position** - Zoomed-window horizontal position, in seconds. (default: `None`)

 *property *trigger

Return trigger setup as a dict using these keys:

-

“mode”: trigger sweep mode [auto, normal, single, stop]

-

`trigger_type`: waveform-acquisition trigger condition [edge, slew,glit,intv,runt,drop]

-

“source”: trigger source [c1,c2,c3,c4]

-

`hold_type`: hold type; see page 172 of programing guide

-

`hold_value1`: hold value1; see page 172 of programing guide

-

`hold_value2`: hold value2; see page 172 of programing guide

-

`coupling`: input coupling for the selected trigger sources

-

`level`: trigger-level voltage for the active trigger source

-

`level2`: lower trigger-level voltage for the active trigger source (only slew/runt trigger)

-

`slope`: specified trigger source trigger slope

 *property *trigger_mode*: Any*

Set the trigger sweep mode (string).

<mode>:= {AUTO,NORM,SINGLE,STOP}

-

auto : In AUTO sweep mode, the oscilloscope searches for a trigger signal satisfying the conditions. When the trigger condition is met, the upper-left running state shows Trig'd and a stable waveform appears. If not, the running state remains Auto and the waveform shown is unstable.

-

normal : In NORMAL sweep mode, the oscilloscope waits for triggering while searching for trigger signals that satisfy the conditions. If the condition is met, the running state reads Trig'd and the display shows a stable waveform. Otherwise, the running state reads Ready, and the display either keeps the last triggered waveform (previous trigger) or shows no waveform (no previous trigger).

-

single : In SINGLE sweep mode, the SINGLE key backlight turns on; the oscilloscope waits for a trigger and searches for a trigger signal satisfying the conditions. When the condition is met, the running state reads Trig'd and the display shows a stable waveform. The oscilloscope then halts the scan, lights the RUN/STOP key red, and reports Stop as the running status. If no trigger is found, the running state reads Ready and no waveform is displayed.

-

stopped : STOP is accepted as an option for this command, but it is not an oscilloscope trigger mode.

 *property *trigger_select

Set the waveform-acquisition trigger condition (string).

Some trigger types require additional parameters. Supply those extra parameters as pairs: the first element names the variable to change, and the second provides its new value. The pairs can appear in any order and can be limited to only the variables being changed.

Five parameters can be specified. Parameters 1. 2. 3. are required in every case. Parameters 4. 5. are only needed for particular combinations of the earlier parameters.

1.

<trig_type>:={edge, slew, glit, intv, runt, drop}

2.

<source>:={c1, c2, c3, c4, line}

3.

<hold_type>:=

  -

{ti, off} for edge trigger.

  -

{ti} for drop trigger.

  -

{ps, pl, p2, p1} applies to glit/runt trigger.

  -

{is, il, i2, i1} applies to slew/intv trigger.

4.

<hold_value1>:= a time value with unit.

5.

<hold_value2>:= a time value with unit.

Note:

-

`line` is selectable only with trigger type `edge`.

-

Give all time arguments as multiples of seconds; use scientific notation when needed.

-

hold_values ranges depend on trigger type: [80nS, 1.5S] for `edge` trigger, and [2nS, 4.2S] for the others.

-

`trigger_select` switches automatically among the short, normal, and extended versions according to the expected parameter count.

 trigger_setup(*mode=None*, *source=None*, *trigger_type=None*, *hold_type=None*, *hold_value1=None*, *hold_value2=None*, *coupling=None*, *level=None*, *level2=None*, *slope=None*)

Set up trigger.

Omitted parameters stay unchanged. Altering one parameter can affect others; consult the oscilloscope documentation and, if necessary, make consecutive trigger_setup and channel_setup calls.

Parameters:

-

**mode** – trigger sweep mode [auto, normal, single, stop] (default: `None`)

-

**source** – trigger source [c1, c2, c3, c4, line] (default: `None`)

-

**trigger_type** - Waveform-acquisition trigger condition [edge,slew,glit,intv,runt,drop] (default: `None`)

-

**hold_type** - Hold type; see page 172 of programing guide. (default: `None`)

-

**hold_value1** - Hold value1; see page 172 of programing guide. (default: `None`)

-

**hold_value2** - Hold value2; see page 172 of programing guide. (default: `None`)

-

**coupling** - Input coupling for the selected trigger sources. (default: `None`)

-

**level** - Trigger-level voltage for the active trigger source. (default: `None`)

-

**level2** - Lower trigger-level voltage for the active trigger source (only slew/runt trigger). (default: `None`)

-

**slope** - Trigger slope for the specified trigger source. (default: `None`)

 values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return the reply as a list of formatted values.

Parameters:

-

**command** (`str`) - SCPI command sent to the instrument.

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable run on the instrument reply string before splitting; it returns that processed string. (default: `None`)

-

**separator** (`Optional`[`str`]) - Separator character used to split the device-returned string into a list. None means split on any whitespace; see `str.split`. (default: `','`)

-

**maxsplit** (`int`) - Maximum number of splits to apply to the string returned by the device. `-1` (default) means unlimited. (default: `-1`)

-

**cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: if casting fails, that element remains a string. A future version will raise an error instead. To allow mixed types explicitly, pass a dedicated function, for example `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

****kwargs** - Keyword arguments forwarded to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] - List containing the requested type, or, in deprecated behavior, str for elements where casting fails.

 wait_for(*query_delay=None*)

Pause briefly; `ask` uses this delay before reading.

Parameters:

**query_delay** (`Optional`[`float`]) - Seconds to wait between writing and reading. None selects the default delay. (default: `None`)

Return type:

`None`

 *property *waveform_first_point*: Any*

Set the address of the first data point to send (int). In sequence-mode waveforms, this is the relative address within the selected segment. The first data point begins at zero and is strictly positive.

 *property *waveform_points*: Any*

Set how many waveform points the digitize method transfers (int). NP = 0 sends all data points.

Be aware that the oscilloscope can return fewer than the requested nb of points.

 *property *waveform_preamble

Return selected-waveform-source preamble information as a dict with these keys:

-

“type”: normal, peak detect, average, high resolution (str)

-

`requested_points`: user-requested number of data points (int)

-

`sampled_points`: data-point count sampled by the oscilloscope (int)

-

`transmitted_points`: count of data points actually transmitted (optional) (int)

-

`memory_size`: oscilloscope internal-memory size in bytes (int)

-

`sparsing`: sparse point; it sets the interval between data points. (int)

-

`first_point`: first data point address to be sent (int)

-

`source`: data source: `C1`, `C2`, `C3`, `C4`, `MATH`.

-

`unit`: physical units used for the Y-axis

-

`type`: data acquisition type. Can be `normal`, `peak`, `average`, `highres`

-

`average`: number of times used for average acquisition

-

`sampling_rate`: sampling rate; this property is read-only

-

`grid_number`: horizontal grid count; this property is read-only

-

`status`: scope acquisition status. Can be `stopped`, `triggered`, `ready`, `auto`, `armed`

-

`xdiv`: horizontal scale in seconds, using units per division

-

`xoffset`: seconds between the trigger event and the reference position

-

`ydiv`: vertical scale in Volts, using units per division

-

`yoffset`: value shown at the screen center, in Volts

 *property *waveform_sparsing*: Any*

Set the data-point interval (integer). Example:

SP = 0 transfers all data points. SP = 4 transfers 1 point per 4 data points.

 write(*command*, ***kwargs*)

Send the command to the instrument via the adapter.

Note: if the previous command was issued less than WRITE_INTERVAL_S ago, this method waits for the remaining time, ensuring commands are not sent faster than 1/WRITE_INTERVAL_S Hz.

Parameters:

**command** - command string sent to the instrument

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) - Values to transmit.

-

****kwargs** (**args**,*) - Additional arguments passed to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send bytes content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.lecroy.lecroyT3DSO1204.LeCroyT3DSO1204Channel(*parent*, *id*, ***kwargs*)

Bases: [`TeledyneOscilloscopeChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#pymeasure.instruments.teledyne.teledyne_oscilloscope.TeledyneOscilloscopeChannel)

LeCroy T3DSO1204 Oscilloscope channel implementation.

Implementation patterned after the Channel object from the Keysight DSOX1102G instrument.

 *property *bwlimit*: Any*

Control the internal 20 MHz low-pass filter (strict bool).

For this filter, the oscilloscope provides only one available frequency.

 *property *invert*: Any*

Control input-signal inversion (strict bool).

 *property *skew_factor*: Any*

Set the skew factor for the selected channel relative to other channels. Each analog channel supports adjustment by + or -100 ns, giving 200 ns total difference between channels. The oscilloscope's skew control can remove cable-delay errors between channels.

 *property *trigger_level2*: Any*

Set the lower trigger level voltage for the specified source (float). Runt/slope triggers use both higher and lower trigger levels. When setting the trigger level, divide it by the probe attenuation. This behavior is not documented in the datasheet and is probably a scope firmware bug. Out-of-range values are adjusted to the nearest legal value.

 *property *unit*: Any*

Set the unit for the specified trace. Measurement results, channel sensitivity, and trigger level reflect the selected measurement units. (`A` for Amperes, `V` for Volts).
