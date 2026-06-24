# Keysighte36312A, Keysightn7776C

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Includes coverage for: Keysight E36312A Triple Output Power Supply; Keysight N5776C Power Supply.

## Keysight E36312A Triple Output Power Supply

### Keysight E36312A Triple Output Power Supply

 *class *pymeasure.instruments.keysight.KeysightE36312A(*adapter*, *name='Keysight E36312A'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Defines the Keysight E36312A Power supply interface used to communicate with the instrument.

```python
supply = KeysightE36312A(resource)
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

Parent implementation shared by ChannelCreator and MultiChannelCreator.

Parameters:

-

**cls** ??? Class applied to every child, or a tuple/list giving one class for each child.

-

****kwargs** ??? Keyword arguments supplied to every child.

 *class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Create one channel on the parent class.

At instantiation, the child is attached to the parent instance through `CommonBase.add_child()`. The channel interface uses the attribute name assigned to ChannelCreator in the Instrument class.

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

**cls** (`type`[`Child`]) ??? Channel class used for the channel interface

-

**id** (`Union`[`int`, `str`, `None`]) ??? Instrument channel id, supplied as an integer or string. (default: `None`)

-

****kwargs** ??? Keyword arguments supplied to every child.

 *class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Create multiple channels on the parent class.

At instantiation, the children are attached to the parent instance through `CommonBase.add_child()`. The attribute name, such as `channels`, becomes the child collection. You can choose the attribute prefix. When no stronger reason applies, keep `channels` for the attribute name and use the default `"ch_"` prefix.

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

**cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) ??? Class shared by all children, or a tuple/list with one class per child.

-

**id** (`Union`[`int`, `str`, `None`]) ??? tuple/list containing the instrument channel ids. (default: `None`)

-

**prefix** (`Optional`[`str`]) ??? Collection prefix for attributes; for example, ???ch_??? creates self.ch_A. If prefix evaluates False, the child is placed directly under the variable name. Required when id is a tuple/list. (default: `'ch_'`)

-

****kwargs** ??? Keyword arguments supplied to every child.

 add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Attach a child to this instance, then return its position in the children list.

The created child can be reached through the children dictionary by id or through the generated attribute; for example, the fifth channel of an instrument with id ???F??? can be accessed either way: `instrument.channels["F"] == instrument.ch_F`

Note

Leave the default collection and prefix parameter unchanged unless separate collections of different children must be distinguished, such as analog and digital channel types.

Parameters:

-

**cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) ??? Channel class to instantiate.

-

**id** (`Union`[`int`, `str`, `None`]) ??? Child id as used during communication, for example ???A???. (default: `None`)

-

**collection** (`str`) ??? Collection name for dictionary access to the channel interfaces. (default: `'channels'`)

-

**prefix** (`Optional`[`str`]) ??? When multiple channel interfaces are created, the prefix such as ???ch_??? is added before the channel interface attribute name self.ch_A. If prefix evaluates False, the child is attached directly beneath the collection name. (default: `'ch_'`)

-

**attr_name** (`Optional`[`str`]) ??? For a single channel interface, attr_name supplies the attribute name assigned to that channel interface. (default: `''`)

-

****kwargs** ??? Keyword arguments passed to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) ??? Created child instance.

 ask(*command*, *query_delay=None*)

Send a command to the instrument, then return the response that is read back.

Parameters:

-

**command** (`str`) ??? Command string sent to the instrument.

-

**query_delay** (`Optional`[`float`]) ??? Seconds to wait between write and read operations. (default: `None`)

Returns:

`str` ??? Device response string with read_termination removed.

 binary_values(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument, then return binary data as a numpy array.

Parameters:

-

**command** (`str`) ??? Command sent to the instrument.

-

**query_delay** (`Optional`[`float`]) ??? Seconds to wait between write and read operations. (default: `None`)

-

**kwargs** ??? Arguments forwarded to `read_binary_values()`.

Returns:

NumPy array of values.

 check_errors()

Retrieve every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property get, check for errors and log any results.

Invoked when `check_get_errors=True` is configured for that property.

An override of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set, check for errors and log any results.

Invoked when `check_set_errors=True` is configured for that property.

An override of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property supports synchronization between a controller and a device. The Operation Complete query writes an ASCII character 1 into the device???s Output Queue after all pending selected device operations have completed.

 *static *control(*get_command*, *set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. The resulting property can be written to and read from the instrument. See also `measurement()` and `setting()`.

Parameters:

-

**get_command** (`Optional`[`str`]) ??? String command that requests the value; use None when get is unsupported (see also `setting()`).

-

**set_command** (`Optional`[`str`]) ??? String command that sends the value; use None when set is unsupported (see also `measurement()`).

-

**docs** (`str`) ??? Docstring text included in the documentation

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `TypeVar`(`V2`)]) ??? Function receiving a value plus a set of valid values; it returns a valid value or raises an exception. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f80f0>`)

-

**values** (`TypeVar`(`Vs`)) ??? List, tuple, range, or dictionary of valid values; when `map_values` is True, it may also map values. (default: `()`)

-

**map_values** (`bool`) ??? Boolean flag selecting whether values are treated as a map. (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) ??? Function that receives a value for processing before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f81a0>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) ??? Function that receives the value list and processes it. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8250>`)

-

**set_process** (`Callable`[[`TypeVar`(`V2`)], `Any`]) ??? Function that receives a value for processing before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8300>`)

-

**check_set_errors** (`bool`) ??? Enables or disables error checking after setting. (default: `False`)

-

**check_get_errors** (`bool`) ??? Enables or disables error checking after getting. (default: `False`)

-

**dynamic** (`bool`) ??? Indicates whether property parameters are intended to be changed on instances or subclasses. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) ??? Optional callable that processes the instrument response string before splitting; it returns the processed string. (default: `None`)

-

**separator** (`Optional`[`str`]) ??? Character used to split the device response string into a list. None splits on any whitespace (see `str.split`). (default: `','`)

-

**maxsplit** (`int`) ??? Maximum number of split operations applied to the device response string. -1 (default) means unlimited splitting. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: When casting fails, that element remains a string; see `values()`. To permit mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) ??? Additional keyword arguments for `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

Dynamic parameter usage can follow this pattern:

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

Unexpected side effects from dynamic properties

Users need care with dynamic properties, because defining class and/or instance attributes with particular name patterns can create unwanted side effects. The reserved pattern is property_param, where property names the dynamic property (for example, center_frequency in the example) and param is any parameter name of this method except dynamic and docs (for example, values in the example); those names control dynamic property behavior.

 *static *get_channel_pairs(*cls*)

Return every channel pair defined on the Instrument as a list

 *static *get_channels(*cls*)

Return all ChannelCreator and MultiChannelCreator instances belonging to the Instrument as a list

Return type:

`list`[`tuple`[`str`, [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)]]

 *property *id*: Any*

Read the instrument identification.

 *static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. This measurement quantity is read-only for the instrument and cannot be set.

Parameters:

-

**get_command** (`str`) ??? String command that requests the value

-

**docs** (`str`) ??? Docstring text included in the documentation

-

**values** (`Any`) ??? List, tuple, range, or dictionary of valid values; when `map_values` is True, it may also map values. (default: `()`)

-

**map_values** (`bool`) ??? Boolean flag selecting whether values are treated as a map. (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) ??? Function that receives a value for processing before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) ??? Function that receives the value list and processes it. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

-

**check_get_errors** (`bool`) ??? Enables or disables error checking after getting. (default: `False`)

-

**dynamic** (`bool`) ??? Indicates whether property parameters are intended to be changed on instances or subclasses. See `control()` for a usage example. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) ??? Optional callable that processes the instrument response string before splitting; it returns the processed string. (default: `None`)

-

**separator** (`Optional`[`str`]) ??? Character used to split the device response string into a list. None splits on any whitespace (see `str.split`). (default: `','`)

-

**maxsplit** (`int`) ??? Maximum number of split operations applied to the device response string. -1 (default) means unlimited splitting. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: When casting fails, that element remains a string; see `values()`. To permit mixed types deliberately, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) ??? Additional keyword arguments for `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

 *property *next_error*: Any*

Retrieve the next queued error. To read and log every error, use `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until read_termination is reached, excluding it, or consume the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) ??? Number of bytes requested. A value of -1 means the entire read buffer is read.

-

**kwargs** ??? Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 remove_child(*child*)

Detach the child from both the instrument and the matching collection.

Parameters:

**child** (`Child`) ??? Child instance to delete.

Return type:

`None`

 reset()

Reset the instrument.

 *static *setting(*set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the supplied commands. This property can be set, but reading it from the instrument raises an exception.

Parameters:

-

**set_command** (`str`) ??? String command that writes the value

-

**docs** (`str`) ??? Docstring text included in the documentation

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) ??? Function receiving a value plus a set of valid values; it returns a valid value or raises an exception. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

-

**values** (`TypeVar`(`Vs`)) ??? List, tuple, range, or dictionary of valid values; when `map_values` is True, it may also map values. (default: `()`)

-

**map_values** (`bool`) ??? Boolean flag selecting whether values are treated as a map. (default: `False`)

-

**set_process** (`Callable`[[`Any`], `Any`]) ??? Function that receives a value for processing before value mapping and returns the processed value. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

-

**check_set_errors** (`bool`) ??? Enables or disables error checking after setting. (default: `False`)

-

**dynamic** (`bool`) ??? Indicates whether property parameters are intended to be changed on instances or subclasses. See `control()` for a usage example. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]

 shutdown()

Put the instrument into a safe, stable state

Return type:

`None`

 *property *status*: Any*

Read the status byte together with the Master Summary Status bit.

 values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return the result as a list of formatted values.

Parameters:

-

**command** (`str`) ??? SCPI command sent to the instrument.

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) ??? Optional callable that processes the instrument response string before splitting; it returns the processed string. (default: `None`)

-

**separator** (`Optional`[`str`]) ??? Character used to split the device response string into a list. None splits on any whitespace (see `str.split`). (default: `','`)

-

**maxsplit** (`int`) ??? Maximum number of split operations applied to the device response string. -1 (default) means unlimited splitting. (default: `-1`)

-

**cast** (`Union`[`type`[`TypeVar`(`T`)], `Callable`[[`str`], `TypeVar`(`T`)]]) –

Type used to cast every element from the split string.

Deprecated since version 0.17.0: When casting fails, that element remains a string. A later version will raise an error instead. To permit mixed types deliberately, use a dedicated function, for example `cast_or_str()` as cast function. (default: `<class 'float'>`)

-

****kwargs** ??? Keyword arguments forwarded to the `ask()` method.

Returns:

`list`[`TypeVar`(`T`)] ??? List of the desired type, or, where casting fails, the deprecated str fallback.

 wait_for(*query_delay=None*)

Pause for a specified interval. Used by ???ask??? before the read step.

Parameters:

**query_delay** (`Optional`[`float`]) ??? Seconds to wait between write and read operations. None means the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Parameters:

-

**command** (`str`) ??? command string sent to the instrument

-

**kwargs** ??? Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) ??? Values to transmit.

-

****kwargs** (**args**,*) ??? Additional arguments passed to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Write byte content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.keysight.keysightE36312A.VoltageChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

 *property *current*: Any*

Measure this channel's actual current.

 *property *current_limit*: Any*

Set this channel's current limit; range depends on channel.(dynamic)

 *property *output_enabled*: Any*

Control whether this channel output is enabled (boolean).

 *property *voltage*: Any*

Measure this channel's actual voltage.

 *property *voltage_setpoint*: Any*

Set this channel's output voltage; range depends on channel.(dynamic)

## Keysight N5776C Power Supply

### Keysight N5776C Power Supply

 *class *pymeasure.instruments.keysight.KeysightN7776C(*adapter*, *name='N7776C Tunable Laser Source'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Describes the Keysight N7776C Tunable Laser Source interface.

```python
laser = N7776C(address)
laser.sweep_wl_start = 1550
laser.sweep_wl_stop = 1560
laser.sweep_speed = 1
laser.sweep_mode = 'CONT'
laser.output_enabled = 1
while laser.sweep_state == 1:
    log.info('Sweep in progress.')
laser.output_enabled = 0

```

 close()

Close the instrument connection completely through the adapter connection.

 get_wl_data()

Return the wavelength data stored in the laser's internal memory

 *property *locked*: Any*

Control the laser source lock state (True/False). (bool)

 next_step()

Perform the next stepped-sweep step when the sweep is paused or manual mode is active.

 *property *output_enabled*: Any*

Control the laser source state (on/off). (bool)

 *property *output_power_dBm

Control output power in dBm.

 *property *output_power_mW

Control output power in mW

 previous_step()

Perform one stepped-sweep step backward when it is paused or manual mode is active.

 *property *sweep_mode*: Any*

Control the swept laser source sweep mode

 *property *sweep_points*: Any*

Return the datapoint count that :READout:DATA? will provide.

 *property *sweep_speed*: Any*

Control sweep speed (in nanometers per second).

 *property *sweep_state*: Any*

Control the wavelength sweep state. This stops, starts, pauses, or continues a wavelength sweep. Valid state values are 0 (not running), 1 (running) and 2 (paused). See the N7776C user manual for exact handling of the paused option.

 *property *sweep_step*: Any*

Control sweep step width (in nanometers).

 *property *sweep_twoway*: Any*

Control repeat mode. This applies in stepped,continuous and manual sweep mode.

 *property *sweep_wl_start*: Any*

Control the sweep Start Wavelength (in nanometers).

 *property *sweep_wl_stop*: Any*

Control the sweep End Wavelength (in nanometers).

 *property *trigger_in*: Any*

Control the incoming trigger response, and arm the module.

 *property *trigger_out*: Any*

Control whether an output trigger is generated, and at which point in a sweep cycle, then arm the module.

 *property *wavelength*: Any*

Control the output light absolute wavelength (in nanometers)

 *property *wl_logging*: Any*

Control the lambda logging feature State (on/off) of the laser source.
