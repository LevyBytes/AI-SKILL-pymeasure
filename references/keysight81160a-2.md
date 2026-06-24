# Keysight81160A (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable that transforms the instrument reply string before it is split, returning that processed string. (default: `None`)

-

**separator** (`Optional`[`str`]) - Character used as the delimiter that turns the device reply string into a list. None splits on any whitespace; see `str.split`. (default: `','`)

-

**maxsplit** (`int`) - The returned device string is split no more than maxsplit times. -1 (default) means unlimited splitting. (default: `-1`)

-

**cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every item produced by splitting the string.

Deprecated since version 0.17.0: When a cast operation fails, that element remains a string. A later version will raise an error instead. To permit mixed types deliberately, supply a dedicated function, for example `cast_or_str()` as cast function. (default: `<class 'float'>`)

-

****kwargs** - Keyword arguments forwarded to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] - List containing the requested type, or, while deprecated behavior remains, str entries where casting fails.

 *property *voltage_high*: Any*

Set or query the upper voltage level in Volts (float).(dynamic)

 *property *voltage_low*: Any*

Set or query the lower voltage level in Volts (float).(dynamic)

 wait_for(*query_delay=None*)

Pause for a time interval. 'ask' uses this wait before reading.

Parameters:

**query_delay** (`Optional`[`float`]) - Seconds to wait between writing and reading. None means the default delay. (default: `None`)

Return type:

`None`

 wait_for_trigger(*timeout=3600*, *should_stop=<function Agilent33500.<lambda>>*)

Block until triggering completes or the timeout is hit.

Parameters:

-

**timeout** - Maximum permitted wait duration. Exceeding timeout raises TimeoutError. Setting timeout to zero disables the timeout. (default: `3600`)

-

**should_stop** - Optional bool-returning function that can stop the wait before it finishes. (default: `<function Agilent33500.<lambda> at 0x7aa592a19010>`)

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) - command string sent to the instrument

-

**kwargs** - Keyword arguments passed through to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) - Values that will be transmitted.

-

****kwargs** (**args**,*) - Additional arguments passed on to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send the bytes content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.keysight.keysight81160A.Keysight81160AChannel(**args*, ***kwargs*)

Base class: [`Agilent33500Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33521A.html#pymeasure.instruments.agilent.agilent33500.Agilent33500Channel)

Models the Keysight 81160A channel and exposes a high-level interface for working with the instrument channels.

 apply_dc(*voltage*)

Apply a DC voltage.

Parameters:

**voltage** - Voltage value to apply (float).

 apply_noise(*amplitude*, *offset*)

Apply noise to the output.

Parameters:

-

**amplitude** - Noise amplitude (float).

-

**offset** – The offset voltage (float).

 apply_pulse(*frequency*, *amplitude*, *offset*)

Apply a pulse waveform.

Parameters:

-

**frequency** - Pulse frequency (float).

-

**amplitude** - Pulse amplitude (float).

-

**offset** – Offset voltage (float).

 apply_sin(*frequency*, *amplitude*, *offset*)

Apply a sine waveform.

Parameters:

-

**frequency** - Sine wave frequency (float).

-

**amplitude** - Sine wave amplitude (float).

-

**offset** – Offset voltage (float).

 apply_square(*frequency*, *amplitude*, *offset*)

Apply a square waveform.

Parameters:

-

**frequency** - Square wave frequency (float).

-

**amplitude** - Square wave amplitude (float).

-

**offset** – Offset voltage (float).

 apply_user_waveform(*frequency*, *amplitude*, *offset*)

Apply a user-defined waveform.

Parameters:

-

**frequency** - User waveform frequency (float).

-

**amplitude** - User waveform amplitude (float).

-

**offset** – Offset voltage (float).

 *property *coupling_enabled*: Any*

Set or query channel coupling enablement (bool). 'True' copies values from this channel to another one.

 delete_waveform(*name*)

Remove a waveform from the generator's nonvolatile memory.

Parameters:

**name** - Name of the user-defined waveform that should be deleted.

 *property *free_memory_slots*: Any*

Return the count of free non-volatile memory slots available for user waveform storage (int).

 *property *limit_high*: Any*

Set or query the high-level voltage limit in Volts (float).(dynamic)

 *property *limit_low*: Any*

Set or query the low-level voltage limit in Volts (float).(dynamic)

 *property *limit_state_enabled*: Any*

Set or query whether the state limit is enabled (bool).

 save_waveform(*waveform*, *name*)

Store a waveform in the generator's nonvolatile memory.

Parameters:

-

**waveform** – The waveform data.

-

**name** - Waveform memory identifier. It can contain up to 12 characters; the first one must be a letter (A-Z), and later characters may be numbers (0-9) or the underscore character ('_'). Blank spaces are not allowed.

 *property *trigger_count*: Any*

Set or query the cycle count produced for each triggered burst (int). Enable burst state if number > 1.

Abbreviated form of burst_ncycles and burst_state = True(dynamic)

 *property *trigger_mode*: Any*

Set or query the triggering mode (string, strictly 'IMM', 'INT2', 'EXT' or 'MAN').(dynamic)

 *property *waveform_volatile

Get volatile waveform data.

Warning: This property can differ from the current device volatile waveform. It returns only the waveform previously set via this driver. After a device power-cycle, external modification, or no prior waveform set, the returned value may be invalid or None.

Returns:

waveform data (array-like), or None when unset.

 *property *waveforms*: Any*

Return the available user waveforms stored in memory (list[str]).
