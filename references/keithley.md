# Keithley2750, Keithley2306, Keithley6517B

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Keithley 2750 Multimeter/Switch System; Keithley 2306 Dual Channel Battery/Charger Simulator; Keithley 6517B Electrometer.

## Keithley 2750 Multimeter/Switch System

### Keithley 2750 Multimeter/Switch System

 *class *pymeasure.instruments.keithley.Keithley2750(*adapter*, *name='Keithley 2750 Multimeter/Switch System'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley2750 multimeter/switch system, exposing a higher-level API for instrument operations.

 check_errors()

Retrieve every error currently reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect and log any reported errors.

Runs when that property has `check_get_errors=True` configured.

Subclasses that override this method can raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 check_set_errors()

After assigning a property, inspect and log any reported errors.

Runs when that property has `check_set_errors=True` configured.

Subclasses that override this method can raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 close(*channel*)

Closes (connects) the specified channel.

Parameters:

**channel** (*int*) ??? 3-digit channel number.

Returns:

None

 *property *closed_channels*: Any*

Return the channels that are currently closed.

 *property *complete*: Any*

Get the synchronization bit.

This property coordinates a controller with the device. Once all pending selected device operations finish, the Operation Complete query inserts ASCII character 1 into the device???s Output Queue.

 *property *id*: Any*

Return the instrument identification string.

 *property *next_error*: Any*

Fetch one error from the queue. To collect and log every error, call `check_errors()` instead.

 open(*channel*)

Opens (disconnects) the specified channel.

Parameters:

**channel** (*int*) ??? 3-digit channel number.

Returns:

None

 open_all()

Open every channel on the switch matrix, disconnecting them all.

Returns:

None

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until just before read_termination, or consume the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) ??? Bytes to read. Use -1 to consume the entire read buffer.

-

**kwargs** ??? Adapter-specific keyword arguments.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Put the instrument into a stable, safe condition.

Return type:

`None`

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 wait_for(*query_delay=None*)

Pause for a duration; ???ask??? uses this delay before reading.

Parameters:

**query_delay** (`Optional`[`float`]) ??? Seconds to wait between write and read. None selects the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Parameters:

-

**command** (`str`) ??? Command string sent to the instrument.

-

**kwargs** ??? Adapter-specific keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) ??? Values that will be transmitted.

-

****kwargs** (**args**,*) ??? Additional arguments passed through to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

## Keithley 2306 Dual Channel Battery/Charger Simulator

### Keithley 2306 Dual Channel Battery/Charger Simulator

 *class *pymeasure.instruments.keithley.Keithley2306(*adapter*, *name='Keithley 2306'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 2306 Dual Channel Battery/Charger Simulator.

 *property *both_channels_enabled*: Any*

Enable or disable both channel outputs; accepted values are True and False.

 ch(*channel_number*)

Return one channel object from this instrument.

Param:

channel_number: int: number identifying the channel to select.

Type:

`Keithley2306Channel`

 check_errors()

Retrieve every error currently reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect and log any reported errors.

Runs when that property has `check_get_errors=True` configured.

Subclasses that override this method can raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 check_set_errors()

After assigning a property, inspect and log any reported errors.

Runs when that property has `check_set_errors=True` configured.

Subclasses that override this method can raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property coordinates a controller with the device. Once all pending selected device operations finish, the Operation Complete query inserts ASCII character 1 into the device???s Output Queue.

 *property *display_brightness*: Any*

Set the floating display brightness from 0.0 through 1.0. 0.0 blanks the display; values less or equal to 0.25 use 1/4 brightness, values less than or equal to 0.5 use 1/2 brightness, values less than or equal to 0.75 use 3/4 brightness, and higher values select full brightness.

 *property *display_channel*: Any*

Select the integer display channel; valid choices are 1 and 2.

 *property *display_enabled*: Any*

Enable or disable the display with a boolean True or False value.

 *property *display_text_data*: Any*

Set the displayed text string, with a maximum length of 32 characters.

 *property *display_text_enabled*: Any*

Enable or disable display text with a boolean True or False value.

 *property *id*: Any*

Return the instrument identification string.

 *property *next_error*: Any*

Fetch one error from the queue. To collect and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until just before read_termination, or consume the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) ??? Bytes to read. Use -1 to consume the entire read buffer.

-

**kwargs** ??? Adapter-specific keyword arguments.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`

 relay(*relay_number*)

Return one relay channel object from this instrument.

Param:

relay_number: int: number identifying the relay to select.

Type:

`Relay`

 reset()

Reset the instrument.

 shutdown()

Put the instrument into a stable, safe condition.

Return type:

`None`

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 wait_for(*query_delay=None*)

Pause for a duration; ???ask??? uses this delay before reading.

Parameters:

**query_delay** (`Optional`[`float`]) ??? Seconds to wait between write and read. None selects the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Parameters:

-

**command** (`str`) ??? Command string sent to the instrument.

-

**kwargs** ??? Adapter-specific keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) ??? Values that will be transmitted.

-

****kwargs** (**args**,*) ??? Additional arguments passed through to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

## Keithley 6517B Electrometer

### Keithley 6517B Electrometer

 *class *pymeasure.instruments.keithley.Keithley6517B(*adapter*, *name='Keithley 6517B Electrometer/High Resistance Meter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 6517B ElectroMeter, exposing a higher-level API for instrument operations.

```python
keithley = Keithley6517B("GPIB::1")

keithley.apply_voltage()              # Sets up to source current
keithley.source_voltage_range = 200   # Sets the source voltage
                                      # range to 200 V
keithley.source_voltage = 20          # Sets the source voltage to 20 V
keithley.enable_source()              # Enables the source output

keithley.measure_resistance()         # Sets up to measure resistance

keithley.ramp_to_voltage(50)          # Ramps the voltage to 50 V
print(keithley.resistance)            # Prints the resistance in Ohms

keithley.shutdown()                   # Ramps the voltage to 0 V
                                      # and disables output

```

 apply_voltage(*voltage_range=None*)

Configure the instrument to source voltage, using auto range unless a voltage range is supplied.

Parameters:

**voltage_range** ??? A `voltage_range` setting, or None to enable auto range. (default: `None`)

 auto_range_source()

Set the source to automatic range mode.

 *property *buffer_data

Return buffer contents as a numpy array of values.

 *property *buffer_points*: Any*

Set or read the configured integer count for buffer points. This is the configuration setting, not the number currently stored in the buffer.

 check_errors()

Retrieve every error currently reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect and log any reported errors.

Runs when that property has `check_get_errors=True` configured.

Subclasses that override this method can raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 check_set_errors()

After assigning a property, inspect and log any reported errors.

Runs when that property has `check_set_errors=True` configured.

Subclasses that override this method can raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property coordinates a controller with the device. Once all pending selected device operations finish, the Operation Complete query inserts ASCII character 1 into the device???s Output Queue.

 config_buffer(*points=64*, *delay=0*)

Set up the measurement buffer for a point count, using the requested delay between points.

Parameters:

-

**points** ??? Number of points configured for the buffer. (default: `64`)

-

**delay** ??? Delay duration in seconds. (default: `0`)

 *property *current*: Any*

Return current in Amps when the instrument is configured for that reading.

 *property *current_nplc*: Any*

Set the floating NPLC value for DC current measurements; this controls integration period and measurement speed. Valid values run from 0.01 to 10, with 0.1, 1, and 10 corresponding to Fast, Medium, and Slow respectively.

 *property *current_range*: Any*

Set the floating current measurement range in Amps; accepted values span -20 to +20 mA. Setting this property turns off auto-range.

 disable_buffer()

Disconnect measurements from the buffer without aborting the measurement process.

 disable_source()

Turn off the configured current or voltage source.

 enable_source()

Turn on the configured current or voltage source.

 *property *error

Return the next queued error.

Deprecated since version 0.15: Use next_error instead.

 *static *extract_value(*result*)

Pull the physical value out of a result object returned by the instrument.

 *property *id*: Any*

Return the instrument identification string.

 is_buffer_full()

Return True when the buffer contains its full set of measurements.

 measure_current(*nplc=1*, *current=0.000105*, *auto_range=True*)

Configures the measurement of current.

Parameters:

-

**nplc** ??? Power line cycle count (NPLC), from 0.01 to 10. (default: `1`)

-

**current** ??? Upper current bound in Amps, from -21 mA to 21 mA. (default: `0.000105`)

-

**auto_range** ??? Enables auto_range when True; otherwise the current_range attribute is used. (default: `True`)

 measure_resistance(*nplc=1*, *resistance=210000.0*, *auto_range=True*)

Configures the measurement of resistance.

Parameters:

-

**nplc** ??? Power line cycle count (NPLC), from 0.01 to 10. (default: `1`)

-

**resistance** ??? Upper resistance bound in Ohms, from -210 POhms to 210 POhms. (default: `210000.0`)

-

**auto_range** ??? Enables auto_range when True; otherwise the resistance_range attribute is used. (default: `True`)

 measure_voltage(*nplc=1*, *voltage=21.0*, *auto_range=True*)

Configures the measurement of voltage.

Parameters:

-

**nplc** ??? Power line cycle count (NPLC), from 0.01 to 10. (default: `1`)

-

**voltage** ??? Upper voltage bound in Volts, from -1000 V to 1000 V. (default: `21.0`)

-

**auto_range** ??? Enables auto_range when True; otherwise the voltage_range attribute is used. (default: `True`)

 *property *next_error*: Any*

Fetch one error from the queue. To collect and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 ramp_to_voltage(*target_voltage*, *steps=30*, *pause=0.02*)

Move from the currently set voltage to target voltage through a chosen number of linear steps, pausing between each step.

Parameters:

-

**target_voltage** ??? Voltage value in Volts.

-

**steps** ??? Integer step count. (default: `30`)

-

**pause** ??? Pause duration in seconds between steps. (default: `0.02`)

 read(***kwargs*)

Read until just before read_termination, or consume the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) ??? Bytes to read. Use -1 to consume the entire read buffer.

-

**kwargs** ??? Adapter-specific keyword arguments.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`

 reset()

Reset the instrument and clear the queue.

 reset_buffer()

Reset the buffer.

 *property *resistance*: Any*

Return resistance in Ohms when the instrument is configured for that reading.

 *property *resistance_nplc*: Any*

Set the floating NPLC value for 2-wire resistance measurements; this controls integration period and measurement speed. Valid values run from 0.01 to 10, with 0.1, 1, and 10 corresponding to Fast, Medium, and Slow respectively.

 *property *resistance_range*: Any*

Set the floating resistance range in Ohms; valid values run from 0 to 100e18 Ohms. Setting this property turns off auto-range.

 shutdown()

Force current or voltage to zero and disable the output.

 *property *source_current_resistance_limit*: Any*

Enable or disable the current limit.

 *property *source_enabled*: Any*

Return whether the source is enabled.

 *property *source_voltage*: Any*

Set the floating source voltage in Volts.

 *property *source_voltage_range*: Any*

Set the floating source voltage range in Volts; accepted values span -1000 to 1000 V. Setting this property turns off auto-range.

 start_buffer()

Starts the buffer.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 stop_buffer()

Abort buffered measurement by stopping the measurement arming and triggering sequence. When available, use a Selected Device Clear (SDC).

 trigger()

Issue a bus trigger for use after `trigger_on_bus()` has been configured.

 trigger_immediately()

Configure measurements to use the internal trigger at the highest sampling rate.

 trigger_on_bus()

Configure event detection based on the bus trigger, which `trigger()` can activate.

 *property *voltage*: Any*

Return voltage in Volts when the instrument is configured for that reading.

 *property *voltage_nplc*: Any*

Set the floating NPLC value for DC voltage measurements; this controls integration period and measurement speed. Valid values run from 0.01 to 10, with 0.1, 1, and 10 corresponding to Fast, Medium, and Slow respectively.

 *property *voltage_range*: Any*

Set the floating voltage measurement range in Volts; accepted values span -1000 to 1000 V. Setting this property turns off auto-range.

 wait_for(*query_delay=None*)

Pause for a duration; ???ask??? uses this delay before reading.

Parameters:

**query_delay** (`Optional`[`float`]) ??? Seconds to wait between write and read. None selects the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*should_stop=<function KeithleyBuffer.<lambda>>*, *timeout=60*, *interval=0.1*)

Block execution until the buffer is full. The call returns earlier if `should_stop` returns True or if timeout occurs before the buffer fills.

Parameters:

-

**should_stop** ??? Function returning True when this call should exit early. (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

-

**timeout** ??? Time in seconds after which the call exits early. (default: `60`)

-

**interval** ??? Time in seconds between buffer-full checks. (default: `0.1`)

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Parameters:

-

**command** (`str`) ??? Command string sent to the instrument.

-

**kwargs** ??? Adapter-specific keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) ??? Values that will be transmitted.

-

****kwargs** (**args**,*) ??? Additional arguments passed through to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`
