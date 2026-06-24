# Lecroyt3Dso1204 (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### LeCroy T3DSO1204 Oscilloscope

 *class *pymeasure.instruments.lecroy.LeCroyT3DSO1204(*adapter*, *name='LeCroy T3DSO1204 Oscilloscope'*, ***kwargs*)

Bases: [`TeledyneOscilloscope`](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#pymeasure.instruments.teledyne.TeledyneOscilloscope)

Provides the LeCroy T3DSO1204 Oscilloscope interface used to communicate with the instrument.

Use the LeCroy T3DSO1204 Oscilloscope Programmer’s Guide when you need more detail on the lower-level methods that talk directly to the scope.

This implementation derives from the shared `TeledyneOscilloscope` base class.

Attributes:

>

WRITE_INTERVAL_S: lower bound on the gap between consecutive commands. When a command arrives before WRITE_INTERVAL_S has elapsed since the prior command, execution waits until WRITE_INTERVAL_S seconds have passed. Some oscilloscope operations are slow enough that callers may still need to tune the sleep interval between commands. The default WRITE_INTERVAL_S is 10ms, but the best setting depends on both the command mix and connection type, so there is no single value that works everywhere. In practice, 10ms to 500ms has worked well, with the choice driven by commands and connection latency.

```python
scope = LeCroyT3DSO1204(resource)
scope.autoscale()
ch1_data_array, ch1_preamble = scope.download_waveform(source="C1", points=2000)
# ...
scope.shutdown()

```

 ch_1

Channel:

`LeCroyT3DSO1204Channel`

 ch_2

Channel:

`LeCroyT3DSO1204Channel`

 ch_3

Channel:

`LeCroyT3DSO1204Channel`

 ch_4

Channel:

`LeCroyT3DSO1204Channel`

 *class *BaseChannelCreator(***kwargs*)

Bases: `object`

Common parent for ChannelCreator and MultiChannelCreator.

Parameters:

-

**cls** – Class object used for every child, or a tuple/list that supplies one class per child.

-

****kwargs** – Keyword arguments passed to every child.

 *class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach one channel to the parent class.

During instantiation, the child is attached to the parent instance through `CommonBase.add_child()`. The channel interface uses the attribute name assigned to ChannelCreator in the Instrument class.

```python
class Extreme5000(Instrument):
    # Two output channels, accessible by their property names
    # and both are accessible through the 'channels' collection
    output_A = Instrument.ChannelCreator(Extreme5000Channel, "A")
    output_B = Instrument.ChannelCreator(Extreme5000Channel, "B")
    # A channel without a channel accessible through the 'motor' collection
    motor = Instrument.ChannelCreator(MotorControl)

inst = SomeInstrument()
# Set the extreme_temp for channel A of Extreme5000 instrument
inst.output_A.extreme_temp = 42

```

Parameters:

-

**cls** (`type`[`Child`]) – Channel class used for the channel interface.

-

**id** (`Union`[`int`, `str`, `None`]) – Instrument channel id, supplied as an integer or string. (default: `None`)

-

****kwargs** – Keyword arguments applied to every child.

 *class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach multiple channels to the parent class.

At instantiation, the children are registered on the parent instance using `CommonBase.add_child()`. The attribute name, for example `channels`, becomes the collection that holds the child objects. A custom attribute prefix may be supplied; absent a specific need, use `channels` for the attribute and keep the default `"ch_"` prefix.

```python
class Extreme5000(Instrument):
    # Three channels of the same type: 'ch_A', 'ch_B', 'ch_C'
    # and add them to the 'channels' collection
    channels = Instrument.MultiChannelCreator(Extreme5000Channel, ["A", "B", "C"])
    # Two channel interfaces of different types: 'fn_power', 'fn_voltage'
    # and add them to the 'functions' collection
    functions = Instrument.MultiChannelCreator((PowerChannel, VoltageChannel),
                                    ["power", "voltage"], prefix="fn_")

```

Parameters:

-

**cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) – One class for every child, or a tuple/list containing the class for each child.

-

**id** (`Union`[`int`, `str`, `None`]) – Tuple/list of instrument channel ids. (default: `None`)

-

**prefix** (`Optional`[`str`]) – Prefix used for collection attributes; for example, “ch_” creates self.ch_A. If prefix evaluates False, the child is attached directly under the variable name. Required when id is a tuple/list. (default: `'ch_'`)

-

****kwargs** – Keyword arguments supplied to every child.

 *property *acquisition_average*: Any*

Set or read the averaging count for average acquisition.

 acquisition_sample_size(*source*)

Read the acquisition sample size for a selected channel, primarily for waveform capture. For source MATH, SANU? MATH appears not to respond correctly, so the memory size is returned instead.

Parameters:

**source** – Channel number or channel name.

Returns:

Returns the acquisition sample size for that channel.

 *property *acquisition_sample_size_c1*: Any*

Read how many data points the hardware acquires from channel 1 input. Channel 1 and channel 2 share one ADC, so this sample count is identical for both.

 *property *acquisition_sample_size_c2*: Any*

Read how many data points the hardware acquires from channel 2 input. Channel 1 and channel 2 share one ADC, so this sample count is identical for both.

 *property *acquisition_sample_size_c3*: Any*

Read how many data points the hardware acquires from channel 3 input. Channel 3 and channel 4 share one ADC, so this sample count is identical for both.

 *property *acquisition_sample_size_c4*: Any*

Read how many data points the hardware acquires from channel 4 input. Channel 3 and channel 4 share one ADC, so this sample count is identical for both.

 *property *acquisition_sampling_rate*: Any*

Read the scope sample rate.

 *property *acquisition_status*: Any*

Read the scope acquisition status.

 *property *acquisition_type*: Any*

Select the acquisition mode.

Allowed values are ‘normal’, ‘peak’, ‘average’, and ‘highres’.

 add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Attach a child to this instance and return its position in the children list.

The created child can be reached through its id in the children dictionary or through the generated attribute. For example, an instrument fifth channel with id “F” can be accessed either way: `instrument.channels["F"] == instrument.ch_F`

Note

Keep the default collection and prefix values unless separate child collections must be distinguished, such as analog and digital channel types.

Parameters:

-

**cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) – Channel class.

-

**id** (`Union`[`int`, `str`, `None`]) – Child id used for communication, such as “A”. (default: `None`)

-

**collection** (`str`) – Name of the child collection used for dictionary access to channel interfaces. (default: `'channels'`)

-

**prefix** (`Optional`[`str`]) – Prefix added when creating multiple channel interface attributes; for example, “ch_” produces self.ch_A. If prefix evaluates False, the child is attached directly below the collection name. (default: `'ch_'`)

-

**attr_name** (`Optional`[`str`]) – For a single channel interface, attr_name supplies the attribute name used when the interface is assigned. (default: `''`)

-

****kwargs** – Keyword arguments forwarded to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) – Newly created child instance.

 ask(*command*, *query_delay=None*)

Send a command to the instrument and return the response that is read back.

Parameters:

-

**command** (`str`) – Command string sent to the instrument.

-

**query_delay** (`Optional`[`float`]) – Seconds to wait between the write and read operations. (default: `None`)

Returns:

`str` – Device response string with read_termination removed.

 autoscale()

Autoscale displayed channels.

 binary_values(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument and return the binary response as a numpy array.

Parameters:

-

**command** (`str`) – Command sent to the instrument.

-

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. (default: `None`)

-

**kwargs** – Arguments forwarded to `read_binary_values()`.

Returns:

NumPy array of values.

 *property *bwlimit*: Any*

Configure the internal low-pass filter across all channels.(dynamic)

 center_trigger()

Move the trigger levels to the center of the trigger source waveform.

 ch(*source*)

Return a channel object by index or name. If source is “math”, return the scope object itself.

Parameters:

**source** – Accepted source identifiers: 1, 2, 3, 4, C1, C2, C3, C4, MATH

Returns:

handle to the selected source.

 check_errors()

Drain and return all instrument errors.

Returns:

List of error entries.

 check_get_errors()

After a property get, check for errors and log any that are present.

Used when that property has `check_get_errors=True`.

An override may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set, check for errors and log any that are present.

Used when that property has `check_set_errors=True`.

An override may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property is used to synchronize a controller with a device. The Operation Complete query writes ASCII character 1 into the device’s Output Queue after every pending selected device operation has completed.

 *static *control(*get_command*, *set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. The resulting property can be written to and read from the instrument. Related helpers are `measurement()` and `setting()`.

Parameters:

-

**get_command** (`Optional`[`str`]) – String command used to request the value; use None when getting is unsupported (see also `setting()`).

-

**set_command** (`Optional`[`str`]) – String command used to write the value; use None when setting is unsupported (see also `measurement()`).

-

**docs** (`str`) – Docstring text inserted into the documentation.

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `TypeVar`(`V2`)]) – Function receiving a value plus a set of valid values; it returns an accepted value or raises an exception. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f80f0>`)

-

**values** (`TypeVar`(`Vs`)) – Valid values supplied as a list, tuple, range, or dictionary; these may also map values when `map_values` is True. (default: `()`)

-

**map_values** (`bool`) – Boolean flag indicating whether values should be treated as a map. (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f81a0>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives and processes the value list. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8250>`)

-

**set_process** (`Callable`[[`TypeVar`(`V2`)], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8300>`)

-

**check_set_errors** (`bool`) – Enables error checking after a set operation. (default: `False`)

-

**check_get_errors** (`bool`) – Enables error checking after a get operation. (default: `False`)

-

**dynamic** (`bool`) – Indicates whether instances or subclasses may change the property parameters. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that transforms the string returned by the instrument before splitting; it returns the transformed string. (default: `None`)

-

**separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None splits on arbitrary whitespace (see `str.split`). (default: `','`)

-

**maxsplit** (`int`) – The device response string is split no more than maxsplit times. -1 means there is no limit. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: A failed cast leaves that element as a string; see `values()`. To permit mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) – Extra keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

The dynamic parameter can be used as shown here:

```python
class GenericInstrument(Instrument):
    center_frequency = Instrument.control(
        ":SENS:FREQ:CENT?;", ":SENS:FREQ:CENT %e GHz;",
        " A floating point property that represents the frequency ... ",
        validator=strict_range,
        # Redefine this in subclasses to reflect actual instrument value:
        values=(1, 20),
        dynamic=True  # enable changing property parameters on-the-fly
    )

class SpecificInstrument(GenericInstrument):
    # Identical to GenericInstrument, except for frequency range
    # Override the "values" parameter of the "center_frequency" property
    center_frequency_values = (1, 10) # Redefined at subclass level

instrument = SpecificInstrument()
instrument.center_frequency_values = (1, 6e9) # Redefined at instance level

```

Warning

Unexpected behavior can appear when using dynamic properties

Use care with dynamic properties, because class or instance attributes that match reserved naming patterns can produce unwanted side effects. Treat `property_param` as reserved for dynamic property control: `property` is the dynamic property name, such as `center_frequency`, and `param` is one of this method’s parameter names other than `dynamic` and `docs`, such as `values`.

 default_setup()

Prepare the oscilloscope for remote operation.

For remote operation, force COMM_HEADER to OFF. COMM_HEADER determines how query responses are formatted, but it does not change how the oscilloscope parses inbound messages. Long and short headers may be sent regardless of CHDR. With COMM_HEADER set to OFF, replies contain minimal information and are easier for the driver to parse. During normal operation, do not change COMM_HEADER; any setting other than OFF causes this driver to fail.

 display_parameter(*parameter*, *channel*)

Equivalent to the display_parameter method on the Channel subclass.

 download_image()

Retrieve a BMP screenshot from the oscilloscope display as a bytearray in the requested file format.

 download_waveform(*source*, *requested_points=None*, *sparsing=None*)

Read data points from the chosen oscilloscope source.

The call returns two np.ndarray objects, one for data points and one for time points, plus a dict containing the waveform preamble metadata.

Parameters:

-

**source** – Measurement source; valid choices are “C1”, “C2”, “C3”, “C4”, and “MATH”.

-

**requested_points** – Number of points to acquire. If None, the request reuses the point count from the previous call, namely the number of points stored in oscilloscope memory. If 0, the maximum point count is returned. (default: `None`)

-

**sparsing** – Interval between data points. For example, if sparsing = 4, the read keeps one point out of every 4. If 0 or None, the previous call’s sparsing is reused, which is the sparsing value stored in oscilloscope memory. (default: `None`)

Returns:

data_ndarray, time_ndarray, waveform_preamble_dict: dict layout is described by the waveform_preamble property.

 *static *get_channel_pairs(*cls*)

Return every channel pair defined on the Instrument.

 *static *get_channels(*cls*)

Return every ChannelCreator and MultiChannelCreator instance defined on the Instrument.

Return type:

`list`[`tuple`[`str`, [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)]]

 *property *grid_display*: Any*

Set the display grid type: FULL, HALF, or OFF.

 *property *id*: Any*

Read the instrument identification string.

 *property *intensity*: Any*

Set the grid or trace intensity level in percent.

 *property *math_define*: Any*

Choose the waveform math operation applied between two channels.

Pass three parameters together as a tuple:

1.

source1 : left-side source channel

2.

operation : operator must be “*”, “/”, “+”, “-”

3.

source2 : right-side source channel

 *property *math_vdiv*: Any*

Set the vertical scale for the chosen math operation.

This command is valid only for add, subtract, multiply, and divide operation. The legal scale values depend on the selected operation.

 *property *math_vpos*: Any*

Set the vertical position for the math waveform associated with the specified source.

The point is measured in screen pixels relative to the screen center. For example, point 50 displays the math waveform 1 grid above the vertical center, because one grid is 50.

 *property *measure_delay*: Any*

Control measurement delay.

MEASURE_DELY puts the instrument into continuous measurement mode and begins a selected delay measurement. The MEASURE_DELY? query returns the measured delay value. The command takes three arguments using this syntax:

>

measure_delay = (<type>,<sourceA>,<sourceB>)

<type> := {PHA,FRR,FRF,FFR,FFF,LRR,LRF,LFR,LFF,SKEW}

Valid pair form: <sourceA>,<sourceB> := {C1,C2,C3,C4}; when sourceA=CX and sourceB=CY, require X < Y.

| Type | Description |
| --- | --- |
| PHA | Phase difference for two channels. (rising edge - rising edge) |
| FRR | Two-channel delay. (first rising edge - first rising edge) |
| FRF | Two-channel delay. (first rising edge - first falling edge) |
| FFR | Two-channel delay. (first falling edge - first rising edge) |
| FFF | Two-channel delay. (first falling edge - first falling edge) |
| LRR | Two-channel delay. (first rising edge - last rising edge) |
| LRF | Two-channel delay. (first rising edge - last falling edge) |
| LFR | Two-channel delay. (first falling edge - last rising edge) |
| LFF | Two-channel delay. (first falling edge - last falling edge) |
| Skew | Two-channel delay. (edge – edge of the same type) |

 measure_parameter(*parameter*, *channel*)

Equivalent to the measure_parameter method on the Channel subclass.

 *static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. The property represents a measurement quantity that can be read from the instrument but not written.

Parameters:

-

**get_command** (`str`) – String command used to request the value.

-

**docs** (`str`) – Docstring text inserted into the documentation.

-

**values** (`Any`) – Valid values supplied as a list, tuple, range, or dictionary; these may also map values when `map_values` is True. (default: `()`)

-

**map_values** (`bool`) – Boolean flag indicating whether values should be treated as a map. (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives and processes the value list. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

-

**check_get_errors** (`bool`) – Enables error checking after a get operation. (default: `False`)

-

**dynamic** (`bool`) – Indicates whether instances or subclasses may change the property parameters. See `control()` for a usage example. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that transforms the string returned by the instrument before splitting; it returns the transformed string. (default: `None`)

-

**separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None splits on arbitrary whitespace (see `str.split`). (default: `','`)

-

**maxsplit** (`int`) – The device response string is split no more than maxsplit times. -1 means there is no limit. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: A failed cast leaves that element as a string; see `values()`. To permit mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) – Extra keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

 *property *memory_size*: Any*

Set the maximum memory depth.

<size>:={7K,70K,700K,7M} in non-interleaved mode, where one active channel uses each A/D converter. Most oscilloscopes provide two channels per A/D converter.

<size>:={14K,140K,1.4M,14M} in interleave mode, where more than one channel is active on an A/D converter.

 *property *menu*: Any*

Enable or disable the bottom menu, using strict bool handling.

 *property *next_error*: Any*

Read the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until just before read_termination, or read the entire buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Read binary values returned by the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes to read. -1 means read the entire buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 remove_child(*child*)

Detach the child from both the instrument and its associated collection.

Parameters:

**child** (`Child`) – Child instance to remove.

Return type:

`None`

 reset()

Reset the instrument.

 run()

Starts repetitive acquisitions.

Equivalent to pressing the Run key on the front panel.

 *static *setting(*set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the supplied commands. This set-only property can be written, and reading it from the instrument raises an exception.

Parameters:

-

**set_command** (`str`) – String command used to write the value.

-

**docs** (`str`) – Docstring text inserted into the documentation.

-
