# Keithley2400

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Keithley 2400 SourceMeter

 *class *pymeasure.instruments.keithley.Keithley2400(*adapter*, *name='Keithley 2400 SourceMeter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model the Keithley 2400 SourceMeter and expose a high-level interface for instrument communication.

```python
smu = Keithley2400("GPIB::1")
smu.reset()                        # Resets the instrument

smu.source_mode = "current"        # Sets up to source current
smu.source_enabled = True          # Enables the source output

smu.ramp_to_current(5e-3)          # Ramps the current to 5 mA
print(smu.voltage)                 # Prints the voltage in Volts

smu.reset()                        # Resets the instrument

```

 apply_current(*current_range=None*, *compliance_voltage=0.1*)

Set the instrument to source current, using auto range unless `current_range` is supplied, and configure the compliance voltage.

Parameters:

-

**compliance_voltage** ? Float value in the valid `compliance_voltage` range (default: `0.1`)

-

**current_range** ? A `current_range` value, or None (default: `None`)

Deprecated since version 0.16: Configure - source mode with `source_mode`. - source current range with `source_current_range` or `source_current_range_auto_enabled`. - compliance voltage with `compliance_voltage`

 apply_voltage(*voltage_range=None*, *compliance_current=0.1*)

Set the instrument to source voltage, using auto range unless `voltage_range` is supplied, and configure the compliance current.

Parameters:

-

**compliance_current** ? Float value in the valid `compliance_current` range (default: `0.1`)

-

**voltage_range** ? A `voltage_range` value, or None (default: `None`)

Deprecated since version 0.16: Prefer configuring - source mode with `source_mode`. - source voltage range with `source_voltage_range` or `source_voltage_range_auto_enabled`. - compliance current with `compliance_current`

 *property *arm_count

Set the arm layer count (int strictly in range 1 to 2500). `trigger_count` multiplied by `arm_count` must not be greater than 2500.

 *property *arm_input_line*: Any*

Set the arm layer input line (int, strictly in range 1 to 4).

During normal use, choose an `arm_input_line` value different from `trigger_output_line` and `arm_output_line`.

 *property *arm_output_event*: Any*

Set when the arm layer output trigger line emits a trigger pulse (str, strictly ?trigger_enter?, ?trigger_exit?, or ?none?).

 *property *arm_output_line*: Any*

Set the arm layer output line (int, strictly in range 1 to 4).

During normal use, choose an `arm_output_line` value different from `trigger_input_line` and `arm_input_line`.

 *property *arm_source*: Any*

Choose the arm layer event-control source (str; allowed values are ?immediate?, ?trigger_link?, ?timer?, ?manual?, or ?bus?).

 *property *arm_timer*: Any*

Provide the arm layer timer as a float in seconds; valid range is 0.001 to 99999.99.

 *property *auto_output_off*: Any*

Enable or disable auto output-off. True turns the output off after measurement; False leaves output on after measurement.

Deprecated since version 0.16: Use `auto_output_off_enabled` instead.

 *property *auto_output_off_enabled*: Any*

Enable or disable auto output-off behavior (bool).

Warning

If auto output-off is disabled (False), source-measure operations leave the output on afterward.

 auto_range_source()

Put the source range selection into automatic mode.

Deprecated since version 0.16: Use `source_current_range_auto_enabled` or `source_voltage_range_auto_enabled` to manage auto ranging for the selected source.

 *property *auto_zero*: Any*

Enable or disable auto zero. Valid values are True (enabled), False (disabled), and ?ONCE? (force immediate).

Deprecated since version 0.16: Use `auto_zero_enabled` or `auto_zero_once()` instead.

 *property *auto_zero_enabled*: Any*

Enable or disable auto zeroing (bool)

 beep(*frequency*, *duration*)

Sound a system beep.

Parameters:

-

**frequency** ? Frequency in Hz from 65 Hz through 2 MHz

-

**duration** ? Time in seconds from 0 through 7.9 seconds

 *property *buffer_data

Return buffer values as a numpy array.

 *property *buffer_points*: Any*

Set the configured number of buffer points; this is the configuration setting, not the current count of stored buffer points.

 check_errors()

Retrieve every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After reading a property, check for errors and log any that are found.

Invoked when that property has `check_get_errors=True`.

Override this method if selected errors should be raised as an Exception.

Returns:

`list` – List of error entries.

 check_set_errors()

After writing a property, check for errors and log any that are found.

Invoked when that property has `check_set_errors=True`.

Override this method if selected errors should be raised as an Exception.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 clear_trigger()

Immediately clear pending input triggers.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. After all selected pending device operations finish, the Operation Complete query puts ASCII character 1 in the device's Output Queue.

 *property *compliance_current*: Any*

Configure the compliance-current limit, in Amps. Accepted float values are strictly from -1.05 to 1.05.

 *property *compliance_voltage*: Any*

Set the compliance voltage in Volts (float, strictly from -210 to 210).

 config_buffer(*points=64*, *delay=0*)

Prepare the measurement buffer for a specified point count and delay.

Parameters:

-

**points** ? Number of points assigned to the buffer. (default: `64`)

-

**delay** ? Delay duration in seconds. (default: `0`)

 *property *current*: Any*

Read current in Amps (float).

 *property *current_nplc*: Any*

Configure NPLC, the power line cycle count, as a float from 0.01 to 10.

Note

This global command also sets `voltage_nplc` and `resistance_nplc`.

 *property *current_range*: Any*

Set the current measurement range in Amps (float, strictly from -1.05 to 1.05).

When assigned, the instrument chooses the most sensitive range that can hold the set value, and `current_range_auto_enabled` is set to False.

 *property *current_range_auto_enabled*: Any*

Enable or disable current measurement auto-range (bool).

 disable_buffer()

Disconnect measurements from the buffer without aborting the measurement process.

 disable_output_trigger()

Turn off the output trigger for the Trigger layer

Deprecated since version 0.16: To turn off only trigger layer output triggering, set `trigger_output_event` to ?none?; to disable both trigger and arm layer output triggering, use ~.disable_output_triggers.

 disable_output_triggers()

Turn off the output trigger for the Trigger layer

 disable_source()

Disable the source.

 *property *display_enabled*: Any*

Enable or disable the sourcemeter display (bool).

 enable_source()

Enable the source.

 *property *error

Return the next queued instrument error.

Deprecated since version 0.15: Use next_error instead.

 *property *filter_count*: Any*

Set how many readings are acquired into the filter buffer (int, strictly from 1 to 100).

 *property *filter_enabled*: Any*

Enable or disable the filter (bool).

 *property *filter_state*: Any*

Set filter activity as a string, strictly ?ON? or ?OFF?.

Deprecated since version 0.16: Use `filter_enabled` instead.

 *property *filter_type*: Any*

Set the filter type (String). REP : repeat filtering; MOV : moving filtering.

Deprecated since version 0.16: Use `repeat_filter_enabled` instead.

 *property *front_terminals_enabled*: Any*

Select terminal routing (bool). True routes the front terminals and disconnects the rear terminals; False reverses that selection.

 *property *id*: Any*

Return the instrument identification string.

 is_buffer_full()

Return True when the measurement buffer is full.

 *property *line_frequency*: Any*

Set line frequency in Hertz (int, strictly 50 or 60).

 *property *line_frequency_auto*: Any*

Enable or disable automatic line-frequency selection (boolean).

Deprecated since version 0.16: Use `auto_zero_enabled` or `auto_zero_once()` instead.

 *property *line_frequency_auto_enabled*: Any*

Enable or disable auto line frequency (bool).

 *property *max_current

Return the largest current value in the buffer (float).

 *property *max_resistance

Return the largest resistance value in the buffer (float).

 *property *max_voltage

Return the largest voltage value in the buffer (float).

 *property *maximums*: Any*

Return calculated maxima for voltage, current, and resistance from buffer data (list of floats).

 *property *mean_current

Return the buffer mean current (float).

 *property *mean_resistance

Return the buffer mean resistance (float).

 *property *mean_voltage

Return the buffer mean voltage (float).

 *property *means*: Any*

Return calculated means for voltage, current, and resistance from buffer data (list of floats).

 measure_all()

Acquire current (A), voltage (V), resistance (Ohm), time (s), and status in one operation.

Note

Also sets `resistance_mode_auto` to False

### Returns

dict

Dictionary containing these keys: - ?current? (float): current in A. - ?voltage? (float): voltage in V. - ?resistance? (float): resistance in Ohms. - ?time? (float): elapsed time in s. - ?status? (int): status flag from the instrument.

 measure_current(*nplc=1*, *current=0.000105*, *auto_range=True*)

Configure the measurement of current.

Parameters:

-

**nplc** ? NPLC power-line-cycle setting, from 0.01 to 10 (default: `1`)

-

**current** ? Upper current limit in Amps, from -1.05 A to 1.05 A (default: `0.000105`)

-

**auto_range** ? Turns on auto_range when True; otherwise uses the supplied current (default: `True`)

Deprecated since version 0.16: Current measurement setup now happens implicitly through `current`. Prefer - current nplc through `current_nplc`. - current range through `current_range` or `current_range_auto_enabled`.

 measure_resistance(*nplc=1*, *resistance=210000.0*, *auto_range=True*)

Configure the measurement of resistance.

Parameters:

-

**nplc** ? NPLC power-line-cycle setting, from 0.01 to 10 (default: `1`)

-

**resistance** ? Upper resistance limit in Ohms, from -210 MOhms to 210 MOhms (default: `210000.0`)

-

**auto_range** ? Turns on auto_range when True; otherwise uses the supplied resistance (default: `True`)

Deprecated since version 0.16: Resistance measurement setup now happens implicitly through `resistance`. Instead: - set resistance nplc with `resistance_nplc`. - set resistance range with `resistance_range` or `resistance_range_auto_enabled`.

 measure_voltage(*nplc=1*, *voltage=21.0*, *auto_range=True*)

Configure the measurement of voltage.

Parameters:

-

**nplc** ? NPLC power-line-cycle setting, from 0.01 to 10 (default: `1`)

-

**voltage** ? Upper voltage limit in Volts, from -210 V to 210 V (default: `21.0`)

-

**auto_range** ? Turns on auto_range when True; otherwise uses the supplied voltage (default: `True`)

Deprecated since version 0.16: Voltage measurement setup now happens implicitly through `voltage`. Prefer - voltage nplc through `voltage_nplc`. - voltage range through `voltage_range` or `voltage_range_auto_enabled`.

 *property *min_current

Return the smallest current value in the buffer (float).

 *property *min_resistance

Return the smallest resistance value in the buffer (float).

 *property *min_voltage

Return the smallest voltage value in the buffer (float).

 *property *minimums*: Any*

Return calculated minima for voltage, current, and resistance from buffer data (list of floats).

 *property *next_error*: Any*

Return the next queued error. To read and log the full queue, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *output_off_state*: Any*

Control the output-off state.

str:

-

?disconnected?: Opens the output relay; avoid this state for frequent output on/off cycling to limit relay wear.

-

?normal?: Selects the V-source and sets it to 0V.

-

?zero?: Lets the sourcemeter measure current while the output is off.

-

?guard?: Selects the I-source and sets it to 0A.

Deprecated since version 0.16: Do not use ?HIMP?, ?NORM?, ?ZERO?, or ?GUAR? with `output_off_state`.

 output_trigger_on_external(*line=1*, *after='DEL'*)

Configure output triggering on the selected trigger link line number, optionally choosing the measurement phase after which the trigger is generated (default to delay, immediately before measurement).

Parameters:

-

**line** ? Trigger line from 1 to 4 (default: `1`)

-

**after** ? Event string specifying trigger timing (default: `'DEL'`)

Deprecated since version 0.16: Use `trigger_output_event` and `trigger_output_line` instead.

 ramp_to_current(*target_current*, *steps=30*, *pause=0.02*)

Move from the set current value to the target current in linear steps, waiting the pause duration between steps.

Parameters:

-

**target_current** ? Current value in Amps

-

**steps** ? Integer count of steps (default: `30`)

-

**pause** ? Pause duration in seconds between steps (default: `0.02`)

 ramp_to_voltage(*target_voltage*, *steps=30*, *pause=0.02*)

Move from the present voltage value to the target voltage in linear steps, waiting the pause duration between steps.

Parameters:

-

**target_voltage** ? Voltage value in Amps

-

**steps** ? Integer count of steps (default: `30`)

-

**pause** ? Pause duration in seconds between steps (default: `0.02`)

 read(***kwargs*)

Read until just before read_termination, or read the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) ? Bytes to read. A value of -1 means read the complete read buffer.

-

**kwargs** ? Keyword arguments forwarded to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 *property *repeat_filter_enabled*: Any*

Enable or disable repeat filtering (bool). If False, the moving filter is selected.

 reset()

Reset the instrument.

 reset_buffer()

Reset the buffer.

 reset_data_format()

Restore the data format expected by `Keithley2400`.

Expected data format: [<current>, <voltage>, <resistance>, <time>, <status>].

Caution

Changing the data format after initialization with the ?:FORMAT:ELEMENTS? command can cause parts of `Keithley2400` to fail.

 reset_trigger()

Reset the trigger system, returning it to idle.

 *property *resistance*: Any*

Read resistance in Ohms (float).

 *property *resistance_mode_auto_enabled*: Any*

Enable or disable resistance mode auto status (bool).

When True, the selected resistance_range determines source_current and voltage_range. When False, source_current and voltage_range are set manually.

 *property *resistance_nplc*: Any*

Configure NPLC, the power line cycle count, as a float from 0.01 to 10.

Note

This global command also sets `current_nplc` and `voltage_nplc`.

 *property *resistance_range*: Any*

Set the resistance range in Ohms (float, strictly from 0 to 210e6).

When assigned, the instrument chooses the most sensitive range that can hold the set value, and `resistance_range_auto_enabled` is set to False.

 *property *resistance_range_auto_enabled*: Any*

Enable or disable resistance measurement auto-range (bool).

 sample_continuously()

Make the instrument read samples continuously and disable any buffer or output triggering.

 set_timed_arm(*interval*)

Configure measurement with the internal trigger at a variable sampling rate, where the interval in seconds separates sampling points.

Deprecated since version 0.16: Set `arm_source` to ?time? and use `arm_timer` to control the interval instead.

 set_trigger_counts(*arm*, *trigger*)

Set counts for both sweeps (arm) and points within each sweep (trigger); total points can not exceed 2500

Deprecated since version 0.16: Use `trigger_count` and/or `arm_count` instead

 shutdown()

Bring current or voltage to zero, then disable the output.

 *property *source_current*: Any*

Configure the sourced current, in Amps. Accepted float values are strictly from -1.05 to 1.05.

 *property *source_current_range*: Any*

Configure the range used for sourced current, in Amps. Accepted float values are strictly from -1.05 to 1.05.

When assigned, the instrument chooses the most sensitive range that can hold the set value, and Auto-range is disabled.

 *property *source_current_range_auto_enabled*: Any*

Enable or disable source current auto-range (bool).

 *property *source_delay*: Any*

Set the manual source delay, in seconds, between output enablement and measurement (float strictly from 0 to 999.9999).

Assigning this property also sets `source_delay_auto_enabled` to False.

 *property *source_delay_auto*: Any*

Control the auto delay (boolean).

Deprecated since version 0.16: Use `source_delay_auto_enabled` instead.

 *property *source_delay_auto_enabled*: Any*

Enable or disable source auto delay (bool).

 *property *source_enabled*: Any*

Enable or disable the source (bool).

 *property *source_mode*: Any*

Set the source mode (str, strictly ?current? or ?voltage?).

 *property *source_voltage*: Any*

Set the source voltage in Volts (float, strictly from -210 to 210).

 *property *source_voltage_range*: Any*

Set the source voltage range in Volts (float, strictly from -210 to 210).

When assigned, the instrument chooses the most sensitive range that can hold the set value, and Auto-range is disabled.

 *property *source_voltage_range_auto_enabled*: Any*

Enable or disable source voltage auto-range (bool).

 *property *standard_devs*: Any*

Return calculated standard deviations for voltage, current, and resistance from buffer data (list of floats).

 start_buffer()

Starts the buffer.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 *property *std_current

Return the current standard deviation from the buffer (float).

 *property *std_resistance

Return the resistance standard deviation from the buffer (float).

 *property *std_voltage

Return the voltage standard deviation from the buffer.

 stop_buffer()

Abort the buffered measurement by stopping the arming and triggering sequence; when available, Selected Device Clear (SDC) is used.

 triad(*base_frequency*, *duration*)

Play a musical triad through the system beep.

Parameters:

-

**base_frequency** ? Frequency in Hz from 65 Hz through 1.3 MHz

-

**duration** ? Time in seconds from 0 through 7.9 seconds

 trigger()

Issue a bus trigger for configurations made with `trigger_on_bus()`.

 *property *trigger_count

Set the trigger layer count (int strictly in range 1 to 2500). `trigger_count` multiplied by `arm_count` must not be greater than 2500.

 *property *trigger_delay*: Any*

Provide the trigger layer delay as seconds; value is a float strictly in range 0 to 999.9999.

 trigger_immediately()

Configure measurements to use the internal trigger at the highest sampling rate.

 *property *trigger_input_line*: Any*

Set the trigger layer input line (int, strictly in range 1 to 4).

During normal use, choose a `trigger_input_line` value different from `trigger_output_line` and `arm_output_line`.

 trigger_on_bus()

Configure trigger detection for bus-trigger events, activated with `trigger()`.

 trigger_on_external(*line=1*)

Configure the measurement trigger to come from a selected external trigger line

Parameters:

**line** ? Trigger line from 1 to 4 (default: `1`)

 *property *trigger_output_event*: Any*

Set when the trigger layer output trigger line emits a pulse (str, strictly ?source?, ?delay?, ?sense?, or ?none?).

 *property *trigger_output_line*: Any*

Set the trigger layer output line (int, strictly in range 1 to 4).

During normal use, choose a `trigger_output_line` value different from `trigger_input_line` and `arm_input_line`.

 *property *trigger_source*: Any*

Select the trigger layer event-control source (str, strictly ?immediate? or ?trigger_link?).

 use_front_terminals()

Route measurement to the front terminals and disconnect the rear terminals.

Deprecated since version 0.16: Set `front_terminals_enabled` to True instead.

 use_rear_terminals()

Route measurement to the rear terminals and disconnect the front terminals.

Deprecated since version 0.16: Set `front_terminals_enabled` to False instead.

 *property *voltage*: Any*

Read voltage in Volts (float).

 *property *voltage_nplc*: Any*

Configure NPLC, the power line cycle count, as a float from 0.01 to 10.

Note

This global command also sets `current_nplc` and `resistance_nplc`.

 *property *voltage_range*: Any*

Set the voltage measurement range in Volts (float, strictly from -210 to 210).

When assigned, the instrument chooses the most sensitive range that can hold the set value, and `voltage_range_auto_enabled` is set to False.

 *property *voltage_range_auto_enabled*: Any*

Enable or disable voltage measurement auto-range (bool).

 wait_for(*query_delay=None*)

Pause for a period; ?ask? uses this wait before reading.

Parameters:

**query_delay** (`Optional`[`float`]) ? Delay between writing and reading, in seconds. None uses the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*should_stop=<function KeithleyBuffer.<lambda>>*, *timeout=60*, *interval=0.1*)

Block until the buffer is full. The call returns sooner if `should_stop` returns True or if `timeout` expires first.

Parameters:

-

**should_stop** ? Early-exit callback; returning True ends the wait before the buffer is full (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

-

**timeout** ? Time in seconds after which this function returns early (default: `60`)

-

**interval** ? Time in seconds between buffer-full checks (default: `0.1`)

 *property *wires*: Any*

Set wire count (int, strictly 2 or 4) for voltage sourcing, voltage measurement, or resistance measurement.

 write(*command*, ***kwargs*)

Send a string command to the instrument and append write_termination.

Parameters:

-

**command** (`str`) ? command string sent to the instrument

-

**kwargs** ? Keyword arguments forwarded to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) ? Values to transmit.

-

****kwargs** (**args**,*) ? Additional arguments passed through to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send bytes content to the instrument.

Return type:

`None`
