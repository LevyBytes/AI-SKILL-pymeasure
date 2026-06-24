# Keysight81160A (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Keysight 81160A Pulse Function Arbitrary Noise Generator

Class constructor: pymeasure.instruments.keysight.Keysight81160A(adapter, **kwargs).
Default name: 'Agilent 33500 Function/Arbitrary Waveform generator family'.

Bases: [`Agilent33500`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33500.html#pymeasure.instruments.agilent.Agilent33500)

Provide a high-level Python interface for controlling and querying the Keysight 81160A instrument.

```python
generator = Keysight81160A("GPIB::1")        # Replace with your device address
generator.reset()                            # Reset the generator to default settings

generator.shape = "SIN"                      # Set default channel output shape to sine
generator.channels[1].shape = "SIN"          # Set channel 1 output signal shape to sine
generator.frequency = 1e3                    # Set default channel output frequency to 1 kHz
generator.channels[1].frequency = 1e3        # Set channel 1 output frequency to 1 kHz
generator.channels[2].amplitude = 5          # Set channel 2 output amplitude to 5 Vpp
generator.channels[2].offset = 0.5           # Set channel 2 output offset to 0.5 V
generator.channels[2].output = True          # Enable channel 2 output

# Output a square wave at 1 kHz with 5 Vpp and 0.5 V offset
generator.channels[2].apply_square(1e3, 5, 0)

ch1 = generator.channels[1]                  # Short form for channel 1
waveform = [-2.0, -1.5, 0.0, 1.5, 2.0]       # Define a user-defined waveform in Volts
ch1.waveform_volatile = waveform             # Set user-defined waveform to volatile memory
print(f"{ch1.free_memory_slots} slots free") # Get number of slots in non-volatile memory
ch1.save_waveform(waveform, "test")          # Save the waveform to non-volatile memory
ch1.shape = "USER"                           # Set channel 1 shape to user-defined
ch1.trigger_mode = "MAN"                     # Set trigger mode to manual
ch1.trigger_count = 2                        # Set number of cycles to be generated to 2
ch1.output = True                            # Enable channel 1 output
generator.trigger()                          # Trigger the generator to output the waveform
ch1.delete_waveform("test")                  # Delete the waveform from non-volatile memory

```

 ch_1

Channel:

`Keysight81160AChannel`

 ch_2

Channel:

`Keysight81160AChannel`

 *class *BaseChannelCreator(***kwargs*)

Bases: `object`

Shared parent implementation used by ChannelCreator and MultiChannelCreator.

Parameters:

-

**cls** – Child class to use for every child, or a tuple/list that supplies one class per child.

-

****kwargs** – Keyword arguments passed through to every child.

 *class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach one channel to the parent class.

When the parent instance is created, `CommonBase.add_child()` attaches the child. The attribute that holds the ChannelCreator inside the Instrument class becomes the channel interface name.

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

**id** (`Union`[`int`, `str`, `None`]) – Instrument-side channel id, supplied as an integer or string. (default: `None`)

-

****kwargs** – Keyword arguments passed through to every child.

 *class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach multiple channels to the parent class.

During parent instantiation, `CommonBase.add_child()` creates each child. The assigned attribute name, such as `channels`, becomes the child collection. A custom attribute prefix can be supplied. In normal cases, choose `channels` for the attribute and keep the default prefix `"ch_"`.

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

**cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) – One class used for every child, or a tuple/list giving a separate class for each child.

-

**id** (`Union`[`int`, `str`, `None`]) – tuple/list containing the instrument channel ids. (default: `None`)

-

**prefix** (`Optional`[`str`]) – Attribute collection prefix; for example, “ch_” produces self.ch_A. If prefix evaluates False, the child is placed directly below the variable name. Required if id is tuple/list. (default: `'ch_'`)

-

****kwargs** – Keyword arguments passed through to every child.

 add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Create a child on this instance, then return that child's position in the children list.

The created child can be reached through the children dictionary by id or through the generated attribute. Example: a fifth channel with id “F” may be addressed both ways: `instrument.channels["F"] == instrument.ch_F`

Note

Keep the default collection and prefix values unless separate child collections must be identified, for example different channel types (analog and digital).

Parameters:

-

**cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) – Channel class to instantiate.

-

**id** (`Union`[`int`, `str`, `None`]) – Communication id used for the child, for example “A”. (default: `None`)

-

**collection** (`str`) – Child collection name used for dictionary access to channel interfaces. (default: `'channels'`)

-

**prefix** (`Optional`[`str`]) – Prefix used when generating several channel interface attributes; for example, “ch_” is put before the channel attribute name self.ch_A. If prefix evaluates False, the child is attached directly under the collection name. (default: `'ch_'`)

-

**attr_name** (`Optional`[`str`]) – For a single channel interface, attr_name supplies the attribute name assigned to that channel interface. (default: `''`)

-

****kwargs** – Keyword arguments provided to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) – Created child instance.

 *property *amplitude*: Any*

Set or read voltage amplitude in Volts (float).(dynamic)

 *property *amplitude_unit*: Any*

Select amplitude units (string, strictly ‘VPP’, ‘VRMS’, or ‘DBM’).(dynamic)

 *property *arb_advance*: Any*

Choose point-to-point advancement behavior for the device (str). Accepted settings are ‘TRIG<GER>’ or ‘SRAT<E>’ (default).

 *property *arb_file*: Any*

Select the arbitrary signal held in the device volatile memory.(dynamic)

 *property *arb_filter*: Any*

Configure the arbitrary-signal filter setting (str). Accepted values are ‘NORM<AL>’, ‘STEP’ and ‘OFF’.

 *property *arb_srate*: Any*

Set or read the selected arbitrary signal sample rate in Sa/s (float). Valid entries span 1 µSa/s to 250 MSa/s (maximum range, device-dependent).

 ask(*command*, *query_delay=None*)

Send a command to the instrument, then read and return its response.

Parameters:

-

**command** (`str`) – Command string sent to the instrument.

-

**query_delay** (`Optional`[`float`]) – Seconds to wait between the write operation and the read operation. (default: `None`)

Returns:

`str` – Device response string with read_termination removed.

 beep()

Causes a system beep.

 binary_values(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument and return binary data as a numpy array.

Parameters:

-

**command** (`str`) – Command sent to the instrument.

-

**query_delay** (`Optional`[`float`]) – Seconds to wait between the write operation and the read operation. (default: `None`)

-

**kwargs** – Arguments forwarded to `read_binary_values()`.

Returns:

NumPy array of values.

 *property *burst_mode*: Any*

Set or read burst mode type (str, strictly ‘TRIG<GERED>’ or ‘GAT<ED>’).(dynamic)

 *property *burst_ncycles*: Any*

Set or read the cycle count emitted after a burst trigger (int).(dynamic)

 *property *burst_period*: Any*

Set or read the time between successive bursts in seconds (float).(dynamic)

 *property *burst_state*: Any*

Enable or disable burst mode (bool).(dynamic)

 check_errors()

Read every error currently reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property get operation, check for instrument errors and log any findings.

Invoked for a property when `check_get_errors=True` is configured.

Override this method if selected errors should raise an Exception.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set operation, check for instrument errors and log any findings.

Invoked for a property when `check_set_errors=True` is configured.

Override this method if selected errors should raise an Exception.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 clear_display()

Clear a text message from the display.

 *property *complete*: Any*

Get the synchronization bit.

This property supports controller-device synchronization. An Operation Complete query puts ASCII character 1 into the device's Output Queue after every pending selected device operation has completed.

 *static *control(*get_command*, *set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the provided commands. The resulting property supports both instrument reads and writes. See also `measurement()` and `setting()`.

Parameters:

-

**get_command** (`Optional`[`str`]) – String command used to request the value; use None when reading is unsupported (see also `setting()`).

-

**set_command** (`Optional`[`str`]) – String command used to write the value; use None when setting is unsupported (see also `measurement()`).

-

**docs** (`str`) – Docstring text inserted into the documentation

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `TypeVar`(`V2`)]) – Function that receives a value plus valid values and returns an accepted value; otherwise it raises an exception (default: `<function CommonBase.<lambda> at 0x7aa5aa7f80f0>`)

-

**values** (`TypeVar`(`Vs`)) – Valid values supplied as a list, tuple, range, or dictionary; when `map_values` is True this may also map values. (default: `()`)

-

**map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value, can transform it before value mapping, and returns the transformed value (default: `<function CommonBase.<lambda> at 0x7aa5aa7f81a0>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives the value list and returns its processed form. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8250>`)

-

**set_process** (`Callable`[[`TypeVar`(`V2`)], `Any`]) – Function that receives a value, may transform it before value mapping, and returns the processed result (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8300>`)

-

**check_set_errors** (`bool`) – Enables error checks after setting a value (default: `False`)

-

**check_get_errors** (`bool`) – Enables error checks after retrieving a value (default: `False`)

-

**dynamic** (`bool`) – Indicates whether property parameters are intended to be changed on instances or subclasses. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that transforms the instrument reply string before it is split. It returns that transformed string. (default: `None`)

-

**separator** (`Optional`[`str`]) – Separator character used to split the device response string into a list. None means split on whitespace as in `str.split`. (default: `','`)

-

**maxsplit** (`int`) – Maximum number of splits to apply to the device response string. The default -1 means unlimited splitting. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast each value produced by splitting the string.

Deprecated since version 0.17.0: When a cast fails, that element remains a string; see `values()`. To permit mixed types explicitly, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) – Additional keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

A dynamic parameter usage example follows:

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

Use care with dynamic properties: defining class or instance attributes that match particular patterns can create unintended behavior. The reserved pattern is property_param, where property is the dynamic property name (for example center_frequency in the example) and param is any parameter name accepted by this method except dynamic and docs (for example values in the example). Those names are reserved for controlling dynamic properties.

 data_arb(*arb_name*, *data_points*, *data_format='DAC'*)

Upload an arbitrary trace into the device volatile memory.

data_points may be supplied as comma separated 16 bit DAC values, comma separated floating point values, or a binary data stream. DAC entries range from -32767 to +32767. Floating point entries range from -1.0 to +1.0. See the manual for details. Storage is device-type dependent and ranges from 8 Sa to 16 MSa (maximum).

Parameters:

-

**arb_name** – Trace name stored in volatile memory. Use this name when accessing the trace.

-

**data_points** – Individual trace samples. The format parameter selects the representation. format = ‘DAC’ (default): accepts a list of integer values from -32767 to +32767, with at least 8 and no more than 65536 points. format = ‘float’: accepts floating point list entries from -1.0 to +1.0, with at least 8 and no more than 65536 points. format = ‘binary’: accepts 8 bit data supplied as a binary stream.

-

**data_format** – Specifies the data_points representation. Allowed values are ‘DAC’ (default), ‘float’ or ‘binary’. See the data_points parameter documentation above. (default: `'DAC'`)

 data_volatile_clear()

Remove all arbitrary signals from volatile memory.

Use this when repeatedly loading different arbitrary signals under the same name, because loading a trace whose name already exists in memory will produce an error.

 *property *display*: Any*

Set the front-panel display text on the device (string).

 *property *ext_trig_out*: Any*

Enable or disable the trigger out signal (bool).

 *property *frequency*: Any*

Set or read waveform frequency in Hz (float). The chosen shape determines the valid behavior.(dynamic)

 *static *get_channel_pairs(*cls*)

Return a list containing all Instrument channel pairs

 *static *get_channels(*cls*)

Return a list containing all Instrument ChannelCreator and MultiChannelCreator instances

Return type:

`list`[`tuple`[`str`, [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)]]

 *property *id*: Any*

Read the instrument identification string.

 *static *measurement(*get_command*, *docs*, *values=()*, *map_values=False*, *get_process=<function CommonBase.<lambda>>*, *get_process_list=<function CommonBase.<lambda>>*, *check_get_errors=False*, *dynamic=False*, *preprocess_reply=None*, *separator='*, *'*, *maxsplit=-1*, *cast=<class 'float'>*, *values_kwargs=None*)

Create a class property from the supplied commands. This measurement quantity is read-only from the instrument and cannot be set.

Parameters:

-

**get_command** (`str`) – String command that requests the value

-

**docs** (`str`) – Docstring text inserted into the documentation

-

**values** (`Any`) – Valid values supplied as a list, tuple, range, or dictionary; when `map_values` is True this may also map values. (default: `()`)

-

**map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

-

**get_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value, can transform it before value mapping, and returns the transformed value (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8510>`)

-

**get_process_list** (`Callable`[[`list`[`Any`]], `Any`]) – Function that receives the value list and returns its processed form. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f85c0>`)

-

**check_get_errors** (`bool`) – Enables error checks after retrieving a value (default: `False`)

-

**dynamic** (`bool`) – Indicates whether property parameters are intended to be changed on instances or subclasses. See `control()` for a usage example. (default: `False`)

-

**preprocess_reply** (`Optional`[`Callable`[[`str`], `str`]]) – Optional callable that transforms the instrument reply string before it is split. It returns that transformed string. (default: `None`)

-

**separator** (`Optional`[`str`]) – Separator character used to split the device response string into a list. None means split on whitespace as in `str.split`. (default: `','`)

-

**maxsplit** (`int`) – Maximum number of splits to apply to the device response string. The default -1 means unlimited splitting. (default: `-1`)

-

**cast** (`Callable`[[`str`], `TypeVar`(`T`)]) –

Type used to cast each value produced by splitting the string.

Deprecated since version 0.17.0: When a cast fails, that element remains a string; see `values()`. To permit mixed types explicitly, pass `cast_or_str()` as the cast function. (default: `<class 'float'>`)

-

**values_kwargs** (*dict*) – Additional keyword arguments passed to `values()`.

Return type:

`Union`[`property`, `DynamicProperty`]

 *property *next_error*: Any*

Read the next queued error. To read and log every error, call `check_errors()` instead.

 *property *offset*: Any*

Set or read voltage offset in Volts (float).(dynamic)

 *property *options*: Any*

Get the device options installed.

 *property *output*: Any*

Set or read output state (bool).(dynamic)

 *property *output_load*: Any*

Set or read expected load resistance in Ohms (str or float). Output impedance remains 50 Ohm; this setting adjusts the displayed voltage for loads that are not matched to 50 Ohm.(dynamic)

 *property *phase*: Any*

Set or read waveform phase in degrees (float, from -360 to 360).

 phase_sync()

Synchronize every channel phase.

 *property *pulse_dutycycle*: Any*

Set or read pulse duty cycle in percent (float, from 0 to 100).(dynamic)

 *property *pulse_hold*: Any*

Choose whether pulse width or duty cycle is held constant when waveform period or frequency changes (str).(dynamic)

 *property *pulse_period*: Any*

Set or read pulse period in seconds (float). Overrides frequency. If period < pulse width + edge time, both edge time and pulse width are adjusted.(dynamic)

 *property *pulse_transition*: Any*

Set or read pulse edge time, covering both rising and falling edges, in seconds (float).(dynamic)

 *property *pulse_width*: Any*

Set or read pulse width in seconds (float).(dynamic)

 *property *ramp_symmetry*: Any*

Set or read ramp waveform symmetry in percent (float, from 0 to 100).(dynamic)

 read(***kwargs*)

Read until just before read_termination, or read the entire buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes requested. A value of -1 means read the entire buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 remove_child(*child*)

Delete the child from both the instrument and the matching collection.

Parameters:

**child** (`Child`) – Child instance to remove.

Return type:

`None`

 reset()

Reset the instrument.

 *static *setting(*set_command*, *docs*, *validator=<function CommonBase.<lambda>>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.<lambda>>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the supplied commands. This property can be set, but attempting to read it from the instrument raises an exception.

Parameters:

-

**set_command** (`str`) – String command that writes the value

-

**docs** (`str`) – Docstring text inserted into the documentation

-

**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) – Function that receives a value plus valid values and returns an accepted value; otherwise it raises an exception (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

-

**values** (`TypeVar`(`Vs`)) – Valid values supplied as a list, tuple, range, or dictionary; when `map_values` is True this may also map values. (default: `()`)

-

**map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

-

**set_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value, can transform it before value mapping, and returns the transformed value (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

-

**check_set_errors** (`bool`) – Enables error checks after setting a value (default: `False`)

-

**dynamic** (`bool`) – Indicates whether property parameters are intended to be changed on instances or subclasses. See `control()` for a usage example. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]

 *property *shape*: Any*

Set or read the output waveform shape (str).(dynamic)

 shutdown()

Put the instrument into a safe, stable state

Return type:

`None`

 *property *square_dutycycle*: Any*

Set or read square wave duty cycle in percent (float).(dynamic)

 *property *status*: Any*

Read the status byte and Master Summary Status bit.

 trigger()

Issue a trigger signal to the function generator.

 *property *trigger_source*: Any*

Control the trigger source (str).

 values(*command*, *separator='*, *'*, *cast=<class 'float'>*, *preprocess_reply=None*, *maxsplit=-1*, ***kwargs*)

Send a command to the instrument and return the response as a list of formatted values.

Parameters:

-

**command** (`str`) – SCPI command sent to the instrument.

-
