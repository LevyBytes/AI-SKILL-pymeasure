# Keithley2450

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Keithley 2450 SourceMeter

 *class *pymeasure.instruments.keithley.Keithley2450(*adapter*, *name='Keithley 2450 SourceMeter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 2450 SourceMeter and exposes a high-level control interface for that instrument.

NOTE: PyMeasure does not currently support the Keithley 2450 model's default buffer-handling SCPI command set. Operation works when the instrument is configured to emulate a 2400 model by selecting 'SCPI 2400' as the command set in the instrument's system settings.

```python
keithley = Keithley2450("GPIB::1")

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

Sets the instrument up to source current, using auto range unless a current range is provided, and sets the compliance voltage.

Parameters:

-

**compliance_voltage** - Float within the allowed `compliance_voltage` range (default: `0.1`)

-

**current_range** - `current_range` value, or None (default: `None`)

 apply_voltage(*voltage_range=None*, *compliance_current=0.1*)

Sets the instrument up to source voltage, using auto range unless a voltage range is provided, and sets the compliance current.

Parameters:

-

**compliance_current** - Float within the allowed `compliance_current` range (default: `0.1`)

-

**voltage_range** - `voltage_range` value, or None (default: `None`)

 auto_range_source()

Sets automatic ranging for the source.

 beep(*frequency*, *duration*)

Sounds a system beep.

Parameters:

-

**frequency** - Frequency in Hz from 65 Hz to 2 MHz

-

**duration** - Duration in seconds from 0 to 7.9 seconds

 *property *buffer_data

Return the buffer contents as a numpy array of values.

 *property *buffer_points*: Any*

Set or read the integer configuration value for buffer points; it is not the count of actual points already in the buffer.

 check_errors()

Retrieve every instrument error.

Returns:

List of error entries.

 check_get_errors()

After a property get, inspect errors and log any found.

Invoked when that property has `check_get_errors=True`.

Overrides of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set, inspect errors and log any found.

Invoked when that property has `check_set_errors=True`.

Overrides of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property supports controller-device synchronization. The Operation Complete query writes an ASCII character 1 to the device's Output Queue after every pending selected device operation has completed.

 *property *compliance_current*: Any*

Set or read the floating compliance current in Amps.

 *property *compliance_voltage*: Any*

Set or read the floating compliance voltage in Volts.

 config_buffer(*points=64*, *delay=0*)

Set up the measurement buffer with a point count and a specified delay.

Parameters:

-

**points** - Number of points in the buffer (default: `64`)

-

**delay** - Delay time in seconds (default: `0`)

 *property *current*: Any*

Return the current in Amps when this reading is configured.

 *property *current_filter_count*: Any*

Set or read the integer count of readings acquired and stored in the filter buffer for averaging.

 *property *current_filter_state*: Any*

Set or read, as a string, whether the filter is active.

 *property *current_filter_type*: Any*

Set or read the current filter type as a String. REP : Repeating filter MOV : Moving filter

 *property *current_nplc*: Any*

Set or read the floating number of power line cycles (NPLC) for DC current measurements. It controls integration period and measurement speed, accepts 0.01 to 10, and maps 0.1, 1, and 10 to Fast, Medium, and Slow respectively.

 *property *current_output_off_state*: Any*

Set or read SourceMeter output behavior. HIMP : opens the output relay, disconnecting external circuitry. NORM : selects V-Source, sets it to 0V, and sets Compliance to 0.5% full scale of the present current range. ZERO : selects V-Source, sets it to 0V, and sets compliance to whichever is greater: the programmed Source I value or 0.5% full scale of the present current range. GUAR : selects I-Source and sets it to 0A

 *property *current_range*: Any*

Set or read the floating measurement current range in Amps; accepted values are between -1.05 and +1.05 A, and setting this property disables auto-range.

 disable_buffer()

Turn off the link between measurements and the buffer without aborting the measurement process.

 disable_source()

Turn off the current or voltage source according to the instrument configuration.

 enable_source()

Turn on the current or voltage source according to the instrument configuration.

 *property *error

Return the next error from the queue.

Since version 0.15, this is deprecated; use next_error instead.

 *property *id*: Any*

Return the instrument identification.

 is_buffer_full()

Return True when the buffer is filled with measurements.

 *property *max_current

Return the buffer's maximum current.

 *property *max_resistance

Return the buffer's maximum resistance.

 *property *max_voltage

Return the buffer's maximum voltage.

 *property *maximums*: Any*

Return a list containing calculated maximum values for voltage, current, and resistance from the buffer data.

 *property *mean_current

Return the buffer's mean current.

 *property *mean_resistance

Return the buffer's mean resistance.

 *property *mean_voltage

Return the buffer's mean voltage.

 *property *means*: Any*

Return a list containing calculated means (averages) for voltage, current, and resistance from the buffer data.

 measure_current(*nplc=1*, *current=0.000105*, *auto_range=True*)

Configures the measurement of current.

Parameters:

-

**nplc** - Power line cycle count (NPLC) for current measurements, from 0.01 to 10 (default: `1`)

-

**current** - Current upper limit in Amps, from -1.05 A to 1.05 A (default: `0.000105`)

-

**auto_range** - If True, enables auto_range; otherwise the set current is used (default: `True`)

 measure_resistance(*nplc=1*, *resistance=210000.0*, *auto_range=True*)

Configures the measurement of resistance.

Parameters:

-

**nplc** - Power line cycle count (NPLC) for resistance measurements, from 0.01 to 10 (default: `1`)

-

**resistance** - Resistance upper limit in Ohms, from -210 MOhms to 210 MOhms (default: `210000.0`)

-

**auto_range** - If True, enables auto_range; otherwise the set resistance is used (default: `True`)

 measure_voltage(*nplc=1*, *voltage=21.0*, *auto_range=True*)

Configures the measurement of voltage.

Parameters:

-

**nplc** - Power line cycle count (NPLC) for voltage measurements, from 0.01 to 10 (default: `1`)

-

**voltage** - Voltage upper limit in Volts, from -210 V to 210 V (default: `21.0`)

-

**auto_range** - If True, enables auto_range; otherwise the set voltage is used (default: `True`)

 *property *min_current

Return the buffer's minimum current.

 *property *min_resistance

Return the buffer's minimum resistance.

 *property *min_voltage

Return the buffer's minimum voltage.

 *property *minimums*: Any*

Return a list containing calculated minimum values for voltage, current, and resistance from the buffer data.

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 ramp_to_current(*target_current*, *steps=30*, *pause=0.02*)

Move from the configured current value to a target current in a specified count of linear steps, pausing between each step.

Parameters:

-

**target_current** - Current in Amps

-

**steps** - Integer step count (default: `30`)

-

**pause** - Pause duration in seconds between steps (default: `0.02`)

 ramp_to_voltage(*target_voltage*, *steps=30*, *pause=0.02*)

Move from the configured voltage value to a target voltage in a specified count of linear steps, pausing between each step.

Parameters:

-

**target_voltage** - Voltage in Amps

-

**steps** - Integer step count (default: `30`)

-

**pause** - Pause duration in seconds between steps (default: `0.02`)

 read(***kwargs*)

Read until, but not including, read_termination; otherwise read the full read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) - Bytes to read. A value of -1 means read the entire read buffer.

-

**kwargs** - Keyword arguments passed to the adapter.

Returns bytes:

Instrument bytes response, including termination.

Return type:

`bytes`

 reset()

Reset the instrument and clear the queue.

 reset_buffer()

Reset the buffer.

 *property *resistance*: Any*

Return the resistance in Ohms when this reading is configured.

 *property *resistance_nplc*: Any*

Set or read the floating number of power line cycles (NPLC) for 2-wire resistance measurements. It controls integration period and measurement speed, accepts 0.01 to 10, and maps 0.1, 1, and 10 to Fast, Medium, and Slow respectively.

 *property *resistance_range*: Any*

Set or read the floating resistance range in Ohms; accepted values run from 0 to 210 MOhms, and setting this property disables auto-range.

 shutdown()

Make sure the current or voltage is brought to zero, then disable the output.

 *property *source_current*: Any*

Set or read the floating source current in Amps.

 *property *source_current_delay*: Any*

Set or read the floating manual source delay after output turns on and before measurement. Setting this property disables auto delay. Valid values are between 0 [seconds] and 999.9999 [seconds].

 *property *source_current_delay_auto*: Any*

Set or read auto delay as a bool. Valid values are True and False.

 *property *source_current_range*: Any*

Set or read the floating source current range in Amps; accepted values are between -1.05 and +1.05 A, and setting this property disables auto-range.

 *property *source_enabled*: Any*

Return a boolean value that is True when the source is enabled.

 *property *source_mode*: Any*

Set or read the source mode as a string; allowed values are 'current' and 'voltage'. You can also use the convenience methods `apply_current()` and `apply_voltage()`.

 *property *source_voltage*: Any*

Set or read the floating source voltage in Volts.

 *property *source_voltage_delay*: Any*

Set or read the floating manual source delay after output turns on and before measurement. Setting this property disables auto delay. Valid values are between 0 [seconds] and 999.9999 [seconds].

 *property *source_voltage_delay_auto*: Any*

Set or read auto delay as a bool. Valid values are True and False.

 *property *source_voltage_range*: Any*

Set or read the floating source voltage range in Volts; accepted values are from -210 to 210 V, and setting this property disables auto-range.

 *property *standard_devs*: Any*

Return a list containing calculated standard deviations for voltage, current, and resistance from the buffer data.

 start_buffer()

Starts the buffer.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 *property *std_current

Return the buffer's current standard deviation.

 *property *std_resistance

Return the buffer's resistance standard deviation.

 *property *std_voltage

Return the buffer's voltage standard deviation.

 stop_buffer()

Abort the buffering measurement by stopping measurement arming and the triggering sequence. When available, Selected Device Clear (SDC) is used.

 triad(*base_frequency*, *duration*)

Play a musical triad through the system beep.

Parameters:

-

**base_frequency** - Frequency in Hz between 65 Hz and 1.3 MHz

-

**duration** - Duration in seconds from 0 to 7.9 seconds

 trigger()

Executes a bus trigger.

 use_front_terminals()

Enable the front terminals for measurement and disable the rear terminals.

 use_rear_terminals()

Enable the rear terminals for measurement and disable the front terminals.

 *property *voltage*: Any*

Return the voltage in Volts when this reading is configured.

 *property *voltage_filter_count*: Any*

Set or read the integer count of readings acquired and stored in the filter buffer for averaging.

 *property *voltage_filter_type*: Any*

Set or read the current filter type as a String. REP : Repeating filter MOV : Moving filter

 *property *voltage_nplc*: Any*

Set or read the floating number of power line cycles (NPLC) for DC voltage measurements. It controls integration period and measurement speed, accepts 0.01 to 10, and maps 0.1, 1, and 10 to Fast, Medium, and Slow respectively.

 *property *voltage_output_off_state*: Any*

Set or read SourceMeter output behavior. HIMP : output relay is open and disconnects external circuitry. NORM : select V-Source, set it to 0V, and set Compliance to 0.5% full scale of the present current range. ZERO : select V-Source, set it to 0V, and set compliance to whichever is greater: the programmed Source I value or 0.5% full scale of the present current range. GUAR : select I-Source and set it to 0A

 *property *voltage_range*: Any*

Set or read the floating measurement voltage range in Volts; accepted values are from -210 to 210 V, and setting this property disables auto-range.

 wait_for(*query_delay=None*)

Wait for a period of time. `ask` uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) - Delay in seconds between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*should_stop=<function KeithleyBuffer.<lambda>>*, *timeout=60*, *interval=0.1*)

Block program execution until the buffer is full. The function returns before that if `should_stop` returns True or if timeout is reached first.

Parameters:

-

**should_stop** - Function whose True result makes this function return early (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

-

**timeout** - Time in seconds after which this function should return early (default: `60`)

-

**interval** - Time in seconds between checks for a full buffer (default: `0.1`)

 *property *wires*: Any*

Set or read the integer wire count used for resistance measurements; accepted values are 2 or 4.

 write(*command*, ***kwargs*)

Send a string command to the instrument, appending write_termination.

Parameters:

-

**command** (`str`) - command string sent to the instrument

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

**values** (`Sequence`[`Union`[`int`, `float`]]) - Values to transmit.

-

****kwargs** (**args**,*) - Additional arguments passed to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send bytes content to the instrument.

Return type:

`None`
