# Instruments — Instruments (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Instrument classes

 *class *pymeasure.instruments.common_base.CommonBase(***kwargs*)

Shared superclass used by instruments and channels.

This class provides the machinery used by pymeasure's property factory `control()` and by the related helpers `measurement()` and `setting()`.

 *class *BaseChannelCreator(***kwargs*)

Parent implementation shared by ChannelCreator and MultiChannelCreator.

Parameters:

-

**cls** - Class to use for every child, or a tuple/list that supplies one class per child.

-

****kwargs** - Keyword arguments applied to every child.

 *class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Attach one channel to the parent class.

During instantiation, the child is attached to the parent instance through `CommonBase.add_child()`. The channel interface takes its name from the attribute assigned to ChannelCreator on the Instrument class.

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

**cls** (`type`[`Child`]) - Channel class used for the channel interface.

-

**id** (`Union`[`int`, `str`, `None`]) - Instrument-side channel id, supplied as an integer or string. (default: `None`)

-

****kwargs** - Keyword arguments applied to every child.

 *class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Attach multiple channels to the parent class.

At instantiation time, the children are attached to the parent instance with `CommonBase.add_child()`. The attribute name, for example `channels`, becomes the child collection. A custom attribute prefix can be supplied. Unless there is a specific reason to choose differently, use `channels` for the attribute name and keep the default prefix `"ch_"`.

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

**cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) - Class shared by all children, or a tuple/list containing one class for each child.

-

**id** (`Union`[`int`, `str`, `None`]) - tuple/list containing the instrument channel ids. (default: `None`)

-

**prefix** (`Optional`[`str`]) - Attribute collection prefix; for example, "ch_" creates self.ch_A. If prefix evaluates False, the child is placed directly under the variable name. Required when id is a tuple/list. (default: `'ch_'`)

-

****kwargs** - Keyword arguments applied to every child.

 add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Create a child on this instance and return its position in the children list.

After creation, the child can be reached through its id in the children dictionary or through the generated attribute; for example, the fifth channel with id "F" can be accessed as `instrument.channels["F"] == instrument.ch_F`.

Note

Keep the default collection and prefix unless separate child collections must be distinguished, such as analog and digital channel types.

Parameters:

-

**cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) - Class used for the channel.

-

**id** (`Union`[`int`, `str`, `None`]) - Communication id for the child, such as "A". (default: `None`)

-

**collection** (`str`) - Child collection name used for dictionary-style access to channel interfaces. (default: `'channels'`)

-

**prefix** (`Optional`[`str`]) - Prefix placed before the channel interface attribute name when creating several channel interfaces, such as "ch_" in self.ch_A. If prefix evaluates False, the child is attached directly below the collection name. (default: `'ch_'`)

-

**attr_name** (`Optional`[`str`]) - For a single channel interface, attr_name supplies the attribute name used for that interface. (default: `''`)

-

****kwargs** - Keyword arguments passed to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) - Newly created child instance.

 ask(*command*, *query_delay=None*)

Send a command to the instrument, then return the response read back.

Parameters:

-

**command** (`str`) - Command string sent to the instrument.

-

**query_delay** (`Optional`[`float`]) - Seconds to wait between the write and read operations. (default: `None`)

Returns:

`str` - Device reply string with read_termination removed.

 binary_values(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument and return the binary reply as a numpy array.

Parameters:

-

**command** (`str`) - Command sent to the instrument.

-

**query_delay** (`Optional`[`float`]) - Seconds to wait between the write and read operations. (default: `None`)

-

**kwargs** - Arguments forwarded to `read_binary_values()`.

Returns:

NumPy array of values.

 check_errors()

Retrieve every instrument error and write the results to the log.

Returns:

`list` – List of error entries.

 check_get_errors()

After reading a property, inspect and log instrument errors.

This runs when `check_get_errors=True` is configured on that property.

An overriding implementation may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After writing a property, inspect and log instrument errors.

This runs when `check_set_errors=True` is configured on that property.

An overriding implementation may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 *static *control(*get_command*, *set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the provided commands. The resulting property can be written to and read from the instrument. See also `measurement()` and `setting()`.

Parameters:

-

**get_command** (`Optional`[`str`]) - String command used to request the value; use None when getting is unsupported (see also `setting()`).

-

**set_command** (`Optional`[`str`]) - String command used to write the value; use None when setting is unsupported (see also `measurement()`).

-

**docs** (`str`) - Docstring text added to the generated documentation.

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `TypeVar`(`V2`)]) - Function that receives a value plus the valid-values group and returns an accepted value, or raises an exception otherwise. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f80f0>`)

-

**values** (`TypeVar`(`Vs`)) - Valid-value collection, such as a list, tuple, range, or dictionary; it can also provide mappings when `map_values` is True. (default: `()`)

-

**map_values** (`bool`) - Boolean switch indicating whether values should be handled as a mapping. (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) - Function that receives a value, processes it before value mapping, and returns the processed result. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f81a0>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) - Function that receives and processes the value list. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8250>`)

-

**set_process** (`Callable`[[`TypeVar`(`V2`)], `Any`]) - Function that accepts a value, processes it before value mapping, and returns the processed result. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8300>`)

-

**check_set_errors** (`bool`) - Enables or disables error checks after setting. (default: `False`)

-

**check_get_errors** (`bool`) - Enables or disables error checks after getting. (default: `False`)

-

**dynamic** (`bool`) - Controls whether property parameters are intended to vary on instances or subclasses. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable that transforms the instrument reply string before it is split. It returns the transformed string. (default: `None`)

-

**separator** (`Optional`[`str`]) - Separator character used to divide the returned device string into a list. None uses whitespace splitting; see `str.split`. (default: `','`)

-

**maxsplit** (`int`) - Maximum number of splits applied to the device return string. -1, the default, means unlimited splitting. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every item from the split string.

Deprecated since version 0.17.0: When casting is unsuccessful, that element remains a string; see `values()`. To intentionally permit mixed types, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) - Additional keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

A dynamic parameter can be used as shown here:

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

Surprising behavior that can occur with dynamic properties

Use care with dynamic properties because class or instance attributes whose names match reserved patterns can cause unintended behavior. The reserved pattern is property_param, where property is the dynamic property's name, such as center_frequency in the example, and param is any parameter name for this method except dynamic and docs, such as values in the example.

 *static *get_channel_pairs(*cls*)

Return every channel pair defined on the Instrument as a list.

 *static *get_channels(*cls*)

Return a list containing every ChannelCreator and MultiChannelCreator instance on the Instrument.

Return type:

`list`[`tuple`[`str`, `BaseChannelCreator`]]

 *static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the provided commands. This measurement quantity can be read from the instrument only and cannot be set.

Parameters:

-

**get_command** (`str`) - String command that requests the value.

-

**docs** (`str`) - Docstring text added to the generated documentation.

-

**values** (`Any`) - Valid-value collection, such as a list, tuple, range, or dictionary; it can also provide mappings when `map_values` is True. (default: `()`)

-

**map_values** (`bool`) - Boolean switch indicating whether values should be handled as a mapping. (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) - Function that receives a value, processes it before value mapping, and returns the processed result. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) - Function that receives and processes the value list. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

-

**check_get_errors** (`bool`) - Enables or disables error checks after getting. (default: `False`)

-

**dynamic** (`bool`) - Controls whether property parameters are intended to vary on instances or subclasses. See `control()` for an usage example. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable that transforms the instrument reply string before it is split. It returns the transformed string. (default: `None`)

-

**separator** (`Optional`[`str`]) - Separator character used to divide the returned device string into a list. None uses whitespace splitting; see `str.split`. (default: `','`)

-

**maxsplit** (`int`) - Maximum number of splits applied to the device return string. -1, the default, means unlimited splitting. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every item from the split string.

Deprecated since version 0.17.0: When casting is unsuccessful, that element remains a string; see `values()`. To intentionally permit mixed types, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) - Additional keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

 remove_child(*child*)

Delete the child from both the instrument and its related collection.

Parameters:

**child** (`Child`) - Child instance to remove.

Return type:

`None`

 *static *setting(*set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the provided commands. The resulting property is write-only and raises an exception if read from the instrument.

Parameters:

-

**set_command** (`str`) - String command that writes the value.

-

**docs** (`str`) - Docstring text added to the generated documentation.

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) - Function that receives a value plus the valid-values group and returns an accepted value, or raises an exception otherwise. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

-

**values** (`TypeVar`(`Vs`)) - Valid-value collection, such as a list, tuple, range, or dictionary; it can also provide mappings when `map_values` is True. (default: `()`)

-

**map_values** (`bool`) - Boolean switch indicating whether values should be handled as a mapping. (default: `False`)

-

**set_process** (`Callable`[[`Any`], `Any`]) - Function that receives a value, processes it before value mapping, and returns the processed result. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

-

**check_set_errors** (`bool`) - Enables or disables error checks after setting. (default: `False`)

-

**dynamic** (`bool`) - Controls whether property parameters are intended to vary on instances or subclasses. See `control()` for an usage example. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]

 values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return formatted values parsed from the reply.

Parameters:

-

**command** (`str`) - SCPI command sent to the instrument.

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) - Optional callable that transforms the instrument reply string before it is split. It returns the transformed string. (default: `None`)

-

**separator** (`Optional`[`str`]) - Separator character used to divide the returned device string into a list. None uses whitespace splitting; see `str.split`. (default: `','`)

-

**maxsplit** (`int`) - Maximum number of splits applied to the device return string. -1, the default, means unlimited splitting. (default: `-1`)

-

**cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every item from the split string.

Deprecated since version 0.17.0: When casting is unsuccessful, that element remains a string. A later release will raise an error for that situation. To intentionally permit mixed types, provide a dedicated function, such as `cast_or_str()` as cast function. (default: `<class 'float'>`)

-

****kwargs** - Keyword arguments passed through to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] - List containing the requested type, or, in deprecated behavior, str entries where casting fails.

 wait_for(*query_delay=None*)

Pause for a period of time. `ask` uses this wait before reading.

Implement in subclass!

Parameters:

**query_delay** (`Optional`[`float`]) - Seconds to wait between writing and reading. None selects the default delay. (default: `None`)

Return type:

`None`

 *class *pymeasure.instruments.Instrument(*adapter*, *name*, *includeSCPI=None*, ***kwargs*)

Superclass used for every Instrument definition.

Communication with the connected hardware device is handled through one of the [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) classes. That separation keeps the instrument and command definitions independent from the communication interface selected.

If `adapter` is a string, it is interpreted as a suitable resource name. Depending on the installed VISA library, the value may be a simple name like `COM1` or `ASRL2`, or a more complex [VISA resource name](https://pyvisa.readthedocs.io/en/latest/introduction/names.html) that identifies the connection target.

If `adapter` is an integer, it is converted into a GPIB resource name. For both string and integer inputs, a [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) is created from that resource name. Keyword arguments may further configure the connection.

For any other input, the supplied [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) object is used directly and keyword arguments are ignored.

By default, this class includes basic SCPI commands. Instruments that do not support the standard SCPI commands can turn that behavior off with `includeSCPI`.

Parameters:

-

**adapter** (`Union`[[`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter), `int`, `str`]) - String, integer, or [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) subclass object.

-

**name** (*string*) - Instrument name, often defaulting to the model designation.

-

**includeSCPI** (`Optional`[`bool`]) –

Required boolean controlling whether standard SCPI commands are included.

Deprecated since version 0.14: When this is True, inherit from [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin) instead. (default: `None`)

-

****kwargs** - When `adapter` is a string or integer, additional arguments are forwarded to [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter); see that class for details. They are discarded for other adapter forms.

 check_errors()

Retrieve every instrument error and write the results to the log.

Returns:

`list` – List of error entries.

 check_get_errors()

After reading a property, inspect and log instrument errors.

This runs when `check_get_errors=True` is configured on that property.

An overriding implementation may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After writing a property, inspect and log instrument errors.

This runs when `check_set_errors=True` is configured on that property.

An overriding implementation may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clears the instrument status byte

Return type:

`None`

 *property *complete

Get the synchronization bit.

This property synchronizes a controller with a device. The Operation Complete query puts ASCII character 1 into the device's Output Queue after all pending selected device operations have completed.

 *property *id

Return the instrument identification.

 *property *next_error

Return the instrument's next error as a tuple containing code and message.

 *property *options

Get the device options installed.

 read(***kwargs*)

Read until read_termination, excluding it, or read the complete buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Read binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) - Number of bytes to read. A value of -1 requests the entire read buffer.

-

**kwargs** - Keyword arguments passed to the adapter.

Returns bytes:

Instrument bytes response, including termination.

Return type:

`bytes`

 reset()

Resets the instrument.

Return type:

`None`

 shutdown()

Place the instrument into a safe, stable state.

Return type:

`None`

 *property *status

Return the status byte together with the Master Summary Status bit.

 wait_for(*query_delay=None*)

Pause for a period of time. `ask` uses this wait before reading.

Parameters:

**query_delay** (`Optional`[`float`]) - Seconds to wait between writing and reading. None selects the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) - command string sent to the instrument.

-

**kwargs** - Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) - Values that will be transmitted.

-

****kwargs** (**args**,*) - Additional arguments passed along to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.Channel(*parent*, *id*, ***kwargs*)

Superclass used for channel definitions.

This class supports dynamic properties in the same style as `Instrument`, but it needs an `Instrument` instance as its communication parent.

`insert_id()` modifies an outgoing command by adding the channel id. By default, it substitutes the Channel placeholder, default "ch", across command strings such as "CHANnel{ch}:foo".

Parameters:

-

**parent** (`CommonBase`) - Instrument instance, specifically an `Instrument`, that owns the channel.

-

**id** (`Union`[`int`, `str`, `None`]) - Channel identifier as used during communication.

 check_errors()

Retrieve every instrument error and write the results to the log.

Returns:

`list` – List of error entries.

 check_get_errors()

After reading a property, inspect and log instrument errors.

This runs when `check_get_errors=True` is configured on that property.

An overriding implementation may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After writing a property, inspect and log instrument errors.

This runs when `check_set_errors=True` is configured on that property.

An overriding implementation may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 insert_id(*command*)

Insert the channel id into a command by replacing the placeholder.

Override this method for different behavior, such as always prepending the channel id.

Return type:

`str`

 read(***kwargs*)

Read until read_termination, excluding it, or read the complete buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Read binary values from the instrument.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) - Number of bytes to read. A value of -1 requests the entire read buffer.

-

**kwargs** - Keyword arguments passed to the adapter.

Returns bytes:
