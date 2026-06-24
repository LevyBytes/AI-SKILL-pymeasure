# Keithley2182, Keithley2700

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Keithley 2182 Nanovoltmeter; Keithley 2700 MultiMeter/Switch System.

## Keithley 2182 Nanovoltmeter

### Keithley 2182 Nanovoltmeter

 *class *pymeasure.instruments.keithley.Keithley2182(*adapter*, *name='Keithley 2182 Nanovoltmeter'*, *read_termination='\r'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), `KeithleyBuffer`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model interface for the Keithley 2182 Nanovoltmeter, exposing high-level operations for communicating with the instrument.

```python
keithley = Keithley2182("GPIB::1")

keithley.reset()                        # Return instrument settings to default
                                          values
keithley.thermocouple = 'S'             # Sets thermocouple type to S
keithley.active_channel = 1             # Sets channel 1 for active measurement
keithley.channel_function = 'voltage'   # Configures active channel for voltage
                                          measurement
print(keithley.voltage)                 # Prints the voltage in volts

keithley.ch_1.setup_voltage()           # Set channel 1 active and prepare
                                          voltage measurement
keithley.ch_2.setup_temperature()       # Set channel 2 active and prepare
                                          temperature measurement

```

 ch_1

Channel:

`Keithley2182Channel`

 ch_2

Channel:

`Keithley2182Channel`

 *property *active_channel*: Any*

Select the channel used for measurements. Valid values are 0 (internal temperature sensor), 1, and 2.

 auto_line_frequency()

Apply suitable bounds for NPLC voltage and temperature readings.

 *property *auto_zero_enabled*: Any*

Enable or disable the auto zero option (bool).

 *property *buffer_data

Return buffer contents as a numpy array of values.

 *property *buffer_points*: Any*

Set the configured number of buffer points. This is the configuration value, not the current count of stored points.

 *property *channel_function*: Any*

Choose the measurement mode for the active channel. Valid options are voltage and temperature.

 check_errors()

Retrieve every queued instrument error.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect the error queue and log any entries.

Invoked when that property has `check_get_errors=True` configured.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property write, inspect the error queue and log any entries.

Invoked when that property has `check_set_errors=True` configured.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize the controller with the device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the Output Queue of the device.

 config_buffer(*points=64*, *delay=0*)

Configure the measurement buffer with a requested number of points and a specified delay.

Parameters:

-

**points** – Number of buffer points to configure. (default: `64`)

-

**delay** – Delay duration, in seconds. (default: `0`)

 disable_buffer()

Disconnect measurements from the buffer without aborting the active measurement process.

 *property *display_enabled*: Any*

Enable or disable the voltmeter front display. Valid values are True and False.

 *property *id*: Any*

Return the instrument identification string.

 *property *internal_temperature*: Any*

Measure the instrument internal temperature in Celsius.

 is_buffer_full()

Return True when the buffer contains a full set of measurements.

 *property *line_frequency*: Any*

Line frequency in Hertz is reported as 50 or 60. On 2182 this setting is read-only.

 *property *maximum*: Any*

Return the maximum value calculated from the buffer data.

 *property *mean*: Any*

Return the mean (average) calculated from the buffer data.

 *property *minimum*: Any*

Return the minimum value calculated from the buffer data.

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until just before read_termination, or consume the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Byte count to read. A value of -1 reads the complete read buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Bytes returned by the instrument, including termination.

Return type:

`bytes`

 reset()

Reset the instrument and empty the queue.

 reset_buffer()

Reset the buffer.

 sample_continuously()

Set up continuous sample reading and disable buffer or output triggering.

 shutdown()

Place the instrument in a safe, stable state.

Return type:

`None`

 *property *standard_dev*: Any*

Return the standard deviation calculated from the buffer data.

 start_buffer()

Starts the buffer.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 stop_buffer()

Stop the buffering measurement by aborting the measurement arming and triggering sequence. When available, this uses Selected Device Clear (SDC).

 *property *temperature*: Any*

Measure temperature in Celsius when the active channel is configured for that reading.

 *property *temperature_nplc*: Any*

Set the number of power line cycles (NPLC) for temperature measurements; this determines integration period and measurement speed. Line frequency determines whether the upper limit is 50 or 60; the lower limit is 0.01. Default is 5.(dynamic)

 *property *temperature_reference_junction*: Any*

Choose whether the thermocouple reference junction uses internal (INT) or simulated (SIM) mode. Default is INT.

 *property *temperature_simulated_reference*: Any*

Set the simulated thermocouple reference junction value in Celsius. Default is 23 C.

 *property *thermocouple*: Any*

Select the temperature-measurement thermocouple type. Choices are B, E, J, K, N, R, S, and T.

 trigger()

Send a bus trigger for use after `trigger_on_bus()` has been configured.

 *property *trigger_count*: Any*

Set the trigger count, accepting values from 1 to 9,999. Default is 1.

 *property *trigger_delay*: Any*

Set trigger delay in seconds; accepted values run from 0 to 999999.999 s. Default is 0.

 trigger_immediately()

Use the internal trigger to take measurements at the maximum sampling rate.

 trigger_on_bus()

Set triggering to respond to bus trigger events, which `trigger()` can activate.

 *property *voltage*: Any*

Measure voltage in Volts when the active channel is configured for that reading.

 *property *voltage_nplc*: Any*

Set the number of power line cycles (NPLC) for voltage measurements; this determines integration period and measurement speed. Line frequency determines whether the upper limit is 50 or 60; the lower limit is 0.01. Default is 5.(dynamic)

 wait_for(*query_delay=None*)

Pause for a period of time. Used by ask before it reads.

Parameters:

**query_delay** (`Optional`[`float`]) – Delay in seconds between write and read operations. None means the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*should_stop=<function KeithleyBuffer.<lambda>>*, *timeout=60*, *interval=0.1*)

Block until the buffer is full. This function exits early if `should_stop` returns True or if timeout occurs before the buffer fills.

Parameters:

-

**should_stop** – Function that returns True to make this function exit early. (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

-

**timeout** – Time in seconds after which this function exits early. (default: `60`)

-

**interval** – Time in seconds between checks for whether the buffer is full. (default: `0.1`)

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values to transmit.

-

****kwargs** (**args**,*) – Additional arguments to pass to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Write byte content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.keithley.keithley2182.Keithley2182Channel(*parent*, *id*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Implementation of a Keithley 2182 channel.

Channel 1 is the primary measurement channel; channel 2 supplies sense measurements. Channel 2 inputs reference Channel 1 LO. Possible configurations are

Supported configurations: Voltage (Channel 1); Temperature (Channel 1); dual voltage using Voltage (Channel 1) and Voltage (Channel 2); voltage plus temperature using Voltage (Channel 1) and Temperature (Channel 2)

 acquire_temperature_reference()

Take a temperature measurement and save it as the relative offset value.

Reference acquisition occurs only when temperature offset is enabled.

 acquire_voltage_reference()

Take a voltage measurement and save it as the relative offset value.

Reference acquisition occurs only when voltage offset is enabled.

 setup_temperature(*nplc=5*)

Switch the active channel and set that channel up for temperature measurement.

Parameters:

**nplc** – NPLC setting, expressed in power line cycles, allowed from 0.01 to 50/60. (default: `5`)

 setup_voltage(*auto_range=True*, *nplc=5*)

Select the active channel and set that channel up for voltage measurement.

Parameters:

-

**auto_range** – If True, enables auto_range; otherwise uses the set voltage range. (default: `True`)

-

**nplc** – NPLC setting, expressed in power line cycles, allowed from 0.01 to 50/60. (default: `5`)

 *property *temperature_offset*: Any*

Set the temperature relative-offset value. Displayed value = actual value - offset value. Allowed values run from -273 C to 1800 C.

 *property *temperature_offset_enabled*: Any*

Choose whether temperature readings are relative or absolute (bool). Disabled by default.

 *property *voltage_offset*: Any*

Set the relative offset used for voltage measurement. Displayed value = actual value - offset value. For Ch. 1, valid ranges are -120 V to +120 V; for Ch. 2, valid ranges are -12 V to +12 V.(dynamic)

 *property *voltage_offset_enabled*: Any*

Choose relative or absolute voltage readings (bool). For Ch. 2 voltage, the default is enabled because that channel is measured relative to Ch. 1 voltage.

 *property *voltage_range*: Any*

Set the positive full-scale voltage range in Volts. Keithley 2182 range selection is based on the expected voltage. DCV1 offers 10 mV, 100 mV, 1 V, 10 V, and 100 V across five ranges. DCV2 offers 100 mV, 1 V, and 10 V across three ranges. Limits are 0 to 120 V on Ch. 1 and 0 to 12 V on Ch. 2. Setting this property turns off auto-range automatically.(dynamic)

 *property *voltage_range_auto_enabled*: Any*

Enable or disable automatic voltage ranging (bool).

## Keithley 2700 MultiMeter/Switch System

### Keithley 2700 MultiMeter/Switch System

 *class *pymeasure.instruments.keithley.Keithley2700(*adapter*, *name='Keithley 2700 MultiMeter/Switch System'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model interface for the Keithley 2700 Multimeter/Switch System, exposing high-level operations for communicating with the instrument.

```python
keithley = Keithley2700("GPIB::1")

```

 beep(*frequency*, *duration*)

Sounds a system beep.

Parameters:

-

**frequency** – Frequency in Hz from 65 Hz through 2 MHz

-

**duration** – Time in seconds from 0 through 7.9 seconds

 *property *buffer_data

Return buffer contents as a numpy array of values.

 *property *buffer_points*: Any*

Set the configured number of buffer points. This is the configuration value, not the current count of stored points.

 channels_from_rows_columns(*rows*, *columns*, *slot=None*)

Compute the 7709 connection matrix channel numbers for the supplied column(s) and row(s). Returns a list of channel numbers. Only one of "rows" or "columns" can be "all"

Parameters:

-

**rows** – row number, list of numbers, or "all"

-

**columns** – column number, list of numbers, or "all"

-

**slot** – slot number (1 or 2) for the 7709 card to use. (default: `None`)

 check_errors()

Retrieve every queued instrument error.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect the error queue and log any entries.

Invoked when that property has `check_get_errors=True` configured.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property write, inspect the error queue and log any entries.

Invoked when that property has `check_set_errors=True` configured.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 close_rows_to_columns(*rows*, *columns*, *slot=None*)

Close, meaning connect, the 7709 connection matrix channels between the chosen column(s) and row(s). Only one of "rows" or "columns" can be "all"

Parameters:

-

**rows** – row number, list of numbers, or "all"

-

**columns** – column number, list of numbers, or "all"

-

**slot** – slot number (1 or 2) for the 7709 card to use. (default: `None`)

 *property *closed_channels*: Any*

Set the open/closed channel state. Every listed channel is closed; channels not listed are opened.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize the controller with the device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the Output Queue of the device.

 config_buffer(*points=64*, *delay=0*)

Configure the measurement buffer with a requested number of points and a specified delay.

Parameters:

-

**points** – Number of buffer points to configure. (default: `64`)

-

**delay** – Delay duration, in seconds. (default: `0`)

 determine_valid_channels()

Identify the cards installed in the Keithley 2700 and use that information to determine valid channels.

 disable_buffer()

Disconnect measurements from the buffer without aborting the active measurement process.

 display_closed_channels()

Display the channels that are currently closed on the Keithley 2700.

 *property *display_text*: Any*

Set the (string) text shown on the Keithley 2700 display. Text may contain up to 12 ASCII characters and must be enabled before it appears.

 *property *error

Return the next queued error.

Since version 0.15, this is deprecated; use next_error instead.

 get_state_of_channels(*channels*)

Return the open or closed state for the specified channels.

Parameters:

**channels** – list of channel numbers, or one channel number

 *property *id*: Any*

Return the instrument identification string.

 is_buffer_full()

Return True when the buffer contains a full set of measurements.

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 open_all_channels()

Open every Keithley 2700 channel.

 *property *open_channels*: Any*

Assign the specified channel list. This value is set-only.

 open_rows_to_columns(*rows*, *columns*, *slot=None*)

Open, meaning disconnect, the 7709 connection matrix channels between the chosen column(s) and row(s). Only one of "rows" or "columns" can be "all"

Parameters:

-

**rows** – row number, list of numbers, or "all"

-

**columns** – column number, list of numbers, or "all"

-

**slot** – slot number (1 or 2) for the 7709 card to use. (default: `None`)

 *property *options*: Any*

Return the installed-card lists for the Keithley 2700. The result is a dict whose positions contain integer card numbers.

 read(***kwargs*)

Read until just before read_termination, or consume the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Byte count to read. A value of -1 reads the complete read buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Bytes returned by the instrument, including termination.

Return type:

`bytes`

 reset()

Reset the instrument and empty the queue.

 reset_buffer()

Reset the buffer.

 shutdown()

Place the instrument in a safe, stable state.

Return type:

`None`

 start_buffer()

Starts the buffer.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 stop_buffer()

Stop the buffering measurement by aborting the measurement arming and triggering sequence. When available, this uses Selected Device Clear (SDC).

 *property *text_enabled*: Any*

Enable or disable whether a text message can appear on the Keithley 2700 display (boolean).

 triad(*base_frequency*, *duration*)

Play a musical triad through the system beep.

Parameters:

-

**base_frequency** – Frequency in Hz from 65 Hz through 1.3 MHz

-

**duration** – Time in seconds from 0 through 7.9 seconds

 wait_for(*query_delay=None*)

Pause for a period of time. Used by ask before it reads.

Parameters:

**query_delay** (`Optional`[`float`]) – Delay in seconds between write and read operations. None means the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*should_stop=<function KeithleyBuffer.<lambda>>*, *timeout=60*, *interval=0.1*)

Block until the buffer is full. This function exits early if `should_stop` returns True or if timeout occurs before the buffer fills.

Parameters:

-

**should_stop** – Function that returns True to make this function exit early. (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

-

**timeout** – Time in seconds after which this function exits early. (default: `60`)

-

**interval** – Time in seconds between checks for whether the buffer is full. (default: `0.1`)

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values to transmit.

-

****kwargs** (**args**,*) – Additional arguments to pass to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Write byte content to the instrument.

Return type:

`None`
