# Virtualbench

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### NI Virtual Bench

### General Information

Use [armstrap/pyvirtualbench](https://github.com/armstrap/armstrap-pyvirtualbench), the Python binding for the VirtualBench C-API. This Instrument driver talks through that pyvirtualbench Python wrapper only.

### Examples

Documentation is still pending; see the pyvirtualbench repository examples for usage patterns.

Minimal example for toggling DIO module digital lines.

```python
from pymeasure.instruments.ni import VirtualBench

vb = VirtualBench(device_name='VB8012-3057E1C')
line = 'dig/2'  # may be list of lines
# initialize DIO module -> available via vb.dio
vb.acquire_digital_input_output(line, reset=False)

vb.dio.write(self.line, {True})
sleep(1000)
vb.dio.write(self.line, {False})

vb.shutdown()

```

### Instrument Class

 *class *pymeasure.instruments.ni.virtualbench.VirtualBench(*device_name=''*, *name='VirtualBench'*)

Bases: `object`

Represents National Instruments Virtual Bench main frame.

The module-specific behavior is supplied by subclasses:

>
-

Mixed-Signal-Oscilloscope (MSO)

-

Digital Input Output (DIO)

-

Function Generator (FGEN)

-

Power Supply (PS)

-

Serial Peripheral Interface (SPI) -> not currently implemented in pymeasure

-

Inter Integrated Circuit (I2C) -> not currently implemented in pymeasure

Each module has file-based save/load configuration methods. Those wrappers are not present yet; see the pyvirtualbench file for details.

Calibration classes and methods are not currently wrapped because they are rarely needed. Network connection support is also absent; consult the pyvirtualbench file when that capability is required.

Parameters:

-

**device_name** (*str*) – Full unique device name

-

**name** (*str*) ? Display label used by pymeasure

 *class *DigitalInputOutput(*virtualbench*, *lines*, *reset*, *vb_name=''*)

Bases: `VirtualBenchInstrument`

Models the Virtual Bench device Digital Input Output (DIO) Module. It can read or write digital channels and assign channels to export the FGEN module start signal or the MSO module trigger.

 export_signal(*line*, *digitalSignalSource*)

Routes a signal onto the requested line.

Parameters:

-

**line** (*str*) – Line string

-

**digitalSignalSource** (*int*) ? use `0` for FGEN start or `1` for MSO trigger

 query_export_signal(*line*)

Reports which signal is routed through the specified line.

Parameters:

**line** (*str*) – Line string

Returns:

Signal exported from FGEN start or MSO trigger

Return type:

enum

 query_line_configuration()

Reports current line setup. Tristate Lines, Static Lines, and Export Lines include comma-separated range_data and/or colon-delimited lists for all acquired lines

 read(*lines*)

Gets the present state for the requested lines.

Parameters:

**lines** (*str*) ? Line string; use the complete name such as `'VB8012-xxxxxxx/dig/0:7'` because instrument_handle is not required (only library_handle)

Returns:

Line state list (HIGH/LOW)

Return type:

list

 reset_instrument()

Restores default session configuration and returns the device plus driver software to a known state.

 shutdown()

Closes the session and releases resources allocated during it. Enabled channel outputs stay at their existing levels.

 tristate_lines(*lines*)

Places every specified line into high-impedance mode. (Default)

 validate_lines(*lines*, *return_single_lines=False*, *validate_init=False*)

Validate lines string Allowed patterns (case sensitive):

>
-

`'VBxxxx-xxxxxxx/dig/0:7'`

-

`'VBxxxx-xxxxxxx/dig/0'`

-

`'dig/0'`

-

`'VBxxxx-xxxxxxx/trig'`

-

`'trig'`

Allowed Line Numbers: 0-7 or trig

Parameters:

-

**lines** (*str*) ? Line string being checked

-

**return_single_lines** (*bool**, **optional*) ? Also return a list of line numbers, defaults to False (default: `False`)

-

**validate_init** (*bool**, **optional*) ? Verify that lines are initialized in `self._line_numbers`, defaults to False (default: `False`)

Returns:

Line string, with optional single-line-number list

Return type:

str, optional (str, list)

 write(*lines*, *data*)

Sends data values to the requested lines.

Parameters:

-

**lines** (*str*) – Line string

-

**data** (*list** or **tuple*) ? Data list where `True` = High and `False` = Low

 *class *DigitalMultimeter(*virtualbench*, *reset*, *vb_name=''*)

Bases: `VirtualBenchInstrument`

Models the Virtual Bench device Digital Multimeter (DMM) Module. It supports DC/AC voltage or current, Resistance, and Diodes measurements.

 configure_ac_current(*auto_range_terminal*)

Set the auto range terminal used for AC current measurement

Parameters:

**auto_range_terminal** ? Terminal used for auto ranging (`'LOW'` or `'HIGH'`)

 configure_dc_current(*auto_range_terminal*)

Set the auto range terminal used for DC current measurement

Parameters:

**auto_range_terminal** ? Terminal used for auto ranging (`'LOW'` or `'HIGH'`)

 configure_dc_voltage(*dmm_input_resistance*)

Configure DC voltage input resistance

Parameters:

**dmm_input_resistance** (*int** or **str*) ? Input resistance selection (`'TEN_MEGA_OHM'` or `'TEN_GIGA_OHM'`)

 configure_measurement(*dmm_function*, *auto_range=True*, *manual_range=1.0*)

Set up the Instrument for a DMM measurement

Parameters:

-

**name** (*dmm_function:DMM function index or*) ?
  -

`'DC_VOLTS'`, `'AC_VOLTS'`

  -

`'DC_CURRENT'`, `'AC_CURRENT'`

  -

`'RESISTANCE'`

  -

`'DIODE'`

-

**auto_range** (*bool*) – Enable/Disable auto ranging

-

**manual_range** (*float*) – Manually set measurement range

 query_ac_current()

Reports the auto range terminal configured for AC current measurement

 query_dc_current()

Reports the auto range terminal configured for DC current measurement

 query_dc_voltage()

Reports the input resistance selected for DC voltage measurement

 query_measurement()

Reads DMM measurement settings from the instrument

Returns:

Auto range, range data

Return type:

(bool, float)

 read()

Reads a measurement value from the instrument

Returns:

Measurement value

Return type:

float

 reset_instrument()

Restore the DMM module default settings

 shutdown()

Closes the session and releases resources allocated during it. Enabled channel outputs stay at their existing levels.

 validate_auto_range_terminal(*auto_range_terminal*)

Validate the value used to select the auto range terminal for DC current measurement

Parameters:

**auto_range_terminal** (*int** or **str*) ? Terminal used for auto ranging (`'LOW'` or `'HIGH'`)

Returns:

Auto range terminal value supplied to the instrument

Return type:

int

 validate_dmm_function(*dmm_function*)

Determine whether DMM function *dmm_function* is available

Parameters:

**dmm_function** (*int** or **str*) –

DMM function index or name:

-

`'DC_VOLTS'`, `'AC_VOLTS'`

-

`'DC_CURRENT'`, `'AC_CURRENT'`

-

`'RESISTANCE'`

-

`'DIODE'`

Returns:

DMM function index supplied to the instrument

Return type:

int

 *static *validate_range(*dmm_function*, *range*)

Validates `range` against the selected `dmm_function`

Parameters:

-

**dmm_function** (*int*) – DMM Function

-

**range** (*int** or **float*) ? Range value, for example the maximum measurable value

Returns:

Range value supplied to instrument

Return type:

int

 *class *FunctionGenerator(*virtualbench*, *reset*, *vb_name=''*)

Bases: `VirtualBenchInstrument`

Models the Virtual Bench device Function Generator (FGEN) Module.

 configure_arbitrary_waveform(*waveform*, *sample_period*)

Sets the instrument to generate a waveform. When output is already enabled, the new waveform follows the current one; otherwise it starts as soon as output is enabled.

Parameters:

-

**waveform** (*list*) ? Waveform represented as a list of values

-

**sample_period** (*float*) ? Time spacing between waveform points (maximum of 125MS/s, which equals 80ns)

 configure_arbitrary_waveform_gain_and_offset(*gain*, *dc_offset*)

Sets arbitrary waveform output with the requested gain and offset. If output is already active, it begins after the current waveform ends; otherwise it begins when output is enabled.

Parameters:

-

**gain** (*float*) ? Gain multiplier applied to waveform values

-

**dc_offset** (*float*) ? DC offset value in volts

 configure_standard_waveform(*waveform_function*, *amplitude*, *dc_offset*, *frequency*, *duty_cycle*)

Sets a standard waveform output on the instrument. Refer to the instrument manual for load-dependent maximum ratings.

Parameters:

-

**waveform_function** (*int** or **str*) ? Waveform function choice (`"SINE", "SQUARE", "TRIANGLE/RAMP", "DC"`)

-

**amplitude** (*float*) – Amplitude in volts

-

**dc_offset** (*float*) ? DC offset value in volts

-

**frequency** (*float*) – Frequency in Hz

-

**duty_cycle** (*int*) ? Duty cycle expressed in %

 *property *filter

Turns the instrument filter on or off.

Parameters:

**enable_filter** (*bool*) – Enable/Disable filter

 query_arbitrary_waveform()

Reports the samples per second used for arbitrary waveform generation.

Returns:

Samples per second

Return type:

int

 query_arbitrary_waveform_gain_and_offset()

Reports arbitrary waveform generation settings, including gain and offset.

Returns:

Gain, DC offset

Return type:

(float, float)

 query_generation_status()

Reports the instrument waveform-generation status.

Returns:

Status

Return type:

enum

 query_standard_waveform()

Reports the configuration used for standard waveform generation.

Returns:

Waveform function, amplitude, dc_offset, frequency, duty_cycle

Return type:

(enum, float, float, float, int)

 query_waveform_mode()

Reports whether the instrument output waveform is standard or arbitrary.

Returns:

Waveform mode

Return type:

enum

 reset_instrument()

Restores default session configuration and returns the device plus driver software to a known state.

 run()

Moves the session from Stopped state into Running state.

 self_calibrate()

Runs offset nulling calibration on the device. FGEN Initialize must be run before calling this method.

 shutdown()

Closes the session and releases resources allocated during it. Enabled channel outputs stay at their existing levels.

 stop()

Moves acquisition from Triggered or Running state into Stopped state.

 *class *MixedSignalOscilloscope(*virtualbench*, *reset*, *vb_name=''*)

Bases: `VirtualBenchInstrument`

Models the Virtual Bench device Mixed Signal Oscilloscope (MSO) Module. It measures oscilloscope data from analog and digital channels.

pyvirtualbench methods not yet implemented in pymeasure:

>
-

`enable_digital_channels`

-

`configure_digital_threshold`

-

`configure_advanced_digital_timing`

-

`configure_state_mode`

-

`configure_digital_edge_trigger`

-

`configure_digital_pattern_trigger`

-

`configure_digital_glitch_trigger`

-

`configure_digital_pulse_width_trigger`

-

`query_digital_channel`

-

`query_enabled_digital_channels`

-

`query_digital_threshold`

-

`query_advanced_digital_timing`

-

`query_state_mode`

-

`query_digital_edge_trigger`

-

`query_digital_pattern_trigger`

-

`query_digital_glitch_trigger`

-

`query_digital_pulse_width_trigger`

-

`read_digital_u64`

 auto_setup()

Automatically configure the instrument

 configure_analog_channel(*channel*, *enable_channel*, *vertical_range*, *vertical_offset*, *probe_attenuation*, *vertical_coupling*)

Configure analog measurement channel

Parameters:

-

**channel** (*str*) – Channel string

-

**enable_channel** (*bool*) – Enable/Disable channel

-

**vertical_range** (*float*) ? Vertical measurement range (0V - 20V); the instrument snaps to `[20, 10, 5, 2, 1, 0.5, 0.2, 0.1, 0.05]`, with each entry equal to 5x the value displayed in the native UI.

-

**vertical_offset** (*float*) ? Vertical offset correction (inverted compared to VB native UI, -20V - +20V, resolution 0.1mV)

-

**probe_attenuation** (*int** or **str*) ? Probe attenuation choice (`'ATTENUATION_10X'` or `'ATTENUATION_1X'`)

-

**vertical_coupling** (*int** or **str*) ? Vertical coupling choice (`'AC'` or `'DC'`)

 configure_analog_channel_characteristics(*channel*, *input_impedance*, *bandwidth_limit*)

Set electrical characteristics for the specified channel

Parameters:

-

**channel** (*str*) – Channel string

-

**input_impedance** (*int** or **str*) ? Input Impedance choice (`'ONE_MEGA_OHM'` or `'FIFTY_OHMS'`)

-

**bandwidth_limit** (*int*) ? Bandwidth limit value (100MHz or 20MHz)

 configure_analog_edge_trigger(*trigger_source*, *trigger_slope*, *trigger_level*, *trigger_hysteresis*, *trigger_instance*)

Sets a trigger on the specified source that fires when the analog edge reaches the specified levels.

Parameters:

-

**trigger_source** (*str*) – Channel string

-

**trigger_slope** (*int** or **str*) ? Trigger slope selection (`'RISING'`, `'FALLING'` or `'EITHER'`)

-

**trigger_level** (*float*) – Trigger level

-

**trigger_hysteresis** (*float*) – Trigger hysteresis

-

**trigger_instance** (*int** or **str*) ? Trigger instance

 configure_analog_pulse_width_trigger(*trigger_source*, *trigger_polarity*, *trigger_level*, *comparison_mode*, *lower_limit*, *upper_limit*, *trigger_instance*)

Creates an analog pulse-width trigger for the requested source; the edge must hit the configured levels within the configured time window.

Parameters:

-

**trigger_source** (*str*) – Channel string

-

**trigger_polarity** (*int** or **str*) ? Trigger slope selection (`'POSITIVE'` or `'NEGATIVE'`)

-

**trigger_level** (*float*) – Trigger level

-

**comparison_mode** (*int** or **str*) ? Comparison mode (`'GREATER_THAN_UPPER_LIMIT'`, `'LESS_THAN_LOWER_LIMIT'`, `'INSIDE_LIMITS'` or `'OUTSIDE_LIMITS'`)

-

**lower_limit** (*float*) – Lower limit

-

**upper_limit** (*float*) – Upper limit

-

**trigger_instance** (*int** or **str*) ? Trigger instance

 configure_immediate_trigger()

Sets an immediate trigger on the specified channels once pretrigger time has elapsed.

 configure_timing(*sample_rate*, *acquisition_time*, *pretrigger_time*, *sampling_mode*)

Set MSO timing settings

Parameters:

-

**sample_rate** (*int*) – Sample rate (15.26kS - 1GS)

-

**acquisition_time** (*float*) – Acquisition time (1ns - 68.711s)

-

**pretrigger_time** (*float*) – Pretrigger time (0s - 10s)

-

**sampling_mode** ? Sampling mode selection (`'SAMPLE'` or `'PEAK_DETECT'`)

 configure_trigger_delay(*trigger_delay*)

Sets how long to wait after the trigger condition is satisfied before triggering.

>

param float trigger_delay:

Trigger delay (0s - 17.1799s)

 force_trigger()

Forces a software-timed trigger after pretrigger time has elapsed.

 query_acquisition_status()

Reports the state of an acquisition, whether completed or still running.

 query_analog_channel(*channel*)

Reports vertical configuration for the specified channel.

Returns:

Channel enabled, vertical range, vertical offset, probe attenuation, vertical coupling

Return type:

(bool, float, float, enum, enum)

 query_analog_channel_characteristics(*channel*)

Reports the properties governing electrical characteristics for the specified channel. An error is returned when excessive power is applied to the channel.

>

return:

Input impedance, bandwidth limit

rtype:

(enum, float)

 query_analog_edge_trigger(*trigger_instance*)

Reports analog edge trigger configuration for the specified instance.

Returns:

Trigger source, trigger slope, trigger level, trigger hysteresis

Return type:

(str, enum, float, float)

 query_analog_pulse_width_trigger(*trigger_instance*)

Reports analog pulse width trigger configuration for the specified instance.

Returns:

Trigger source, trigger polarity, trigger level, comparison mode, lower limit, upper limit

Return type:

(str, enum, float, enum, float, float)

 query_enabled_analog_channels()

Returns a String listing enabled analog channels.

Returns:

Enabled analog channels

Return type:

str

 query_timing()

Reports the MSO timing configuration. Call it right before measurement to capture the actual timing configuration and store it in the matching class variables; this is needed to interpret measurement data because no time information is included.

Returns:

Sample rate, acquisition time, pretrigger time, sampling mode

Return type:

(float, float, float, enum)

 query_trigger_delay()

Reports the MSO trigger delay setting.

Returns:

Trigger delay

Return type:

float

 query_trigger_type(*trigger_instance*)

Reports trigger type for the specified instance.

Parameters:

**trigger_instance** ? Trigger instance selection (`'A'` or `'B'`)

Returns:

Trigger type

Return type:

str

 read_analog_digital_dataframe()

Transfers data from the instrument and returns a pandas dataframe containing analog measurement data with time coordinates

Returns:

Dataframe containing time values and measurement data

Return type:

pd.DataFrame

 read_analog_digital_u64()

Transfers data from the instrument when acquisition state is Acquisition Complete. If the state is Running or Triggered, the method waits until Acquisition Complete; if the state is Stopped, it returns an error.

Returns:

Analog data out, analog data stride, analog t0, digital data out, digital timestamps out, digital t0, trigger timestamp, trigger reason

Return type:

(list, int, pyvb.Timestamp, list, list, pyvb.Timestamp, pyvb.Timestamp, enum)

 reset_instrument()

Restores default session configuration and returns the device plus driver software to a known state.

 run(*autoTrigger=True*)

Moves acquisition from Stopped state to Running state. If it is currently Triggered, acquisition first moves to Stopped state, then to Running state. The method returns an error when excessive power is present on any enabled channel.

Parameters:

**autoTrigger** (*bool*) – Enable/Disable auto triggering

 shutdown()

Closes the session and releases resources allocated during it. Enabled channel outputs stay at their existing levels.

 stop()

Moves acquisition from Triggered or Running state into Stopped state.

 validate_channel(*channel*)

Validate that `channel` is specified correctly

Parameters:

**channel** (*str*) – Channel string

Returns:

Channel string

Return type:

str

 *static *validate_trigger_instance(*trigger_instance*)

Validate that `trigger_instance` is an allowed choice

Parameters:

**trigger_instance** (*int** or **str*) ? Trigger instance selection (`'A'` or `'B'`)

Returns:

Trigger instance

Return type:

int

 *class *PowerSupply(*virtualbench*, *reset*, *vb_name=''*)

Bases: `VirtualBenchInstrument`

Models the Virtual Bench device Power Supply (PS) Module

 configure_current_output(*channel*, *current_level*, *voltage_limit*)

Sets current output for a specified channel. Call this once for each channel that should output current.

 configure_voltage_output(*channel*, *voltage_level*, *current_limit*)

Sets voltage output for a specified channel. Call this once for each channel that should output voltage.

 *property *outputs_enabled

Turns every output on every instrument channel on or off.

Parameters:

**enable_outputs** (*bool*) – Enable/Disable outputs

 query_current_output(*channel*)

Reports current output settings for the specified channel.

 query_voltage_output(*channel*)

Reports voltage output settings for the specified channel.

 read_output(*channel*)

Reads voltage level, current level, and output mode for the specified channel.

 reset_instrument()

Restores default session configuration and returns the device plus driver software to a known state.

 shutdown()

Closes the session and releases resources allocated during it. Enabled channel outputs stay at their existing levels.

 *property *tracking

Turns tracking between the positive and negative 25V channels on or off. When tracking is enabled, configuration changes on the positive 25V channel are mirrored to the negative 25V channel, while writes to the negative 25V channel are ignored.

Parameters:

**enable_tracking** (*bool*) – Enable/Disable tracking

 validate_channel(*channel*, *current=False*, *voltage=False*)

Validate the channel string and confirm the requested output current/voltage values are inside that channel's output ranges

Parameters:

-

**channel** (*str*) – Channel string (`"ps/+6V","ps/+25V","ps/-25V"`)

-

**current** (*bool**, **optional*) ? Current output flag, defaults to False (default: `False`)

-

**voltage** (*bool**, **optional*) ? Voltage output flag, defaults to False (default: `False`)

Returns:

channel or channel, current & voltage

Return type:

str or (str, float, float)

 acquire_digital_input_output(*lines*, *reset=False*)

Opens communication with the DIO module. Call this once per session.

Parameters:

-

**lines** (*str*) ? Lines to acquire; all lines can be read

-

**reset** (*bool**, **optional*) ? Whether to reset DIO module, defaults to False (default: `False`)

 acquire_digital_multimeter(*reset=False*)

Opens communication with the DMM module. Call this once per session.

Parameters:

**reset** (*bool**, **optional*) ? Whether to reset the DMM module, defaults to False (default: `False`)

 acquire_function_generator(*reset=False*)

Opens communication with the FGEN module. Call this once per session.

Parameters:

**reset** (*bool**, **optional*) ? Whether to reset the FGEN module, defaults to False (default: `False`)

 acquire_mixed_signal_oscilloscope(*reset=False*)

Opens communication with the MSO module. Call this once per session.

Parameters:

**reset** (*bool**, **optional*) ? Whether to reset the MSO module, defaults to False (default: `False`)

 acquire_power_supply(*reset=False*)

Opens communication with the PS module. Call this once per session.

Parameters:

**reset** (*bool**, **optional*) ? Whether to reset the PS module, defaults to False (default: `False`)

 collapse_channel_string(*names_in*)

Compacts a channel string into an equivalent comma- and colon-delimited form. The final element gives the channel count.

Parameters:

**names_in** (*str*) – Channel string

Returns:

Channel string using colon notation where available, plus number of channels

Return type:

(str, int)

 convert_timestamp_to_values(*timestamp*)

Transforms a timestamp into seconds and fractional seconds

Parameters:

**timestamp** (*pyvb.Timestamp*) – VirtualBench timestamp

Returns:

(seconds_since_1970, fractional seconds)

Return type:

(int, float)

 convert_values_to_datetime(*timestamp*)

Converts timestamp to datetime object

Parameters:

**timestamp** (*pyvb.Timestamp*) – VirtualBench timestamp

Returns:

Timestamp as DateTime object

Return type:

DateTime

 convert_values_to_timestamp(*seconds_since_1970*, *fractional_seconds*)

Builds a timestamp from seconds and fractional seconds

Parameters:

-

**seconds_since_1970** (*int*) ? Date/Time expressed as seconds since 1970

-

**fractional_seconds** (*float*) – Fractional seconds

Returns:

VirtualBench timestamp

Return type:

pyvb.Timestamp

 expand_channel_string(*names_in*)

Expands a channel string to a comma-delimited equivalent without colon notation. The final element gives the channel count. `'dig/0:2'` -> `('dig/0, dig/1, dig/2',3)`

Parameters:

**names_in** (*str*) – Channel string

Returns:

Channel string with every channel comma-separated, plus number of channels

Return type:

(str, int)

 get_calibration_information()

Retrieves calibration details for the specified device, including last calibration date and calibration interval.

Returns:

Calibration date, recommended calibration interval in months, and calibration interval in months

Return type:

(pyvb.Timestamp, int, int)

 get_library_version()

Returns the VirtualBench runtime library version

 shutdown()

Finalize the VirtualBench library.

 *class *pymeasure.instruments.ni.virtualbench.VirtualBench_Direct(**args: Any*, ***kwargs: Any*)

Bases: `PyVirtualBench`

Models the National Instruments Virtual Bench main frame. This class exposes direct access to the armstrap/pyvirtualbench Python wrapper.
