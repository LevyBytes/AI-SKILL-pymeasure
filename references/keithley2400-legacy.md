# Keithley2400 Legacy

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Keithley 2400 SourceMeter (Legacy)

 *class *pymeasure.instruments.keithley.Keithley2400Legacy(*adapter*, *name='Keithley 2400 SourceMeter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model the Keithley 2400 SourceMeter and expose a high-level interface for instrument interaction.

Deprecated since version 0.16: This legacy Keithley2400 implementation is frozen at PyMeausure version 0.15 and retained for backwards compatibility.

```python
keithley = Keithley2400("GPIB::1")

keithley.apply_current()                # Sets up to source current
keithley.source_current_range = 10e-3   # Sets the source current range to 10 mA
keithley.compliance_voltage = 10        # Sets the compliance voltage to 10 V
keithley.source_current = 0             # Sets the source current to 0 mA
keithley.enable_source()                # Enables the source output

keithley.measure_voltage()              # Sets up to measure voltage

keithley.ramp_to_current(5e-3)          # Ramps the current to 5 mA
print(keithley.voltage)                 # Prints the voltage in Volts

keithley.shutdown()                     # Ramps the current to 0 mA and disables output

```

 apply_current(*current_range=None*, *compliance_voltage=0.1*)

Set up the instrument for source current, choosing auto range unless a current range is supplied. Also sets the compliance voltage.

Parameters:

-

**compliance_voltage** - float value within the valid range for `compliance_voltage` (default: `0.1`)

-

**current_range** - `current_range` value, or None (default: `None`)

 apply_voltage(*voltage_range=None*, *compliance_current=0.1*)

Set up the instrument for source voltage, choosing auto range unless a voltage range is supplied. Also sets the compliance current.

Parameters:

-

**compliance_current** - float value within the valid range for `compliance_current` (default: `0.1`)

-

**voltage_range** - `voltage_range` value, or None (default: `None`)

 *property *auto_output_off*: Any*

Control whether auto output-off is active. Valid values are True (output off after measurement) and False (output remains on after measurement).

 auto_range_source()

Set the source to automatic range.

 *property *auto_zero*: Any*

Control whether auto zero is enabled. Valid values are True (enabled), False (disabled), and 'ONCE' (force immediate).

 beep(*frequency*, *duration*)

Sound a system beep.

Parameters:

-

**frequency** - frequency in Hz from 65 Hz to 2 MHz

-

**duration** - time in seconds from 0 to 7.9 seconds

 *property *buffer_data

Return a numpy array containing the buffer values.

 *property *buffer_points*: Any*

Control the buffer point-count setting as an integer. It is the configured value, not the actual number of points currently in the buffer.

 check_errors()

Read every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property get operation, check for errors and log them.

Called when `check_get_errors=True` is set for that property.

When overriding this method, you can raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set operation, check for errors and log them.

Called when `check_set_errors=True` is set for that property.

When overriding this method, you can raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property provides synchronization between a controller and a device. The Operation Complete query writes ASCII character 1 into the device's Output Queue after all pending selected device operations are complete.

 *property *compliance_current*: Any*

Control the compliance current in Amps as a floating value.

 *property *compliance_voltage*: Any*

Control compliance voltage in Volts as a float, truncated from -210 to 210.

 config_buffer(*points=64*, *delay=0*)

Set up the measurement buffer for a specified point count and delay.

Parameters:

-

**points** - number of points in the buffer (default: `64`)

-

**delay** - delay time in seconds (default: `0`)

 *property *current*: Any*

Return the current in Amps, if configured, as a float.

 *property *current_nplc*: Any*

Control the DC current measurement NPLC (number of power line cycles), setting integration period and measurement speed. Values run from 0.01 to 10; 0.1, 1, and 10 correspond to Fast, Medium, and Slow.

 *property *current_range*: Any*

Control measurement current range in Amps as a float, truncated from -1.05 to 1.05. Setting this property disables auto-range.

 disable_buffer()

Disable the connection from measurements to the buffer without aborting the measurement process.

 disable_output_trigger()

Disable the output trigger for the Trigger layer.

 disable_source()

Disable the current or voltage source according to the instrument configuration.

 *property *display_enabled*: Any*

Control whether the sourcemeter display is enabled. Valid values are True and False.

 enable_source()

Enable the current or voltage source according to the instrument configuration.

 *property *error

Return the next error from the queue.

Deprecated since version 0.15: call next_error instead.

 *property *filter_count*: Any*

Control how many readings are acquired and saved in the filter buffer; integer, truncated from 1 to 100.

 *property *filter_state*: Any*

Control whether the filter is active; string, strictly 'ON' or 'OFF'.

 *property *filter_type*: Any*

Control the filter type as a String. REP: Repeating filter. MOV: Moving filter.

 *property *id*: Any*

Return the instrument identification.

 is_buffer_full()

Return True when the buffer is full of measurements.

 *property *line_frequency*: Any*

Control line frequency in Hertz; integer, strictly 50 or 60.

 *property *line_frequency_auto*: Any*

Control automatic line frequency as a boolean.

 *property *max_current

Return the maximum current from the buffer.

 *property *max_resistance

Return the maximum resistance from the buffer.

 *property *max_voltage

Return the maximum voltage from the buffer.

 *property *maximums*: Any*

Return calculated voltage, current, and resistance maximums from the buffer data as a list (list of floats).

 *property *mean_current

Return the mean current from the buffer.

 *property *mean_resistance

Return the mean resistance from the buffer.

 *property *mean_voltage

Return the mean voltage from the buffer.

 *property *means*: Any*

Return calculated voltage, current, and resistance means from the buffer data as a list (list of floats).

 *property *measure_concurent_functions*: Any*

Control whether more than one function can be measured simultaneously (boolean).

 measure_current(*nplc=1*, *current=0.000105*, *auto_range=True*)

Configure the measurement of current.

Parameters:

-

**nplc** - number of power line cycles (NPLC), from 0.01 through 10 (default: `1`)

-

**current** - upper current limit in Amps, from -1.05 A to 1.05 A (default: `0.000105`)

-

**auto_range** - enables auto_range when True; otherwise uses the set current (default: `True`)

 measure_resistance(*nplc=1*, *resistance=210000.0*, *auto_range=True*)

Configure the measurement of resistance.

Parameters:

-

**nplc** - number of power line cycles (NPLC), from 0.01 through 10 (default: `1`)

-

**resistance** - upper resistance limit in Ohms, from -210 MOhms to 210 MOhms (default: `210000.0`)

-

**auto_range** - enables auto_range when True; otherwise uses the set resistance (default: `True`)

 measure_voltage(*nplc=1*, *voltage=21.0*, *auto_range=True*)

Configure the measurement of voltage.

Parameters:

-

**nplc** - number of power line cycles (NPLC), from 0.01 through 10 (default: `1`)

-

**voltage** - upper voltage limit in Volts, from -210 V to 210 V (default: `21.0`)

-

**auto_range** - enables auto_range when True; otherwise uses the set voltage (default: `True`)

 *property *min_current

Return the minimum current from the buffer.

 *property *min_resistance

Return the minimum resistance from the buffer.

 *property *min_voltage

Return the minimum voltage from the buffer.

 *property *minimums*: Any*

Return calculated voltage, current, and resistance minimums from the buffer data as a list (list of floats).

 *property *next_error*: Any*

Return the next error in the queue. To read and log every error, use `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *output_off_state*: Any*

Control the SourceMeter output-off state. HIMP: opens the output relay and disconnects external circuitry. NORM: selects V-Source and sets it to 0V; Compliance becomes 0.5% full scale of the present current range. ZERO: selects V-Source and sets it to 0V; compliance uses the larger of the programmed Source I value or 0.5% full scale of the present current range. GUAR: selects I-Source and sets it to 0A

 output_trigger_on_external(*line=1*, *after='DEL'*)

Configure output triggering on the selected trigger link line number. Optionally choose the part of the measurement after which the trigger is generated; default is delay, immediately before the measurement.

Parameters:

-

**line** - trigger line from 1 to 4 (default: `1`)

-

**after** - event string determining when to trigger (default: `'DEL'`)

 ramp_to_current(*target_current*, *steps=30*, *pause=0.02*)

Move from the set current value to a target current across a chosen number of linear steps, with each step separated by a pause duration.

Parameters:

-

**target_current** - current in Amps

-

**steps** - integer number of steps (default: `30`)

-

**pause** - pause duration in seconds between steps (default: `0.02`)

 ramp_to_voltage(*target_voltage*, *steps=30*, *pause=0.02*)

Move from the set voltage value to a target voltage across a chosen number of linear steps, with each step separated by a pause duration.

Parameters:

-

**target_voltage** - voltage in Amps

-

**steps** - integer number of steps (default: `30`)

-

**pause** - pause duration in seconds between steps (default: `0.02`)

 read(***kwargs*)

Read until, but not including, read_termination, or read the full read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Read binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) - number of bytes to read. -1 means read the whole read buffer.

-

**kwargs** - keyword arguments for the adapter.

Returns bytes:

Instrument bytes response, including termination.

Return type:

`bytes`

 reset()

Reset the instrument, then clear the queue.

 reset_buffer()

Reset the buffer.

 *property *resistance*: Any*

Return resistance in Ohms when configured for this reading.

 *property *resistance_nplc*: Any*

Control the 2-wire resistance measurement NPLC (number of power line cycles), setting integration period and measurement speed. Values run from 0.01 to 10; 0.1, 1, and 10 correspond to Fast, Medium, and Slow.

 *property *resistance_range*: Any*

Control resistance range in Ohms as a float, truncated from 0 to 210e6. Setting this property disables auto-range.

 sample_continuously()

Make the instrument read samples continuously, turning off any buffer or output triggering.

 set_timed_arm(*interval*)

Set measurement acquisition to use the internal trigger. The sampling rate is variable and comes from the interval, in seconds, between sampling points.

 set_trigger_counts(*arm*, *trigger*)

Set counts for both sweeps (arm) and points inside those sweeps (trigger); total points can not exceed 2500.

 shutdown()

Ensure current or voltage is brought to zero, then disable the output.

 *property *source_current*: Any*

Control source current in Amps as a float, truncated from -1.05 to 1.05.

 *property *source_current_range*: Any*

Control source current range in Amps as a float, truncated from -1.05 to 1.05. Setting this property disables auto-range.

 *property *source_delay*: Any*

Control a manual source delay, as a floating value, after output turns on and before a measurement occurs. Setting this property turns auto delay off. Valid values are between 0 [seconds] and 999.9999 [seconds].

 *property *source_delay_auto*: Any*

Control the auto delay (boolean).

 *property *source_enabled*: Any*

Control whether the source is enabled; allowed values are True or False. The convenience methods `enable_source()` and `disable_source()` are also available.

 *property *source_mode*: Any*

Control source mode as a string, with values 'current' or 'voltage'. The convenience methods `apply_current()` and `apply_voltage()` are also available.

 *property *source_voltage*: Any*

Control source voltage in Volts as a float.

 *property *source_voltage_range*: Any*

Control source voltage range in Volts as a float, truncated from -210 to 210. Setting this property disables auto-range.

 *property *standard_devs*: Any*

Return a list of floats containing the buffer-data standard deviations for voltage, current, and resistance.

 start_buffer()

Starts the buffer.

 status()

Return the status byte and Master Summary Status bit.

 *property *std_current

Return the current standard deviation from the buffer.

 *property *std_resistance

Return the resistance standard deviation from the buffer.

 *property *std_voltage

Return the voltage standard deviation from the buffer.

 stop_buffer()

Abort the buffering measurement by stopping the measurement arming and triggering sequence. When possible, uses a Selected Device Clear (SDC).

 triad(*base_frequency*, *duration*)

Play a musical triad with the system beep.

Parameters:

-

**base_frequency** - frequency in Hz from 65 Hz to 1.3 MHz

-

**duration** - time in seconds from 0 to 7.9 seconds

 trigger()

Execute a bus trigger for use when `trigger_on_bus()` is configured.

 *property *trigger_count*: Any*

Control trigger count as an integer, truncated from 1 to 2500.

 *property *trigger_delay*: Any*

Control trigger delay in seconds as a float, truncated from 0 to 999.9999.

 trigger_immediately()

Configure measurements for the internal trigger at the maximum sampling rate.

 trigger_on_bus()

Configure the trigger to detect events from the bus trigger, which `trigger()` can activate.

 trigger_on_external(*line=1*)

Configure the measurement trigger to come from a specific external trigger line.

Parameters:

**line** - trigger line from 1 to 4 (default: `1`)

 use_front_terminals()

Enable the front terminals for measurement and disable the rear terminals.

 use_rear_terminals()

Enable the rear terminals for measurement and disable the front terminals.

 *property *voltage*: Any*

Return voltage in Volts, if configured, as a float.

 *property *voltage_nplc*: Any*

Control the DC voltage measurement NPLC (number of power line cycles), setting integration period and measurement speed. Values run from 0.01 to 10; 0.1, 1, and 10 correspond to Fast, Medium, and Slow.

 *property *voltage_range*: Any*

Control measurement voltage range in Volts as a float, truncated from -210 to 210. Setting this property disables auto-range.

 wait_for(*query_delay=None*)

Wait for a time interval. Used by 'ask' to pause before reading.

Parameters:

**query_delay** (`Optional`[`float`]) - delay in seconds between writing and reading. None means the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*should_stop=<function KeithleyBuffer.<lambda>>*, *timeout=60*, *interval=0.1*)

Block program execution until the buffer is full. This function returns early if `should_stop` returns True, or when timeout is reached before the buffer fills.

Parameters:

-

**should_stop** - function returning True when this function should return early (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

-

**timeout** - time in seconds after which this function should return early (default: `60`)

-

**interval** - seconds between checks of whether the buffer is full (default: `0.1`)

 *property *wires*: Any*

Control number of wires used for resistance measurements; integer, strictly 2 or 4.

 write(*command*, ***kwargs*)

Write a string command to the instrument and append write_termination.

Parameters:

-

**command** (`str`) - command string sent to the instrument

-

**kwargs** - keyword arguments for the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Write binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) - values to transmit.

-

****kwargs** (**args**,*) - additional arguments to pass to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send the bytes content to the instrument.

Return type:

`None`
