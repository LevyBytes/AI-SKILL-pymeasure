# Keysighte3631A, Keysightn5767A

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: APIs for Keysight E3631A Triple Output Power Supply; Keysight N5767A Power Supply.

## Keysight E3631A Triple Output Power Supply

### Keysight E3631A Triple Output Power Supply

 *class *pymeasure.instruments.keysight.KeysightE3631A(*adapter*, *name='Keysight E3631A'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Interface wrapper for controlling and querying a Keysight E3631A Triple Output DC Power Supply.

```python
supply = KeysightE3631A(resource)
supply.ch_1.voltage_setpoint=10
supply.ch_1.current_setpoint=0.1
supply.ch_1.output_enabled=True
print(supply.ch_1.voltage)

```

 ch_1

Channel:

`VoltageChannel`

 ch_2

Channel:

`VoltageChannel`

 ch_3

Channel:

`VoltageChannel`

 *class *BaseChannelCreator(***kwargs*)

Bases: `object`

Shared base used by ChannelCreator and MultiChannelCreator.

Parameters:

-

**cls** – Child class applied to every child, or a tuple/list giving one class per child.

-

****kwargs** – Keyword arguments supplied to every child.

 *class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach one channel to the parent class.

At instantiation, `CommonBase.add_child()` attaches the child to the parent instance. The Instrument class attribute that received ChannelCreator becomes the channel interface name.

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

**cls** (`type`[`Child`]) – Channel class used for the channel interface

-

**id** (`Union`[`int`, `str`, `None`]) – Instrument channel id as an integer or string. (default: `None`)

-

****kwargs** – Keyword arguments supplied to every child.

 *class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach multiple channels to the parent class.

At instantiation, `CommonBase.add_child()` attaches the children to the parent instance. The attribute name (e.g. `channels`) becomes the child collection. You can set an attribute prefix; unless another design requires it, name the attribute `channels` and keep the default prefix `"ch_"`.

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

**cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) – Child class shared by all children, or a tuple/list containing one class for each child.

-

**id** (`Union`[`int`, `str`, `None`]) – Tuple/list of instrument channel ids. (default: `None`)

-

**prefix** (`Optional`[`str`]) – Prefix used when creating collection attributes; for example, “ch_” creates attribute self.ch_A. If prefix evaluates False, the child is attached directly under the variable name. Required if id is tuple/list. (default: `'ch_'`)

-

****kwargs** – Keyword arguments supplied to every child.

 add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Create a child on this instance, then return its position in the children list.

The created child can be reached through its id in the children dictionary or through the generated attribute; for example, the fifth channel of instrument with id “F” can be checked with `instrument.channels["F"] == instrument.ch_F`

Note

Keep the default collection and prefix parameter unless separate child collections must be distinguished, such as analog and digital channel types.

Parameters:

-

**cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) – Channel class.

-

**id** (`Union`[`int`, `str`, `None`]) – Child id used during communication, e.g. “A”. (default: `None`)

-

**collection** (`str`) – Child collection name used for dictionary access to channel interfaces. (default: `'channels'`)

-

**prefix** (`Optional`[`str`]) – Prefix for multiple channel interfaces; for example, “ch_” is placed before the channel interface attribute name self.ch_A. If prefix evaluates False, the child is attached directly under the collection name. (default: `'ch_'`)

-

**attr_name** (`Optional`[`str`]) – When creating one channel interface, attr_name supplies the attribute name assigned to that channel interface. (default: `''`)

-

****kwargs** – Keyword arguments passed to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) – Created child instance.

 ask(*command*, *query_delay=None*)

Send a command to the instrument, then return the response that is read back.

Parameters:

-

**command** (`str`) – Command string sent to the instrument.

-

**query_delay** (`Optional`[`float`]) – Seconds to wait between the write and read operations. (default: `None`)

Returns:

`str` – Device response string with read_termination removed.

 binary_values(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument and receive binary data as a numpy array.

Parameters:

-

**command** (`str`) – Command sent to the instrument.

-

**query_delay** (`Optional`[`float`]) – Seconds to wait between the write and read operations. (default: `None`)

-

**kwargs** – Arguments forwarded to `read_binary_values()`.

Returns:

NumPy array of values.

 check_errors()

Read every queued error from the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property get, inspect errors and log them.

Invoked when that property has `check_get_errors=True`.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set, inspect errors and log them.

Invoked when that property has `check_set_errors=True`.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property lets a controller synchronize with a device. When pending selected device operations are done, the Operation Complete query puts ASCII character 1 into the device's Output Queue.

 *static *control(*get_command*, *set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. The property supports both instrument reads and writes. See also `measurement()` and `setting()`.

Parameters:

-

**get_command** (`Optional`[`str`]) – String command used to request the value; use None when get is unsupported (see also `setting()`).

-

**set_command** (`Optional`[`str`]) – String command used to write the value; use None when set is unsupported (see also `measurement()`).

-

**docs** (`str`) – Docstring text inserted into the documentation

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `TypeVar`(`V2`)]) – Function receiving a value and the valid-value group; it returns a valid value or raises an exception. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f80f0>`)

-

**values** (`TypeVar`(`Vs`)) – Valid values as a list, tuple, range, or dictionary; when `map_values` is True, these can be used for value mapping. (default: `()`)

-

**map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f81a0>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives the value list and returns it after processing. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8250>`)

-

**set_process** (`Callable`[[`TypeVar`(`V2`)], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8300>`)

-

**check_set_errors** (`bool`) – Enables or disables error checks after setting (default: `False`)

-

**check_get_errors** (`bool`) – Enables or disables error checks after getting (default: `False`)

-

**dynamic** (`bool`) – Indicates whether property parameters are intended to be changed on instances or subclasses. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that handles the instrument response string before splitting; it returns the processed string. (default: `None`)

-

**separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None means split on any whitespace (see `str.split`). (default: `','`)

-

**maxsplit** (`int`) – Maximum number of times to split the device response string. -1 (default) means unlimited splitting. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: If a cast fails, that element remains a string; see `values()`. To allow mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) – Additional keyword arguments for `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

A dynamic parameter can be used like this:

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

Surprising side effects from dynamic properties

Use dynamic properties carefully: class or instance attributes whose names match reserved patterns can trigger unintended behavior. The pattern property_param is reserved for dynamic property control, where property is the dynamic property name (for example, center_frequency) and param is one of this method parameter names other than dynamic and docs (for example, values).

 *static *get_channel_pairs(*cls*)

Return all channel pairs for the Instrument as a list

 *static *get_channels(*cls*)

Return every ChannelCreator and MultiChannelCreator instance registered on the Instrument as a list

Return type:

`list`[`tuple`[`str`, [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)]]

 *property *id*: Any*

Retrieve the instrument identification string.

 *static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands for a measurement quantity. It can be read from the instrument only and cannot be set.

Parameters:

-

**get_command** (`str`) – String command used to request the value

-

**docs** (`str`) – Docstring text inserted into the documentation

-

**values** (`Any`) – Valid values as a list, tuple, range, or dictionary; when `map_values` is True, these can be used for value mapping. (default: `()`)

-

**map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives the value list and returns it after processing. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

-

**check_get_errors** (`bool`) – Enables or disables error checks after getting (default: `False`)

-

**dynamic** (`bool`) – Indicates whether property parameters are intended to change on instances or subclasses. See `control()` for a usage example. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that handles the instrument response string before splitting; it returns the processed string. (default: `None`)

-

**separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None means split on any whitespace (see `str.split`). (default: `','`)

-

**maxsplit** (`int`) – Maximum number of times to split the device response string. -1 (default) means unlimited splitting. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: If a cast fails, that element remains a string; see `values()`. To allow mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) – Additional keyword arguments for `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *output_enabled*: Any*

Enable or disable the output of the most recently used channel (boolean).(dynamic)

 read(***kwargs*)

Read until read_termination is reached, excluding it, or read the complete buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes requested. A value of -1 means read the complete buffer.

-

**kwargs** – Keyword arguments forwarded to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 remove_child(*child*)

Delete the child from the instrument and from its associated collection.

Parameters:

**child** (`Child`) – Child instance to remove.

Return type:

`None`

 reset()

Reset the instrument.

 *static *setting(*set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the supplied commands. The property can be set, but reading it from the instrument raises an exception.

Parameters:

-

**set_command** (`str`) – String command used to write the value

-

**docs** (`str`) – Docstring text inserted into the documentation

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) – Function receiving a value and the valid-value group; it returns a valid value or raises an exception. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

-

**values** (`TypeVar`(`Vs`)) – Valid values as a list, tuple, range, or dictionary; when `map_values` is True, these can be used for value mapping. (default: `()`)

-

**map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

-

**set_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

-

**check_set_errors** (`bool`) – Enables or disables error checks after setting (default: `False`)

-

**dynamic** (`bool`) – Indicates whether property parameters are intended to change on instances or subclasses. See `control()` for a usage example. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]

 shutdown()

Put the instrument into a safe, stable state

Return type:

`None`

 *property *status*: Any*

Retrieve the status byte and the Master Summary Status bit.

 *property *tracking_enabled*: Any*

Enable or disable track mode on the power supply (boolean)

 values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return the result as a list of formatted values.

Parameters:

-

**command** (`str`) – SCPI command sent to the instrument.

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that handles the instrument response string before splitting; it returns the processed string. (default: `None`)

-

**separator** (`Optional`[`str`]) – Character used to split the device response string into a list. None means split on any whitespace (see `str.split`). (default: `','`)

-

**maxsplit** (`int`) – Maximum number of times to split the device response string. -1 (default) means unlimited splitting. (default: `-1`)

-

**cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: If a cast fails, the element remains a string. A future version will raise an error instead. To allow mixed types deliberately, use a dedicated function such as `cast_or_str()` as cast function. (default: `<class 'float'>`)

-

****kwargs** – Keyword arguments forwarded to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] – A list containing the desired type; deprecated behavior allows str elements where casting fails.

 wait_for(*query_delay=None*)

Wait for a duration; ‘ask’ uses this pause before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Write a string command to the instrument and append write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Keyword arguments forwarded to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

-

****kwargs** (**args**,*) – Extra arguments forwarded to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.keysight.keysightE3631A.VoltageChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Power supply base class channel implementation

 *property *current*: Any*

Measure this channel's actual current.

 *property *current_limit*: Any*

Set or query this channel's current limit; the valid range depends on channel.(dynamic)

 *property *output_enabled*: Any*

Enable or disable the channel output (boolean).

 *property *voltage*: Any*

Measure this channel's actual voltage.

 *property *voltage_setpoint*: Any*

Set or query this channel's output voltage; the valid range depends on channel.(dynamic)

## Keysight N5767A Power Supply

### Keysight N5767A Power Supply

 *class *pymeasure.instruments.keysight.KeysightN5767A(*adapter*, *name='Keysight N5767A power supply'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Interface wrapper for instrument interaction with the Keysight N5767A Power supply.

 *property *current*: Any*

Get current in Amps.

 *property *current_range*: Any*

Set or query the DC current range in Amps; accepted values run from 0 to 25 A. Setting this property disables Auto-range. (float)

 disable()

Disables the flow of current.

 enable()

Enables the flow of current.

 is_enabled()

Return True when the current supply is enabled.

 *property *voltage*: Any*

Read the DC voltage measurement in Volts.

 *property *voltage_range*: Any*

Set or query the DC voltage range in Volts; accepted values run from 0 to 60 V. Setting this property disables Auto-range.
