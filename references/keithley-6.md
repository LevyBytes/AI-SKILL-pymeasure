# Keithley2200, Keithleydaq6510

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Keithley 2200 Series Power Supplies; Keithley DAQ6510 Data Acquisition Logging Multimeter System.

## Keithley 2200 Series Power Supplies

### Keithley 2200 Series Power Supplies

 *class *pymeasure.instruments.keithley.Keithley2200(*adapter*, *name='Keithley2200'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents the Keithley 2200 Power Supply.

 ch_1

Channel:

`PSChannel`

 ch_2

Channel:

`PSChannel`

 ch_3

Channel:

`PSChannel`

 *class *BaseChannelCreator(***kwargs*)

Bases: `object`

Shared base type for ChannelCreator and MultiChannelCreator.

Parameters:

-

**cls** – Supplies the class used for all children, or a tuple/list of classes matched one-to-one with the children.

-

****kwargs** – Keyword arguments passed to every child.

 *class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Register one channel on the parent class.

At instantiation, the child is attached to the parent instance through `CommonBase.add_child()`. The channel interface uses the Instrument class attribute name that held the ChannelCreator assignment.

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

**id** (`Union`[`int`, `str`, `None`]) – Channel id on the instrument, as an integer or string. (default: `None`)

-

****kwargs** – Keyword arguments passed to every child.

 *class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Register multiple channels on the parent class.

During instantiation, each child is attached to the parent instance with `CommonBase.add_child()`. The attribute name, for example `channels`, becomes the child collection. A custom attribute prefix can be specified. Unless another requirement applies, use `channels` for the attribute name and keep the default prefix `"ch_"`.

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

**cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) – Class applied to every child, or a tuple/list giving a separate class for each child.

-

**id** (`Union`[`int`, `str`, `None`]) – tuple/list of instrument channel ids. (default: `None`)

-

**prefix** (`Optional`[`str`]) – Attribute prefix for the collection; e.g. “ch_” creates self.ch_A. If prefix evaluates False, the child is attached directly under the variable name. Required when id is tuple/list. (default: `'ch_'`)

-

****kwargs** – Keyword arguments passed to every child.

 add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Attach a child to this instance, then return its position in the children list.

The created child can be reached through the children dictionary by id or through its generated attribute; for example, the fifth channel of instrument with id “F” is available as `instrument.channels["F"] == instrument.ch_F`.

Note

Keep the default collection and prefix settings unless multiple child collections must be separated, such as analog and digital channel types.

Parameters:

-

**cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) – Channel class to instantiate.

-

**id** (`Union`[`int`, `str`, `None`]) – Child id used during communication, e.g. “A”. (default: `None`)

-

**collection** (`str`) – Child-collection name used for dictionary lookup of channel interfaces. (default: `'channels'`)

-

**prefix** (`Optional`[`str`]) – Prefix used when building several channel interfaces; e.g. “ch_” is prepended to produce self.ch_A. If prefix evaluates False, the child is attached directly under the collection name. (default: `'ch_'`)

-

**attr_name** (`Optional`[`str`]) – For a single channel interface, attr_name supplies the attribute name assigned to that interface. (default: `''`)

-

****kwargs** – Keyword arguments supplied to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) – Created child instance.

 binary_values(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument and return the binary response as a numpy array.

Parameters:

-

**command** (`str`) – Command sent to the instrument.

-

**query_delay** (`Optional`[`float`]) – Seconds to wait between the write and the read. (default: `None`)

-

**kwargs** – Arguments forwarded to `read_binary_values()`.

Returns:

NumPy array of values.

 check_errors()

Retrieve every error currently reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property get, inspect errors and write them to the log.

Runs for properties configured with `check_get_errors=True`.

Overriding this method lets selected errors raise an Exception.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set, inspect errors and write them to the log.

Runs for properties configured with `check_set_errors=True`.

Overriding this method lets selected errors raise an Exception.

Returns:

`list` – List of error entries.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. When all pending selected device operations are done, the Operation Complete query puts ASCII character 1 in the device’s Output Queue.

 *property *display_enabled*: Any*

Enable or disable the display.

 *property *display_text_data*: Any*

Set the display text(32 characters).

 *static *get_channel_pairs(*cls*)

Return all Instrument channel pairs as a list.

 *static *get_channels(*cls*)

Return all ChannelCreator and MultiChannelCreator instances owned by the Instrument as a list.

Return type:

`list`[`tuple`[`str`, [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)]]

 *property *id*: Any*

Return the instrument identification.

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes to read. Use -1 to consume the entire read buffer.

-

**kwargs** – Keyword arguments forwarded to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 remove_child(*child*)

Delete the child from the instrument and its matching collection.

Parameters:

**child** (`Child`) – Child instance to remove.

Return type:

`None`

 reset()

Reset the instrument.

 shutdown()

Put the instrument into a stable, safe state.

Return type:

`None`

 *property *status*: Any*

Return the status byte plus the Master Summary Status bit.

 wait_for(*query_delay=None*)

Pause for a period of time. `ask` uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

-

****kwargs** (**args**,*) – Additional arguments passed through to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Write byte content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.keithley.keithley2200.PSChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Implementation of a Keithley 2200 channel.

 *property *current*: Any*

Measure the current in Amps.

 *property *current_limit*: Any*

Control output current in Amps.

 insert_id(*command*)

Replace the command placeholder with the channel id.

Override this method to change that behavior, such as always prepending the channel id.

 *property *output_enabled*: Any*

Control the output state.

 *property *power*: Any*

Measure the power in watts.

 *property *voltage*: Any*

Measure the voltage in Volts.

 *property *voltage_limit*: Any*

Set or read the highest voltage that may be configured.

 *property *voltage_limit_enabled*: Any*

Enable or disable enforcement of the maximum voltage limit.

 *property *voltage_setpoint*: Any*

Control output voltage in Volts.

## Keithley DAQ6510 Data Acquisition Logging Multimeter System

### Keithley DAQ6510 Data Acquisition Logging Multimeter System

 *class *pymeasure.instruments.keithley.KeithleyDAQ6510(*adapter*, *name='Keithley DAQ6510'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley DAQ6510 Data Acquisition Logging Multimeter System and exposes a high-level interface for instrument interaction.

```python
keithley = KeithleyDAQ6510("GPIB::1")
keithley = KeithleyDAQ6510("TCPIP::192.168.1.1::INSTR")

print(keithley.current)                 # Prints the current in Amps
keithley.current_range = 10E-6          # Select the 10 uA range

print(keithley.voltage)                 # Prints the voltage in Volts
keithley.voltage_range = 100e-3         # Select the 100 mV range

print(keithley.resistance)              # Prints the resistance in Ohms
keithley.offset_compensated = "ON"      # Turns offset-compensated ohms on

keithley.open_channels([134, 135])      # Open channels 134 and 135 on the MUX card
keithley.close_channel(133)             # Close channel 133 on the MUX card

```

 beep(*frequency*, *duration*)

Sound a system beep.

Parameters:

-

**frequency** – Frequency in Hz, from 20 through 8000 Hz.

-

**duration** – Tone playback time, between 0.001 s to 100 s.

Returns:

None

 *property *buffer_data

Return the buffer values as a numpy array.

 *property *buffer_points*: Any*

Set or read the configured buffer-point count. This is the configuration value, not the actual number of points presently in the buffer.

 check_errors()

Retrieve every error currently reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property get, inspect errors and write them to the log.

Runs for properties configured with `check_get_errors=True`.

Overriding this method lets selected errors raise an Exception.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set, inspect errors and write them to the log.

Runs for properties configured with `check_set_errors=True`.

Overriding this method lets selected errors raise an Exception.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 close_channel(*channel*)

Close one channel.

Parameters:

**channel** – Channel that should be closed.

 close_channels(*channel_list*)

Close several channels.

Parameters:

**channel_list** – Channels that should be closed.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. When all pending selected device operations are done, the Operation Complete query puts ASCII character 1 in the device’s Output Queue.

 config_buffer(*points=64*, *delay=0*)

Prepare the measurement buffer for a chosen point count using the specified delay.

Parameters:

-

**points** – Number of points in the buffer. (default: `64`)

-

**delay** – Delay time in seconds. (default: `0`)

 *property *current*: Any*

Measure current in Amps when the instrument is configured for that reading.

 *property *current_nplc*: Any*

Set or read the DC current NPLC setting; it controls integration time and measurement speed. The accepted span starts at 5E-4, with an upper limit of 15 at 60 Hz or 12 at 50 Hz or 400 Hz. Smaller settings shorten the integration period and produce the fastest reading rate, with more reading noise and fewer usable digits. Larger settings lengthen the integration period and produce the slowest reading rate, with more usable digits.

 *property *current_range*: Any*

Set or read the current measurement range in Amps. For DC measurements, valid ranges span 10E-6 A to 3A. For AC measurements, valid ranges span 100E-6 to 3A. Setting this property turns Auto-range off.

 disable_buffer()

Disconnect measurements from the buffer without aborting the measurement process.

 *property *id*: Any*

Return the instrument identification.

 is_buffer_full()

Return True when the buffer contains a full set of measurements.

 measure_current(*nplc=1*, *current=3*, *auto_range=True*)

Configure the measurement of current.

Parameters:

-

**nplc** – Power line cycle count (NPLC); accepted settings start at 5E-4 and top out at 15 for 60 Hz or 12 for 50 Hz or 400 Hz. (default: `1`)

-

**current** – Current upper limit in Amps: 10E-6 through 3 A for DC, or 100E-6 through 3A for AC. (default: `3`)

-

**auto_range** – Boolean that enables auto_range when `True`; otherwise the configured current is used. (default: `True`)

 measure_resistance(*nplc=1*, *resistance=100000000.0*, *auto_range=True*)

Configure the measurement of resistance.

Parameters:

-

**nplc** – Power line cycle count (NPLC); accepted settings start at 5E-4 and top out at 15 for 60 Hz or 12 for 50 Hz or 400 Hz. (default: `1`)

-

**resistance** – Resistance upper limit in Ohms: 10 through 100E6 for 2-wire, 1 through 100E6 for 4-wire with OCOM off, or 1 through 10E3 for 4-wire with OCOM on. (default: `100000000.0`)

-

**auto_range** – Boolean that enables auto_range when `True`; otherwise the configured resistance is used. (default: `True`)

 measure_voltage(*nplc=1*, *voltage=1000*, *auto_range=True*)

Configure the measurement of voltage.

Parameters:

-

**nplc** – Power line cycle count (NPLC); accepted settings start at 5E-4 and top out at 15 for 60 Hz or 12 for 50 Hz or 400 Hz. (default: `1`)

-

**voltage** – Voltage upper limit in Volts: 100E-3 through 1000 V for DC, or 100E-3 through 750 V for AC. (default: `1000`)

-

**auto_range** – Boolean that enables auto_range when `True`; otherwise the configured voltage is used. (default: `True`)

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *offset_compensated*: Any*

Select whether offset compensation is used. Valid values are OFF, ON, and AUTO.

 open_channel(*channel*)

Open one channel.

Parameters:

**channel** – Channel that should be opened.

 open_channels(*channel_list*)

Open several channels.

Parameters:

**channel_list** – Channels that should be opened.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until, but not including, read_termination, or consume the entire read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes to read. Use -1 to consume the entire read buffer.

-

**kwargs** – Keyword arguments forwarded to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 reset_buffer()

Reset the buffer.

 *property *resistance*: Any*

Measure resistance in Ohms when the instrument is configured for that reading.

 *property *resistance_nplc*: Any*

Set or read the 2-wire resistance NPLC setting; it controls integration time and measurement speed. The accepted span starts at 5E-4, with an upper limit of 15 at 60 Hz or 12 at 50 Hz or 400 Hz. Smaller settings shorten the integration period and produce the fastest reading rate, with more reading noise and fewer usable digits. Larger settings lengthen the integration period and produce the slowest reading rate, with more usable digits.

 *property *resistance_range*: Any*

Set or read the resistance range in Ohms. With the 2-wire measurement function, ranges are 10 to 100E6 Ohms. With 4-wire resistance and offset compensation off, ranges are 1 to 100E6 Ohms. With 4-wire resistance and offset compensation on, ranges are 1 to 10E3 Ohms. Setting this property turns Auto-range off.

 *property *sense_mode*: Any*

Set or read the reading mode; accepted values are ‘current’ or ‘voltage’. The convenience methods `sense_current()` and `sense_voltage()` are available too.

 shutdown()

Put the instrument into a stable, safe state.

Return type:

`None`

 start_buffer()

Starts the buffer.

 *property *status*: Any*

Return the status byte plus the Master Summary Status bit.

 stop_buffer()

Stop the buffering measurement by halting the measurement arming and triggering sequence. When available, Selected Device Clear (SDC) is used.

 *property *voltage*: Any*

Measure voltage in Volts when the instrument is configured for that reading.

 *property *voltage_nplc*: Any*

Set or read the DC voltage NPLC setting; it controls integration time and measurement speed. The accepted span starts at 5E-4, with an upper limit of 15 at 60 Hz or 12 at 50 Hz or 400 Hz. Smaller settings shorten the integration period and produce the fastest reading rate, with more reading noise and fewer usable digits. Larger settings lengthen the integration period and produce the slowest reading rate, with more usable digits.

 *property *voltage_range*: Any*

Set or read the voltage measurement range in Volts. For DC measurements, valid ranges span 100E-3 V to 1000 V. For AC measurements, valid ranges span 100E-3 to 750 V. Setting this property turns Auto-range off.

 wait_for(*query_delay=None*)

Pause for a period of time. `ask` uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*should_stop=<function KeithleyBuffer.<lambda>>*, *timeout=60*, *interval=0.1*)

Block execution until the buffer is full. The function exits early if `should_stop` returns True, or if timeout is reached before a full buffer is available.

Parameters:

-

**should_stop** – Function that returns True when this function should exit early (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

-

**timeout** – Time in seconds after which this function exits early (default: `60`)

-

**interval** – Time in seconds between checks for whether the buffer is full (default: `0.1`)

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Keyword arguments forwarded to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

-

****kwargs** (**args**,*) – Additional arguments passed through to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Write byte content to the instrument.

Return type:

`None`
