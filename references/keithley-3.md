# Keithley2510, Keithley6221

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Keithley 2510 TEC SourceMeter and Keithley 6221 AC and DC Current Source.

## Keithley 2510 TEC SourceMeter

### Keithley 2510 TEC SourceMeter

 *class *pymeasure.instruments.keithley.Keithley2510(*adapter*, *name='Keithley 2510 TEC SourceMeter'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for working with the Keithley 2510 TEC Sourcemeter instrument.

 check_errors()

Retrieve every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property is read, inspect instrument errors and log any findings.

Runs when `check_get_errors=True` has been configured for that property.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 check_set_errors()

After assigning a property value, inspect instrument errors and log any findings.

Runs when `check_set_errors=True` has been configured for that property.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 check_temperature_stability(*tolerance=0.1*, *period=10*, *points=64*)

Determine whether the measured temperature remains within tolerance of the temperature setpoint for the requested period.

Parameters:

-

**tolerance** â€“ Maximum permitted difference from the temperature setpoint, in degrees Centigrade. (default: `0.1`)

-

**period** â€“ Duration, in seconds, used for the stability check. (default: `10`)

Returns:

True if stable, False otherwise.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the deviceâ€™s Output Queue.

 *property *current*: Any*

Measure DC current through the thermoelectric cooler, in Amps.

 disable_source()

Disables the source.

 disable_temperature_protection()

Disable temperature protection.

 enable_source()

Enables the source.

 enable_temperature_protection()

Enable temperature protection.

 *property *id*: Any*

Return the instrument identification string.

 *property *next_error*: Any*

Return the following queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until read_termination, excluding that terminator, or return the whole read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) â€“ Number of bytes requested. Use -1 to read the whole read buffer.

-

**kwargs** â€“ Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Put the instrument into a safe, stable condition

Return type:

`None`

 *property *source_enabled*: Any*

Use this setting to enable or disable the source (bool). You can also call `enable_source()` and `disable_source()`.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 *property *temperature*: Any*

Measure thermistor temperature, in degrees centigrade.

 *property *temperature_pid

Control the temperature PID loop constants as the tuple (proportional_const, integral_const, derivative_const).

 *property *temperature_pid_d*: Any*

Control the derivative constant for the temperature PID loop.

 *property *temperature_pid_i*: Any*

Control the integral constant for the temperature PID loop.

 *property *temperature_pid_p*: Any*

Control the proportional constant for the temperature PID loop.

 *property *temperature_protection_enabled*: Any*

Use this setting to enable or disable temperature protection. Values are True or False. You can also call `enable_temperature_protection()` and `disable_temperature_protection()`.

 *property *temperature_protection_high*: Any*

Use this setting for the upper limit of temperature in degrees centigrade (float strictly from -50 to 225)

 *property *temperature_protection_low*: Any*

Use this setting for the lower limit of temperature in degrees centigrade (float strictly from -50 to 225)

 *property *temperature_protection_range

Control the lower and upper temperature limits in degrees centigrade with the tuple (lower_limit, upper_limit).

 *property *temperature_setpoint*: Any*

Set or read the temperature setpoint, in degrees centigrade (float strictly from -50 to 225)

 *property *voltage*: Any*

Measure DC voltage through the thermoelectric cooler, in Volts.

 wait_for(*query_delay=None*)

Pause for a short time; â€˜askâ€™ uses it before reading.

Parameters:

**query_delay** (`Optional`[`float`]) â€“ Delay, in seconds, between write and read. None selects the default delay. (default: `None`)

Return type:

`None`

 wait_for_temperature_stable(*tolerance=0.1*, *period=10*, *should_stop=<function Keithley2510.<lambda>>*, *timeout=60*)

Block execution until the temperature reaches stable operation at the temperature setpoint.

Parameters:

-

**tolerance** â€“ Allowed maximum difference from the temperature setpoint, in degrees Centigrade. (default: `0.1`)

-

**period** â€“ Duration, in seconds, over which stability is evaluated. (default: `10`)

-

**should_stop** â€“ Function returning True when waiting should stop. (default: `<function Keithley2510.<lambda> at 0x7aa5835c0880>`)

-

**timeout** â€“ Maximum wait duration, in seconds. (default: `60`)

Returns:

True indicates stable operation; False means should_stop stopped the wait.

Raises:

**TimeoutError** â€“ Raised when the temperature remains unstable for the full timeout period.

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) â€“ command string sent to the instrument

-

**kwargs** â€“ Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) â€“ Values that will be transmitted.

-

****kwargs** (**args**,*) â€“ Additional arguments forwarded to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send bytes content to the instrument.

Return type:

`None`

## Keithley 6221 AC and DC Current Source

### Keithley 6221 AC and DC Current Source

 *class *pymeasure.instruments.keithley.Keithley6221(*adapter*, *name='Keithley 6221 SourceMeter'*, ***kwargs*)

Bases: `KeithleyBuffer`, [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for working with the Keithley 6221 AC and DC current source instrument.

```python
keithley = Keithley6221("GPIB::1")
keithley.clear()

# Use the keithley as an AC source
keithley.waveform_function = "square"   # Set a square waveform
keithley.waveform_amplitude = 0.05      # Set the amplitude in Amps
keithley.waveform_offset = 0            # Set zero offset
keithley.source_compliance = 10         # Set compliance (limit) in V
keithley.waveform_dutycycle = 50        # Set duty cycle of wave in %
keithley.waveform_frequency = 347       # Set the frequency in Hz
keithley.waveform_ranging = "best"      # Set optimal output ranging
keithley.waveform_duration_cycles = 100 # Set duration of the waveform

# Link end of waveform to Service Request status bit
keithley.operation_event_enabled = 128  # OSB listens to end of wave
keithley.srq_event_enabled = 128        # SRQ listens to OSB

keithley.waveform_arm()                 # Arm (load) the waveform

keithley.waveform_start()               # Start the waveform

keithley.adapter.wait_for_srq()         # Wait for the pulse to finish

keithley.waveform_abort()               # Disarm (unload) the waveform

keithley.shutdown()                     # Disables output

```

 beep(*frequency*, *duration*)

Sounds a system beep.

Parameters:

-

**frequency** â€“ Frequency in Hz, constrained between 65 Hz and 2 MHz

-

**duration** â€“ Time in seconds, constrained between 0 and 7.9 seconds

 *property *buffer_data

Return a numpy array containing buffer values.

 *property *buffer_points*: Any*

Control the configured buffer point count. This is the configuration value, not the current number of actual buffer points.

 check_errors()

Retrieve every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property is read, inspect instrument errors and log any findings.

Runs when `check_get_errors=True` has been configured for that property.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 check_set_errors()

After assigning a property value, inspect instrument errors and log any findings.

Runs when `check_set_errors=True` has been configured for that property.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the deviceâ€™s Output Queue.

 config_buffer(*points=64*, *delay=0*)

Configure the measurement buffer with a point count and a specified delay.

Parameters:

-

**points** â€“ Number of points in the buffer. (default: `64`)

-

**delay** â€“ Delay time in seconds. (default: `0`)

 define_arbitary_waveform(*datapoints*, *location=1*)

Define arbitrary waveform data points, then copy that waveform definition to the specified storage location.

Parameters:

-

**datapoints** â€“ list (or numpy array) of data points; every value must be between -1 and 1; 100 points maximum.

-

**location** â€“ integer storage location where the waveform is stored. Value must be in range 1 to 4. (default: `1`)

 delta_abort()

Stop delta and return the Model 2182A to local mode.

 delta_arm()

Arm delta.

 *property *delta_buffer_points*: Any*

Control the buffer size (integer strictly from 1 to 1000000).

Buffer size should match the Delta count value.

 *property *delta_cold_switch_enabled*: Any*

Control whether cold switching mode is enabled (boolean).

 *property *delta_compliance_abort_enabled*: Any*

Control whether compliance abort is enabled (boolean).

 *property *delta_connected*: Any*

Get connection status to 2182A.

 *property *delta_cycles*: Any*

Control the cycle count for delta measurements (integer strictly from 1 to 65536, or â€œINFâ€).

 *property *delta_delay*: Any*

Set or read the delay used by delta measurements, in seconds (float strictly from 0 to 9999.999, or â€œINFâ€).

 *property *delta_high_source*: Any*

For delta high source value, set or read the current in A (float strictly from 0 to 0.105).

Setting the high source value also sets the low source value to the negative of the high source value.

 *property *delta_low_source*: Any*

For delta low source value, set or read the current in A (float strictly from -0.105 to 0).

Manual setting is usually unnecessary; the default makes low source value equal to minus the high source value.

 *property *delta_measurement_sets*: Any*

Control how many measurement sets repeat during delta measurements (integer strictly from 1 to 65536, or â€œINFâ€).

 *property *delta_sense*: Any*

Return the most recent delta reading results from 2182/2182A.

 delta_start()

Start delta measurements.

 *property *delta_unit*: Any*

Set or read the reading unit (string strictly in â€˜Vâ€™, â€˜Ohmsâ€™, â€˜Wâ€™ and â€˜Siemensâ€™).

 *property *delta_values*: Any*

Return delta sense readings stored in the 6221 buffer.

 disable_buffer()

Break the link between measurements and the buffer without aborting the measurement process.

 disable_output_trigger()

Turn off the output trigger for the Trigger layer

 disable_source()

Turn off the current or voltage source according to the instrument configuration.

 *property *display_enabled*: Any*

Control (boolean) display enablement for the sourcemeter. Valid values are True and False.

 enable_source()

Enable the current or voltage source according to the instrument configuration.

 *property *error

Return the following error from the queue.

Deprecated since version 0.15: prefer next_error instead.

 *property *id*: Any*

Return the instrument identification string.

 is_buffer_full()

Return True when the buffer contains a full set of measurements.

 *property *measurement_event_enabled*: Any*

Control which measurement events enter the Measurement Summary Bit (MSB) status bit. See the Model 6220/6221 Reference Manual for details on programming the status bits.

 *property *measurement_events*: Any*

Return the measurement events registered in the Measurement event registers. See the Model 6220/6221 Reference Manual for details on programming the status bits. Reading this value clears the register.

 *property *next_error*: Any*

Return the following queued error. To read and log every error, call `check_errors()` instead.

 *property *operation_event_enabled*: Any*

Control which operation events enter the Operation Summary Bit (OSB) status bit. See the Model 6220/6221 Reference Manual for details on programming the status bits.

 *property *operation_events*: Any*

Return the operation events registered in the Operation event registers. See the Model 6220/6221 Reference Manual for details on programming the status bits. Reading this value clears the register.

 *property *options*: Any*

Get the device options installed.

 *property *output_low_grounded*: Any*

Control (boolean) whether the low output of the triax connection is tied to earth ground (True) or left floating (False).

 output_trigger_on_external(*line=1*, *after='DEL'*)

Configure output triggering for a chosen trigger link line number, optionally naming the measurement phase after which the trigger is produced (default to delay, which is just before measurement)

Parameters:

-

**line** â€“ Trigger line from 1 to 4 (default: `1`)

-

**after** â€“ Event string selecting when to trigger (default: `'DEL'`)

 *property *questionable_event_enabled*: Any*

Control which questionable events enter the Questionable Summary Bit (QSB) status bit. See the Model 6220/6221 Reference Manual for details on programming the status bits.

 *property *questionable_events*: Any*

Return the questionable events registered in the Questionable event registers. See the Model 6220/6221 Reference Manual for details on programming the status bits. Reading this value clears the register.

 read(***kwargs*)

Read until read_termination, excluding that terminator, or return the whole read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) â€“ Number of bytes requested. Use -1 to read the whole read buffer.

-

**kwargs** â€“ Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Reset the instrument and clear the queue.

 reset_buffer()

Reset the buffer.

 set_timed_arm(*interval*)

Configure measurement acquisition with the internal trigger at a variable sampling rate, where interval specifies seconds between sampling points

 *property *shield_to_guard_enabled*: Any*

Control whether shield is connected to the guard(boolean).

Otherwise, shield is connected to the output-low.

 shutdown()

Disables the output.

 *property *source_auto_range*: Any*

Control (boolean) current source auto range. Valid values are True or False.

 *property *source_compliance*: Any*

Control (floating) current source compliance, measured in Volts. Allowed range: 0.1 [V] through 105 [V].

 *property *source_current*: Any*

Control (floating) source current in Amps.

 *property *source_delay*: Any*

Control (floating) manual source delay after output turns on and before measurement. Setting this property turns auto delay off. Valid values are between 1e-3 [seconds] and 999999.999 [seconds].

 *property *source_enabled*: Any*

For source enablement, use a (boolean) value. Accepts True or False. The convenience methods `enable_source()` and `disable_source()` remain available for this setting.

 *property *source_range*: Any*

Control (floating) source current range in Amps, with allowed values between -0.105 A and +0.105 A. Setting this property disables auto-range.

 *property *srq_event_enabled*: Any*

Control which event registers assert the Service Request (SRQ) status bit. See the Model 6220/6221 Reference Manual for details on programming the status bits.

 *property *standard_event_enabled*: Any*

Control which standard events enter the Event Summary Bit (ESB) status bit. See the Model 6220/6221 Reference Manual for details on programming the status bits.

 *property *standard_events*: Any*

Return the standard events registered in the Standard event registers. See the Model 6220/6221 Reference Manual for details on programming the status bits. Reading this value clears the register.

 start_buffer()

Starts the buffer.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 stop_buffer()

Abort buffering measurement by stopping measurement arming and the triggering sequence. When available, a Selected Device Clear (SDC) is used.

 triad(*base_frequency*, *duration*)

Play a musical triad through the system beep.

Parameters:

-

**base_frequency** â€“ Frequency in Hz, constrained between 65 Hz and 1.3 MHz

-

**duration** â€“ Time in seconds, constrained between 0 and 7.9 seconds

 trigger()

Execute a bus trigger for configurations created with `trigger_on_bus()`.

 trigger_immediately()

Configure measurements to use the internal trigger at maximum sampling rate.

 trigger_on_bus()

Configure the trigger to detect events from the bus trigger, activated through `trigger()`.

 trigger_on_external(*line=1*)

Configure the measurement trigger to come from a specified external trigger line

Parameters:

**line** â€“ Trigger line from 1 to 4 (default: `1`)

 wait_for(*query_delay=None*)

Pause for a short time; â€˜askâ€™ uses it before reading.

Parameters:

**query_delay** (`Optional`[`float`]) â€“ Delay, in seconds, between write and read. None selects the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*should_stop=<function KeithleyBuffer.<lambda>>*, *timeout=60*, *interval=0.1*)

Block execution until the buffer is full. This function returns early when `should_stop` returns True or when timeout arrives before the buffer fills.

Parameters:

-

**should_stop** â€“ Predicate checked for early exit; return True to make this function return early (default: `<function KeithleyBuffer.<lambda> at 0x7aa583874f60>`)

-

**timeout** â€“ Time in seconds after which this function should return early (default: `60`)

-

**interval** â€“ Time in seconds between checks for whether the buffer is full (default: `0.1`)

 waveform_abort()

Abort waveform output and disarm the waveform function.

 *property *waveform_amplitude*: Any*

Control (floating) the waveform (peak) amplitude in Amps. Valid values are in range 2e-12 to 0.105.

 waveform_arm()

Arm the current waveform function.

 *property *waveform_duration_cycles*: Any*

Control (floating) waveform duration in cycles. Valid values are in range 1e-3 to 99999999900.

 waveform_duration_set_infinity()

Set waveform duration to infinity.

 *property *waveform_duration_time*: Any*

Control (floating) waveform duration in seconds. Valid values are in range 100e-9 to 999999.999.

 *property *waveform_dutycycle*: Any*

Control (floating) waveform duty-cycle in percent for square and ramp waves. Valid values are in range 0 to 100.

 *property *waveform_frequency*: Any*

Control (floating) waveform frequency in Hertz. Valid values are in range 1e-3 to 1e5.

 *property *waveform_function*: Any*

Control (string) the chosen wave function. Valid values are â€œsineâ€, â€œrampâ€, â€œsquareâ€, â€œarbitrary1â€, â€œarbitrary2â€, â€œarbitrary3â€ and â€œarbitrary4â€.

 *property *waveform_offset*: Any*

Control (floating) waveform offset in Amps. Valid values are in range -0.105 to 0.105.

 *property *waveform_phasemarker_line*: Any*

Control (numerical) the phase marker line.

 *property *waveform_phasemarker_phase*: Any*

Control (numerical) the phase marker phase.

 *property *waveform_ranging*: Any*

Control (string) waveform source ranging. Valid values are â€œbestâ€ and â€œfixedâ€.

 waveform_start()

Start waveform output. It must already be armed

 *property *waveform_use_phasemarker*: Any*

Control (boolean) whether the phase marker option is enabled. Valid values True (on) or False (off). Other phase marker settings are not implemented yet.

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) â€“ command string sent to the instrument

-

**kwargs** â€“ Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) â€“ Values that will be transmitted.

-

****kwargs** (**args**,*) â€“ Additional arguments forwarded to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send bytes content to the instrument.

Return type:

`None`
