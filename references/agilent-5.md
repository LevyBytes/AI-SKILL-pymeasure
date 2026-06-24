# Agilent33500, Agilente5270B, Agilente5062A

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Coverage spans the Agilent 33500 Function/Arbitrary Waveform Generator Family, the Agilent E5270B SMU mainframe, and the Agilent E5062A Vector Network Analyzer.

## Agilent 33500 Function/Arbitrary Waveform Generator Family

### Agilent 33500 Function/Arbitrary Waveform Generator Family

 *class *pymeasure.instruments.agilent.Agilent33500(*adapter*, *name='Agilent 33500 Function/Arbitrary Waveform generator family'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent 33500 Function/Arbitrary Waveform Generator family.

Subclasses model the individual instruments. A channel may be supplied for control; when it is omitted, the driver chooses a device-specific default. For example, Agilent33500B uses channel 1. Consult the reference manual for your device.

```python
generator = Agilent33500("GPIB::1")

generator.shape = 'SIN'                 # Sets default channel output signal shape to sine
generator.channels[1].shape = 'SIN'           # Sets channel 1 output signal shape to sine
generator.frequency = 1e3               # Sets default channel output frequency to 1 kHz
generator.channels[1].frequency = 1e3         # Sets channel 1 output frequency to 1 kHz
generator.channels[2].amplitude = 5           # Sets channel 2 output amplitude to 5 Vpp
generator.channels[2].output = 'on'           # Enables channel 2 output

generator.channels[1].shape = 'ARB'           # Set channel 1 shape to arbitrary
generator.channels[1].arb_srate = 1e6         # Set channel 1 sample rate to 1MSa/s

generator.channels[1].data_volatile_clear()   # Clear channel 1 volatile internal memory
generator.channels[1].data_arb(               # Send data of arbitrary waveform to channel 1
    'test',
    range(-10000, 10000, +20),          # In this case a simple ramp
    data_format='DAC'                   # Data format is set to 'DAC'
 )
generator.channels[1].arb_file = 'test'       # Select the transmitted waveform 'test'

```

 ch_1

Channel:

[`Agilent33500Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33521A.html#pymeasure.instruments.agilent.agilent33500.Agilent33500Channel)

 ch_2

Channel:

[`Agilent33500Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33521A.html#pymeasure.instruments.agilent.agilent33500.Agilent33500Channel)

 *property *amplitude*: Any*

Set or read voltage amplitude in Volts (float).(dynamic)

 *property *amplitude_unit*: Any*

Set or read amplitude unit selection (string, strictly ‘VPP’, ‘VRMS’, or ‘DBM’).(dynamic)

 *property *arb_advance*: Any*

Set or read the arbitrary data advance mode (str). Accepts ‘TRIG<GER>’ or the default ‘SRAT<E>’.

 *property *arb_file*: Any*

Select the arbitrary signal stored in the device volatile memory.(dynamic)

 *property *arb_filter*: Any*

Set or read the arbitrary-signal filter mode (str). Allowed values are ‘NORM<AL>’, ‘STEP’ and ‘OFF’.

 *property *arb_srate*: Any*

Set or read sample rate for the selected arbitrary signal in Sa/s (float). Allowed values span 1 µSa/s to 250 MSa/s in the maximum range, with device-specific limits.

 beep()

Causes a system beep.

 *property *burst_mode*: Any*

Set or read burst mode type (str, strictly ‘TRIG<GERED>’ or ‘GAT<ED>’).(dynamic)

 *property *burst_ncycles*: Any*

Set or read how many cycles are emitted for each triggered burst (int).(dynamic)

 *property *burst_period*: Any*

Set or read time between successive bursts in seconds (float).(dynamic)

 *property *burst_state*: Any*

Enable or disable burst mode (bool).(dynamic)

 clear_display()

Clears the display text message.

 data_arb(*arb_name*, *data_points*, *data_format='DAC'*)

Loads an arbitrary trace into device volatile memory.

data_points accepts three encodings: 16 bit DAC entries separated by commas (ranging from -32767 to +32767), floating point entries separated by commas (ranging from -1.0 to +1.0), or a binary data stream. Consult the manual for fuller details. Storage is model-dependent and spans 8 Sa to 16 MSa (maximum).

Parameters:

-

**arb_name** – Name assigned to the trace in volatile memory; use it later to select that trace.

-

**data_points** – Trace sample values. Interpretation is selected by the format parameter. format = ‘DAC’ (default): accepts integer lists from -32767 to +32767. Requires at least 8 and at most 65536 points. format = ‘float’: accepts floating point lists from -1.0 to +1.0. Requires at least 8 and at most 65536 points. format = ‘binary’: accepts an 8 bit binary stream.

-

**data_format** – Chooses how data_points is interpreted. Valid values are ‘DAC’ (default), ‘float’ or ‘binary’. See the data_points parameter description above. (default: `'DAC'`)

 data_volatile_clear()

Erase all arbitrary signals held in volatile memory.

Use this when repeatedly reusing one name for different arbitrary signals; loading a trace whose name already exists in memory causes an error.

 *property *display*: Any*

Write front-panel display text for the device (string).

 *property *ext_trig_out*: Any*

Set or read whether trigger out signal is enabled (bool).

 *property *frequency*: Any*

Set or read waveform frequency in Hz (float); valid limits depend on the selected shape.(dynamic)

 *property *offset*: Any*

Set or read voltage offset in Volts (float).(dynamic)

 *property *output*: Any*

Enable or disable output state (bool).(dynamic)

 *property *output_load*: Any*

Set or read expected load resistance in Ohms (str or float). Physical output impedance remains 50 Ohm; this setting adjusts displayed voltage for loads that are not matched to 50 Ohm.(dynamic)

 *property *phase*: Any*

Set or read waveform phase in degrees (float, from -360 to 360).

 phase_sync()

Align the phase across all channels.

 *property *pulse_dutycycle*: Any*

Set or read pulse duty cycle in percent (float, from 0 to 100).(dynamic)

 *property *pulse_hold*: Any*

Set or read whether pulse width or duty cycle is held constant when waveform period or frequency changes (str).(dynamic)

 *property *pulse_period*: Any*

Set or read pulse period in seconds (float). This overwrites frequency. When the period is less than pulse width + edge time, the instrument adjusts edge time and pulse width.(dynamic)

 *property *pulse_transition*: Any*

Set or read pulse edge time, applying to both rising and falling edges, in seconds (float).(dynamic)

 *property *pulse_width*: Any*

Set or read pulse width in seconds (float).(dynamic)

 *property *ramp_symmetry*: Any*

Set or read ramp waveform symmetry in percent (float, from 0 to 100).(dynamic)

 *property *shape*: Any*

Set or read output waveform shape (str).(dynamic)

 *property *square_dutycycle*: Any*

Set or read square wave duty cycle in percent (float).(dynamic)

 trigger()

Issue a trigger signal to the function generator.

 *property *trigger_source*: Any*

Control the trigger source (str).

 *property *voltage_high*: Any*

Set or read upper voltage level in Volts (float).(dynamic)

 *property *voltage_low*: Any*

Set or read lower voltage level in Volts (float).(dynamic)

 wait_for_trigger(*timeout=3600*, *should_stop=<function Agilent33500.<lambda>>*)

Block until triggering completes or until timeout is reached.

Parameters:

-

**timeout** – Maximum duration allowed for the wait. A TimeoutError is raised if timeout is exceeded. When timeout is zero, waiting has no timeout. (default: `3600`)

-

**should_stop** – Optional callable returning a bool that can end the wait early. (default: `<function Agilent33500.<lambda> at 0x7aa592a19010>`)

## Agilent E5270B SMU mainframe

### Agilent E5270B SMU mainframe

 *class *pymeasure.instruments.agilent.AgilentE5270B(*adapter*, *name='Agilent E5270B'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent E5270B 8 slot SMU mainframe.

Supported plug-in modules are:

| Name | Type | Slots | Range | Resolution |
| --- | --- | --- | --- | --- |
| E5280B | HPSMU | 2 | ±200 V, ±1 A | 2 µV, 10 fA |
| E5281B | MPSMU | 1 | ±100 V, ±100 mA | 0.5 µV, 10 fA |
| E5287A | HRSMU | 1 | ±100 V, ±100 mA | 0.5 µV, 1 fA |
| E5288A | ASU | — | ±100 V, ±100 mA | 0.5 µV, 0.1 fA |

 display

Channel:

`Display`

 check_errors()

Retrieve every instrument error.

Returns:

List of error entries.

 get_error_message(*error_code*)

Return the error message for the specified error code (str).

 *property *options*: Any*

Return installed SMUs (list of str).

Every list item gives module name and revision, e.g. `E5281B,0`; an empty slot reports `0,0`

 *class *pymeasure.instruments.agilent.agilentE5270B.Display(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Models the Agilent E5270B display.

 *property *enabled*: Any*

Enable or disable the display while operating remotely (bool).

 *property *engineering_format_enabled*: Any*

Select engineering data format versus scientific data format (bool).

Example:

-

`True` (engineering): +123.456mA

-

`False` (scientific): +1.234E-1A

Note

Calling [`reset()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.reset) changes the data format to scientific.

 *property *measurement_parameter*: Any*

Choose the LCD parameter for the Measurement Data display area (str; allowed values are strictly `result`, `result_and_source`, `resistance` or `power`).

 *property *measurement_smu*: Any*

Choose the measurement SMU shown on the LCD (int, strictly from `1` to `8`).

 *property *source_parameter1*: Any*

Choose the Source Data display area value for line 1 (str; allowed choices are strictly in `set_point`, `compliance`, `voltage_range`, `current_range` or `error`).

 *property *source_parameter2*: Any*

Choose the Source Data display area value for line 2 (str; allowed choices are strictly in `set_point`, `compliance`, `voltage_range`, `current_range` or `error`).

 *property *source_smu*: Any*

Choose the source SMU whose data appears on the LCD. (int, strictly from `1` to `8`).

 *class *pymeasure.instruments.agilent.agilentE5270B.SMUChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Models an Agilent E5270B SMU channel.

 *property *current*: Any*

Measure current in Amps (float).

 *property *current_setpoint*: Any*

Configure range, output current, and voltage compliance (int, float, float).

```python
inst = AgilentE5270B("GPIB0::17::INSTR")
inst.smu1.current_setpoint = (0, 1.32e-3, 0.5)  # (range, value, compliance)
# Set SMU1 to output 1.32 mA in autorange with 0.5 V voltage compliance

```

Ranges:

-

`0`: Auto ranging

-

`8`: limited auto ranging at 1 pA for E5287A+E5288A

-

`9`: limited auto ranging at 10 pA for E5287A

-

`10`: limited auto ranging at 100 pA for E5287A

-

`11`: 1 nA limited auto ranging

-

`12`: 10 nA limited auto ranging

-

`13`: 100 nA limited auto ranging

-

`14`: 1 μA limited auto ranging

-

`15`: 10 μA limited auto ranging

-

`16`: 100 μA limited auto ranging

-

`17`: 1 mA limited auto ranging

-

`18`: 10 mA limited auto ranging

-

`19`: 100 mA limited auto ranging

-

`20`: limited auto ranging at 1 A for E5280B

 *property *enabled*: Any*

Enable or disable channel output state (bool).

 *property *voltage*: Any*

Measure voltage in Volts (float).

 *property *voltage_setpoint*: Any*

Configure range, output voltage, and current compliance (int, float, float)

```python
inst = AgilentE5270B("GPIB0::17::INSTR")
inst.smu1.voltage_setpoint = (12, 14.42, 0.05)  # (range, value, compliance)
# Set SMU1 to output 14.42 V in 20 V range with 50 mA current compliance

```

Ranges:

-

`0`: Auto ranging

-

`5`: limited auto ranging at 0.5 V for E5281B/E5287A

-

`50`: limited auto ranging at 5 V for E5281B/E5287A

-

`11` or `20`: 2 V limited auto ranging

-

`12` or `200`: 20 V limited auto ranging

-

`13` or `400`: 40 V limited auto ranging

-

`14` or `1000`: 100 V limited auto ranging

-

`15` or `2000`: limited auto ranging at 200 V for E5280B

## Agilent E5062A Vector Network Analyzer

### Agilent E5062A Vector Network Analyzer

Class constructor: pymeasure.instruments.agilent.AgilentE5062A(adapter, **kwargs).
Default name: 'Agilent E5062A Vector Network Analyzer'.

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent E5062A Vector Network Analyzer

This VNA provides 4 independent channels, and every channel owns its sweep. They are exposed through the `channels` dictionary. A channel may be enabled without being shown. Many operations tied to a trace, including data reads, are performed through the channel but apply only to the *active trace*.

A channel can show as many as 4 traces, set by `visible_traces`. Each channel also exposes `display_layout`, which determines trace arrangement within that channel. Trace objects live in the `traces` dictionary, for example `vna.channels[1].traces[1]`.

The VNA has several transfer formats, but this API works only with IEEE 64-bit floating point format. Initialization configures the VNA to use that format, and data transfer format is not exposed as a public property.

Only part of the full E5062A feature set is implemented here. Notable missing pieces include (TODO):

-

changing the display scale

-

markers

-

calibration

-

power sweeps

```python
# connect to the VNA and make a measurement consisting of 10 averages
vna = AgilentE5062A("TCPIP::192.168.2.233::INSTR")
ch = vna.channels[1]            # use channel 1
ch.visible_traces = 4            # use all 4 traces
for i, (tr, parameter) in enumerate(zip(
        ch.traces.values(),
        ['S11', 'S12', 'S21', 'S22'])):
    tr.parameter = parameter

ch.averages = 10                # use 10x averaging
ch.averaging_enabled = True     # turn averaging on
ch.trigger_continuous = False   # turn off continuous triggering
vna.trigger_source = 'BUS'      # require remote trigger
vna.abort()                     # stop the current sweep
ch.restart_averaging()          # clear current averaging
for _ in range(ch.averages):
    ch.trigger_initiate()       # arm channel 1 for single sweep
    vna.trigger_single()        # send a trigger
    vna.wait_for_complete()     # wait until the sweep is complete

# see `agilentE5062A.data` for an example of saving the measurement

```

 ch_1

Channel:

`VNAChannel`

 ch_2

Channel:

`VNAChannel`

 ch_3

Channel:

`VNAChannel`

 ch_4

Channel:

`VNAChannel`

 abort()

Stop the active sweep; this affects the trigger fsm, with details on page 80 of the programmer’s manual.

 *property *display_layout*: Any*

Set or read the display arrangement for windows (channels) (str). Valid options are listed below:

-

D1

-

D12

-

D1_2

-

D112

-

D1_1_2

-

D123

-

D1_2_3

-

D12_33

-

D11_23

-

D13_23

-

D12_13

-

D1234

-

D1_2_3_4

-

D12_34

Generally, a number means the corresponding channel is visible, while ‘_’ marks a vertical split. Repeating a number gives that channel a larger window than the others. See Figure 3-1 in the programmer’s manual for details.

This layout splits multiple *channels*, not traces. Basic S-param measurements usually use one channel with multiple *traces*. See e.g. `AgilentE5062A.channels[1].visible_traces`

 *property *output_enabled*: Any*

Set or read whether RF stimulus is enabled (bool). Measurements require stimulus to be on. Be aware that stimulus defaults to on, i.e. after reset().

 pop_err()

Remove and return one error from the error queue. The return value is a tuple with the code and error description. Error code 0 means success.

Clear the Error queue with the standard SCPI `agilentE5062A.clear()` method.

 trigger()

Generate a trigger no matter which trigger setting is selected, provided triggering has been initialized, i.e. the instrument is in trigger wait state.

 trigger_bus()

When trigger source is BUS and the VNA is waiting because triggering has been initialized, issue a trigger.

 trigger_single()

Similar to trigger(), except the complete SCPI property (synchronization bit) waits until the sweep completes; see agilentE5062A.wait_for_complete().

 *property *trigger_source*: Any*

Set or read trigger source (str). Documentation-defined values are:

-

INT: Selects internal triggering, which automatically produces continuous triggers (default).

-

EXT: Creates a trigger from an external trigger signal received through the Ext Trig connector or handler interface.

-

MAN: Creates a trigger when the front-panel [Trigger] - Trigger key operation is run.

-

BUS: Creates a trigger when `*TRG` is executed.

 wait_for_complete(*attempt=1*, *max_attempts=20*)

Wait, potentially for a long interval, for the synchronization bit. Use with agilentE5062A.trigger_single() when a single sweep must finish before continuing.

 *class *pymeasure.instruments.agilent.agilentE5062A.VNAChannel(**args*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Measurement channel for the E5061A/E5062A

 *property *IF_bandwidth*: Any*

Set or read IF bandwidth in Hz (int), with valid values from 10 Hz to 30 kHz. Default 30 kHz.

 activate()

Select the current channel. The channel must already be displayed through AgilentE5062A.display_layout before it can be activated.

 *property *attenuation

Set or read stimulus attenuation in dB (positive int), from 0 to 40 in increments of 10. Default is 0 dB. Allowed stimulus power occupies a 15 dB span: (`attenuation` - 5 dB, `attenuation` + 10 dB).

Requires the power range extension; without that extension installed, the command is ignored.

 *property *averages*: Any*

Set or read averaging count, from 1-999 (int). `averaging_enabled` must be true before averaging is used.

 *property *averaging_enabled*: Any*

Enable or disable averaging of measurement data (bool).

 *property *data

Read Formatted Data for the *active trace*.

A trace contains `scan_points` samples plotted either against frequency or in a Smith-chart-style arrangement. This property does not return frequency values. For rectangular plots, the query therefore returns just trace y-values. For smith- and polar- plots, it returns two values per data point.

Returns a tuple with primary and secondary data numpy arrays. For trace formats other than smith or polar, secondary data contains only zeros. To capture complex S-parameter data in one operation, use a Smith (Real/Imag) or Polar (Real/Imag) trace format, respectively SCOMplex or POLar.

The VNA can accept formatted data arrays, but this python API does not implement setting them.

Read frequency data from the `frequencies` property.

```python
# build an s-parameter matrix by measuring the trace data,
# where s_matrix[i] = [[S11, S12], [S21, S22]] @ freqs[i]
freqs = ch.frequencies
s_matrix = np.empty((freqs.size, 4), dtype=np.complex64)
for i, tr in enumerate(ch.traces.values()):
    tr.activate()
    ch.trace_format = 'POL'
    re, im = ch.data
    s_matrix[:, i] = re + 1j * im
s_matrix = s_matrix.reshape(-1, 2, 2)  # ready for use with e.g. skrf

```

 *property *display_layout*: Any*

Set or read trace graph layout within the channel (str). This does not change which traces are active. Valid options are:

-

D1

-

D12

-

D1_2

-

D112

-

D1_1_2

-

D123

-

D1_2_3

-

D12_33

-

D11_23

-

D13_23

-

D12_13

-

D1234

-

D1_2_3_4

-

D12_34

Generally, a number means the corresponding trace has its own subplot, while ‘_’ indicates a vertical split. Repeating a number makes that trace window larger than the others. See Figure 3-1 in the programmer’s manual for details. If a trace is active but its number is absent from the `display_layout` identifier, it is drawn in the first subplot.

 *property *frequencies

Return a numpy array of frequencies in Hz, one for each data point of the *active trace*.

 *property *power*: Any*

Set or read stimulus power in dBm (float). The valid range depends on `attenuation`. (dynamic)

 restart_averaging()

Clear averaging history.

 *property *scan_points*: Any*

Set or read sweep point count (int). Valid range 2 - 1601.

 *property *start_frequency*: Any*

Set or read start frequency in Hz (float).

 *property *stop_frequency*: Any*

Set or read stop frequency in Hz (float).

 *property *sweep_time*: Any*

Set or read sweep time in seconds (float). Valid values vary with configuration and the applied value is truncated. `sweep_time_auto_enabled` must be `False` for edits to this property to take effect.

 *property *sweep_time_auto_enabled*: Any*

Enable or disable automatic sweep time selection (bool). This is usually useful because it keeps sweep time minimal for the range, IF BW, and sweep delay time.

 *property *sweep_type*: Any*

Set or read sweep type (string).

| Setting | Description |
| --- | --- |
| LIN | Linear |
| LOG | Logarithmic |
| SEGM | Segment |
| POW | Power |

Default is linear. Segment type sweep configuration is not implemented in this class.

 *property *trace_format*: Any*

Set or read data format for the channel’s *active trace* (str). Default is MLOGarithmic. The programmer’s manual defines:

| Setting | Description |
| --- | --- |
| MLOG | Specifies the logarithmic magnitude format. |
| PHAS | Specifies the phase format. |
| GDEL | Specifies the group delay format. |
| SLIN | Selects Smith chart format (Lin/Phase). |
| SLOG | Selects Smith chart format (Log/Phase). |
| SCOM | Selects Smith chart format (Real/Imag). |
| SMIT | Selects Smith chart format (R+jX). |
| SADM | Selects Smith chart format (G+jB). |
| PLIN | Specifies the polar format (Lin). |
| PLOG | Specifies the polar format (Log). |
| POr | Selects polar format (Re/Im). |
| MLI | Specifies the linear magnitude format. |
| SWR | Specifies the SWR format. |
| REAL | Specifies the real format. |
| IMAG | Specifies the imaginary format. |
| UPH | Specifies the expanded phase format. |
| PPH | Specifies the positive phase format. |

 *property *trigger_continuous*: Any*

Set or read whether the channel triggers continuously (bool). If disabled, completion of a sweep puts the global trigger into hold state, where it will not react to triggers.

 trigger_initiate()

When trigger is in hold state, i.e. `trigger_continuous` is off and measurement is complete, initialize triggering again for one measurement.

 *property *visible_traces

Set or read how many traces are visible in the channel (int).

 *class *pymeasure.instruments.agilent.agilentE5062A.VNATrace(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Trace object belonging to a channel of the E5061A/E5062A

 activate()

Select this trace.

 *property *parameter*: Any*

Set or read the trace measurement parameter (str). Valid values are S11, S21, S12, or S22
