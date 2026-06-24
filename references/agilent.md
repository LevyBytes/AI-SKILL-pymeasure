# Agilent33521A, Agilent8257D, Agilent4156

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Scope includes Agilent 33521A Function/Arbitrary Waveform Generator; also Agilent 8257D Signal Generator; and Agilent 4155/4156 Semiconductor Parameter Analyzer.

## Agilent 33521A Function/Arbitrary Waveform Generator

### Agilent 33521A Function/Arbitrary Waveform Generator

 *class *pymeasure.instruments.agilent.Agilent33521A(*adapter*, ***kwargs*)

Bases: [`Agilent33500`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33500.html#pymeasure.instruments.agilent.Agilent33500)

Describes the Agilent 33521A Function/Arbitrary Waveform Generator.

Only methods that differ from the parent class [Agilent33500](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33500.html) are listed on this documentation page.

 ch_1

Channel:

`Agilent33500Channel`

 ch_2

Channel:

`Agilent33500Channel`

 *property *arb_srate*: Any*

Floating point setting for the sample rate of the currently selected arbitrary signal. Valid limits are 1 ?Sa/s to 250 MSa/s, and the value is writable.

 *property *frequency*: Any*

Floating point setting for output waveform frequency in Hz. The allowed span, from 1 uHz to 30 MHz, depends on the specified function; the value is writable.

 *class *pymeasure.instruments.agilent.agilent33500.Agilent33500Channel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Base-channel implementation for Agilent 33500.

 *property *amplitude*: Any*

Set or read voltage amplitude in Volts (float).(dynamic)

 *property *amplitude_unit*: Any*

Set or read amplitude units (string, strictly ?VPP?, ?VRMS?, or ?DBM?).(dynamic)

 *property *arb_advance*: Any*

Select how the device steps from one data point to the next (str). Accepted values are ?TRIG<GER>? or ?SRAT<E>? (default).

 *property *arb_file*: Any*

Select the arbitrary signal stored in device volatile memory.(dynamic)

 *property *arb_filter*: Any*

Set the arbitrary-signal filter mode (str). Accepted values are ?NORM<AL>?, ?STEP? and ?OFF?.

 *property *arb_srate*: Any*

Set or read the sample rate for the currently selected arbitrary signal in Sa/s (float). The valid span is 1 ?Sa/s to 250 MSa/s (maximum range, device-dependent).

 *property *burst_mode*: Any*

Set or read burst mode type (str, strictly ?TRIG<GERED>? or ?GAT<ED>?).(dynamic)

 *property *burst_ncycles*: Any*

Set or read the cycle count emitted after a burst trigger (int).(dynamic)

 *property *burst_period*: Any*

Set or read the interval between later bursts in seconds (float).(dynamic)

 *property *burst_state*: Any*

Set or read whether burst mode is enabled (bool).(dynamic)

 data_arb(*arb_name*, *data_points*, *data_format='DAC'*)

Send an arbitrary trace to a channel's volatile device memory.

data_points accepts one of three encodings: comma separated 16 bit DAC values (from -32767 to +32767), comma separated floating point values (from -1.0 to +1.0), or a binary data stream. For details, consult the manual. Capacity is device-specific and spans 8 Sa to 16 MSa (maximum).

Parameters:

-

**arb_name** ? Trace name used inside volatile memory; later calls use this name to select that trace.

-

**data_points** –

Trace samples supplied individually. Their required representation follows the format parameter.

format = ?DAC? (default): Takes a list of integer values from -32767 to +32767. Requires at least 8 and at most 65536 points.

format = ?float?: Takes a list of floating point values from -1.0 to +1.0. Requires at least 8 and at most 65536 points.

format = ?binary?: Takes an 8 bit binary stream.

-

**data_format** ? Specifies the representation used for data_points: ?DAC? (default), ?float?, or ?binary?. See the data_points parameter notes above. (default: `'DAC'`)

 data_volatile_clear()

Remove all arbitrary signals from a channel's volatile memory.

Use this before repeatedly writing different arbitrary signals under the same name; loading a trace that is already present in memory raises an error.

 *property *frequency*: Any*

Set or read waveform frequency in Hz (float), with limits determined by the specified shape.(dynamic)

 *property *offset*: Any*

Set or read voltage offset in Volts (float).(dynamic)

 *property *output*: Any*

Set or read output enable state (bool).(dynamic)

 *property *output_load*: Any*

Set or read expected load resistance in Ohms (str or float). Output impedance stays at 50 Ohm; this setting adjusts the displayed voltage for loads that are not matched to 50 Ohm.(dynamic)

 *property *phase*: Any*

Set or read waveform phase in degrees (float, from -360 to 360).

 *property *pulse_dutycycle*: Any*

Set or read pulse duty cycle in percent (float, from 0 to 100).(dynamic)

 *property *pulse_hold*: Any*

Set whether pulse width or duty cycle is preserved when waveform period or frequency changes (str).(dynamic)

 *property *pulse_period*: Any*

Set or read pulse period in seconds (float), overriding frequency. When the period is less than pulse width + the edge time, both edge time and pulse width are adjusted.(dynamic)

 *property *pulse_transition*: Any*

Set or read pulse edge time in seconds for both rising and falling edges (float).(dynamic)

 *property *pulse_width*: Any*

Set or read pulse width in seconds (float).(dynamic)

 *property *ramp_symmetry*: Any*

Set or read ramp waveform symmetry in percent (float, from 0 to 100).(dynamic)

 *property *shape*: Any*

Set or read output waveform shape (str).(dynamic)

 *property *square_dutycycle*: Any*

Set or read square wave duty cycle in percent (float).(dynamic)

 *property *voltage_high*: Any*

Set or read upper voltage level in Volts (float).(dynamic)

 *property *voltage_low*: Any*

Set or read lower voltage level in Volts (float).(dynamic)

## Agilent 8257D Signal Generator

### Agilent 8257D Signal Generator

 *class *pymeasure.instruments.agilent.Agilent8257D(*adapter*, *name='Agilent 8257D RF Signal Generator'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Describes the Agilent 8257D Signal Generator and exposes a higher-level interface for working with the instrument.

```python
generator = Agilent8257D("GPIB::1")

generator.power = 0                     # Sets the output power to 0 dBm
generator.frequency = 5                 # Sets the output frequency to 5 GHz
generator.enable()                      # Enables the output

```

 *property *amplitude_depth*: Any*

Floating point setting for amplitude modulation depth in percent, accepting 0 to 100 %.

 *property *amplitude_source*: Any*

String setting for amplitude modulation signal source. Valid choices are ?internal?, ?internal 2?, ?external?, and ?external 2?.

 *property *center_frequency*: Any*

Floating point setting for center frequency in Hz; writable.

 config_amplitude_modulation(*frequency=1000.0*, *depth=100.0*, *shape='sine'*)

Sets up amplitude modulation for the output signal.

Parameters:

-

**frequency** ? Internal oscillator modulation frequency (default: `1000.0`)

-

**depth** ? Linear modulation depth percentage (default: `100.0`)

-

**shape** ? Shape string for the internal oscillator (default: `'sine'`)

 config_low_freq_out(*source='internal'*, *amplitude=3*)

Sets up the low-frequency output signal.

Parameters:

-

**source** ? Low-frequency output signal source. (default: `'internal'`)

-

**amplitude** ? Low-frequency output amplitude (default: `3`)

 config_pulse_modulation(*frequency=1000.0*, *input='square'*)

Sets up pulse modulation for the output signal.

Parameters:

-

**frequency** ? Pulse rate frequency in Hertz (default: `1000.0`)

-

**input** ? String describing the internal pulse input (default: `'square'`)

 config_step_sweep()

Sets up a frequency step sweep.

 disable()

Turns off signal output.

 disable_amplitude_modulation()

Turns off amplitude modulation for the output signal.

 disable_low_freq_out()

Disables low frequency output

 disable_modulation()

Disables the signal modulation.

 disable_pulse_modulation()

Turns off pulse modulation for the output signal.

 *property *dwell_time*: Any*

Floating point setting for settling time in seconds at the active frequency or power setting; writable.

 enable()

Turns on signal output.

 enable_amplitude_modulation()

Turns on amplitude modulation for the output signal.

 enable_low_freq_out()

Enables low frequency output

 enable_pulse_modulation()

Turns on pulse modulation for the output signal.

 *property *frequency*: Any*

Floating point setting for output frequency in Hz; writable.

 *property *has_amplitude_modulation*: Any*

Returns True when amplitude modulation is enabled.

 *property *has_modulation*: Any*

Returns True when modulation is enabled.

 *property *has_pulse_modulation*: Any*

Returns True when pulse modulation is enabled.

 *property *internal_frequency*: Any*

Floating point setting for the internal oscillator frequency in Hertz, with valid values from 0.5 Hz to 1 MHz.

 *property *internal_shape*: Any*

String setting for the internal oscillation shape. Valid choices are ?sine?, ?triangle?, ?square?, ?ramp?, ?noise?, ?dual-sine?, and ?swept-sine?.

 *property *is_enabled*: Any*

Returns True when output is on.

 *property *low_freq_out_amplitude*: Any*

Floating point setting for low frequency output peak voltage (amplitude) in volts, accepting 0-3.5V.

 *property *low_freq_out_source*: Any*

String setting for low frequency output source. Use ?internal [2]? for the internal source, or ?function [2]? for a configurable internal function generator.

 *property *power*: Any*

Floating point setting for output power in dBm; writable.

 *property *pulse_frequency*: Any*

Floating point setting for pulse rate frequency in Hertz, accepting 0.1 Hz to 10 MHz.

 *property *pulse_input*: Any*

String setting for the internally generated pulse modulation input. Valid choices are ?square?, ?free-run?, ?triggered?, ?doublet?, and ?gated?.

 *property *pulse_source*: Any*

String setting for pulse modulation signal source. Valid choices are ?internal?, ?external?, and ?scalar?.

 shutdown()

Closes down the instrument by turning off any modulation and the output signal.

 *property *start_frequency*: Any*

Floating point setting for start frequency in Hz; writable.

 *property *start_power*: Any*

Floating point setting for start power in dBm; writable.

 start_step_sweep()

Starts a step sweep.

 *property *step_points*: Any*

Integer point count for a step sweep; writable.

 *property *stop_frequency*: Any*

Floating point setting for stop frequency in Hz; writable.

 *property *stop_power*: Any*

Floating point setting for stop power in dBm; writable.

 stop_step_sweep()

Stops a step sweep.

## Agilent 4155/4156 Semiconductor Parameter Analyzer

### Agilent 4155/4156 Semiconductor Parameter Analyzer

 *class *pymeasure.instruments.agilent.agilent4156.Agilent4156(*adapter*, *name='Agilent 4155/4156 Semiconductor Parameter Analyzer'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Describes the Agilent 4155/4156 Semiconductor Parameter Analyzer and offers a high-level interface for current-voltage (I-V) measurements.

```python
from pymeasure.instruments.agilent import Agilent4156

# explicitly define r/w terminations; set sufficiently large timeout or None.
smu = Agilent4156("GPIB0::25", read_termination = '\n', write_termination = '\n',
                  timeout=None)

# reset the instrument
smu.reset()

# define configuration file for instrument and load config
smu.configure("configuration_file.json")

# save data variables, some or all of which are defined in the json config file.
smu.save(['VC', 'IC', 'VB', 'IB'])

# take measurements
status = smu.measure()

# measured data is a pandas dataframe and can be exported to csv.
data = smu.get_data(path='./t1.csv')

```

The JSON file is an ascii text configuration file defining each instrument channel's settings. The convenience function `configure()` uses that JSON file to configure the instrument, as illustrated above. A bipolar transistor measurement setup is provided below as an example.

```json
{
       "SMU1": {
           "voltage_name" : "VC",
           "current_name" : "IC",
           "channel_function" : "VAR1",
           "channel_mode" : "V",
           "series_resistance" : "0OHM"
       },

       "SMU2": {
           "voltage_name" : "VB",
           "current_name" : "IB",
           "channel_function" : "VAR2",
           "channel_mode" : "I",
           "series_resistance" : "0OHM"
       },

       "SMU3": {
           "voltage_name" : "VE",
           "current_name" : "IE",
           "channel_function" : "CONS",
           "channel_mode" : "V",
           "constant_value" : 0,
           "compliance" : 0.1
       },

        "SMU4": {
           "voltage_name" : "VS",
           "current_name" : "IS",
           "channel_function" : "CONS",
           "channel_mode" : "V",
           "constant_value" : 0,
           "compliance" : 0.1
       },

       "VAR1": {
           "start" : 1,
           "stop" : 2,
           "step" : 0.1,
           "spacing" : "LINEAR",
           "compliance" : 0.1
       },

       "VAR2": {
           "start" : 0,
           "step" : 10e-6,
           "points" : 3,
           "compliance" : 2

       }
   }

```

 *property *analyzer_mode*: Any*

Control the instrument operating mode.

-

Values: `SWEEP`, `SAMPLING`

```python
smu.analyzer_mode = "SWEEP"

```

 configure(*config_file*)

Configure instrument channel setup and sweep behavior from a JSON configuration file.

(JSON means [JavaScript Object Notation](https://www.json.org/))

Parameters:

**config_file** ? JSON file used to configure instrument channels.

```python
instr.configure('config.json')

```

 *property *data_variables

Return a string list containing data variables with available measured data.

Searches for variables stored by `save()` and `save_var()` and returns them. Useful when building dataframe headers.

Returns:

List

```python
header = instr.data_variables

```

 *property *delay_time*: Any*

Set or read measurement delay time in seconds; valid values run from 0 to 65s in 0.1s steps.

```python
instr.delay_time = 1 # delay time of 1-sec

```

 disable_all()

Turn off every channel in the instrument.

```python
instr.disable_all()

```

 get_data(*path=None*)

Retrieve measurement data from the instrument once the run is complete.

When `measure()` uses measurement period `INF`, call `stop()` before retrieving data; otherwise valid data is not available.

Parameters:

**path** ? Optional CSV export path. (default: `None`)

Returns:

Pandas Dataframe

```python
df = instr.get_data(path='./datafolder/data1.csv')

```

 *property *hold_time*: Any*

Set or read measurement hold time in seconds; accepted values are 0 to 655s in 1s steps.

```python
instr.hold_time = 2 # hold time of 2-secs.

```

 *property *integration_time*: Any*

Control the integration time.

-

Values: `SHORT`, `MEDIUM`, `LONG`

```python
instr.integration_time = "MEDIUM"

```

 measure(*period='INF'*, *points=100*)

Run one sweep-mode measurement and wait until it finishes.

For sampling mode, both measurement period and number of points may be provided.

Parameters:

-

**period** ? Sampling measurement period, from 6E-6 to 1E11 seconds. Default setting is `INF`. (default: `'INF'`)

-

**points** ? Sample count to measure, from 1 to 10001. Default setting is `100`. (default: `100`)

 save(*trace_list*)

Store voltage or current in the instrument display list.

Parameters:

**trace_list** ? Channel-variable list whose measured data should be saved. Up to 8 variables are allowed. When saving a single variable, a string may be used.

```python
instr.save(['IC', 'IB', 'VC', 'VB']) #for list of variables
instr.save('IC')    #for single variable

```

 save_var(*trace_list*)

Store voltage or current in the instrument variable list.

Use this when saving one or two additional variables beyond the 8 variables permitted by `save()`.

Parameters:

**trace_list** ? Channel-variable list whose measured data should be saved. Up to 2 variables are allowed. When saving a single variable, a string may be used.

```python
instr.save_var(['VA', 'VB'])

```

 stop()

Stop the ongoing measurement.

```python
instr.stop()

```

 *class *pymeasure.instruments.agilent.agilent4156.AgilentMeasurementChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Offers some common properties.

 *property *channel_function*: Any*

Control the channel function.

-

Allowed values: `VAR1`, `VAR2`, `VARD` or `CONS`.

 *property *channel_mode*: Any*

Control the channel mode.(dynamic)

 *property *disable

Apply default settings to this channel.

```python
instr.smu1.disable

```

 reset_settings()

Restore this channel's settings to default value.

```python
instr.smu1.reset_settings()

```

 *property *voltage_name*: Any*

Set or read the channel voltage name.

When input exceeds 6 characters or begins with a number, the name is corrected automatically by prefixing ?a?; the event is logged.

```python
instr.smu1.voltage_name = "Vbase"

```

 *class *pymeasure.instruments.agilent.agilent4156.SMU(*parent*, *id*, ***kwargs*)

Bases: `AgilentMeasurementChannel`

SMU for Agilent 4155/4156 Semiconductor Parameter Analyzer.

 *property *compliance

Set or read SMU<n> *constant* compliance value.

For an SMU channel configured as variable (VAR1, VAR2, VARD), the variable definition supplies compliance limits.

-

Value: Voltage in (-200V, 200V) and current in (-1A, 1A), selected according to `channel_mode()`.

```python
instr.smu1.compliance = 0.1

```

 *property *constant_value

Set or read SMU<n> constant source value.

Use this command only when `channel_function()` is `CONS` and `channel_mode()` is not `COMM`.

Parameters:

**const_value** ? Voltage in (-200V, 200V) and current in (-1A, 1A). Whether voltage or current applies depends on `channel_mode()` being `V` or `I`.

```python
instr.smu1.constant_value = 1

```

 *property *current_name*: Any*

Set or read the channel current name.

When input exceeds 6 characters or begins with a number, the name is corrected automatically by prefixing ?a?; the event is logged.

```python
instr.smu1.voltage_name = "Vbase"

```

 *property *series_resistance*: Any*

Set or read SMU<n> series resistance.

-

Allowed values: `0OHM`, `10KOHM`, `100KOHM`, or `1MOHM`

```python
instr.smu1.series_resistance = "10KOHM"

```

 *class *pymeasure.instruments.agilent.agilent4156.VAR1(*parent*, ***kwargs*)

Bases: `VARX`

Class containing VAR1-specific definitions; the most common methods come from the base class.

 *property *spacing*: Any*

Set or read VAR1 sweep type.

-

Values: `LINEAR`, `LOG10`, `LOG25`, `LOG50`.

 *class *pymeasure.instruments.agilent.agilent4156.VAR2(*adapter*, ***kwargs*)

Bases: `VARX`

Class containing VAR2-specific definitions; common methods are brought in from the base class.

 *property *points*: Any*

Set or read the number of VAR2 sweep steps. Use this command only when an SMU or VSU has function (FCTN) set to VAR2.

```python
instr.var2.points = 10

```

 *class *pymeasure.instruments.agilent.agilent4156.VARD(*parent*, *id='VARD'*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class containing the definitions for VARD, which is always specified relative to VAR1.

 *property *channel_mode

Control the channel mode.

 *property *compliance

Set or read VARD sweep COMPLIANCE value.

```python
instr.vard.compliance = 0.1

```

 *property *offset

Set or read VARD OFFSET value. At each sweep step, VAR1? output values follow this equation: VARD = VAR1 X RATio + OFFSet. Use this command only when an SMU or VSU function is VARD.

```python
instr.vard.offset = 1

```

 *property *ratio*: Any*

Set or read RATIO of VAR1?. At each sweep step, VAR1? output values follow this equation: VAR1? = VAR1 * RATio + OFFSet. Use this command only when an SMU or VSU function (FCTN) is VAR1?.

```python
instr.vard.ratio = 1

```

 *class *pymeasure.instruments.agilent.agilent4156.VARX(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Base class for sweep variable setting definitions.

 *property *channel_mode

Control the channel mode.

 *property *compliance

Control the sweep COMPLIANCE value.

```python
instr.var1.compliance = 0.1

```

 *property *start

Control the sweep START value.

```python
instr.var1.start = 0

```

 *property *step

Control the sweep STEP value.

```python
instr.var1.step = 0.1

```

 *property *stop

Control the sweep STOP value.

```python
instr.var1.stop = 3

```

 *class *pymeasure.instruments.agilent.agilent4156.VMU(*parent*, *id*, ***kwargs*)

Bases: `AgilentMeasurementChannel`

VMU for Agilent 4155/4156 Semiconductor Parameter Analyzer.

 *class *pymeasure.instruments.agilent.agilent4156.VSU(*parent*, *id*, ***kwargs*)

Bases: `AgilentMeasurementChannel`

VSU for Agilent 4155/4156 Semiconductor Parameter Analyzer.

 *property *constant_value

Set or read VSU<n> constant source value.

```python
instr.vsu1.constant_value = 0

```
