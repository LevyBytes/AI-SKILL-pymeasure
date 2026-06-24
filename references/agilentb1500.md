# Agilentb1500 (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Agilent B1500 Semiconductor Parameter Analyzer

### General Information

The B1500 mainframe still has configuration areas that this driver does not expose. Current support covers working with multiple SMU modules, sourcing and measuring current or voltage, and running sampling plus staircase sweep measurements. Additional measurement features are welcome. Keysight maintains the model documentation; consult the relevant â€œProgramming Guideâ€ for control-method details and parameter definitions.

### Command Translation

Alphabetized mapping from implemented B1500 commands to the driver method or attribute that handles each command.

| Command | Property/Method |
| --- | --- |
| `AAD` | `SMU.adc_type` |
| `AB` | `abort()` |
| `AIT` | `adc_setup()` |
| `AV` | `adc_averaging()` |
| `AZ` | `adc_auto_zero` |
| `BC` | `clear_buffer()` |
| `CL` | `SMU.disable()` |
| `CM` | `auto_calibration` |
| `CMM` | `SMU.meas_op_mode` |
| `CN` | `SMU.enable()` |
| `DI` | `SMU.force()` mode: `'CURRENT'` |
| `DV` | `SMU.force()` mode: `'VOLTAGE'` |
| `DZ` | `force_gnd()`, `SMU.force_gnd()` |
| `ERRX?` | `check_errors()` |
| `FL` | `SMU.filter` |
| `FMT` | `data_format()` |
| `*IDN?` | `id` |
| `*LRN?` | `query_learn()`, plus several helpers that retrieve settings and format them directly |
| `MI` | `SMU.sampling_source()` mode: `'CURRENT'` |
| `ML` | `sampling_mode` |
| `MM` | `meas_mode()` |
| `MSC` | `sampling_auto_abort()` |
| `MT` | `sampling_timing()` |
| `MV` | `SMU.sampling_source()` mode: `'VOLTAGE'` |
| `*OPC?` | `check_idle()` |
| `PA` | `pause()` |
| `PAD` | `parallel_meas` |
| `RI` | `meas_range_current` |
| `RM` | `SMU.meas_range_current_auto()` |
| `*RST` | `reset()` |
| `RV` | `meas_range_voltage` |
| `SSR` | `series_resistor` |
| `TSC` | `time_stamp` |
| `TSR` | `clear_timer()` |
| `UNT?` | `query_modules()` |
| `WAT` | `wait_time()` |
| `WI` | `SMU.staircase_sweep_source()` mode: `'CURRENT'` |
| `WM` | `sweep_auto_abort()` |
| `WSI` | `SMU.synchronous_sweep_source()` mode: `'CURRENT'` |
| `WSV` | `SMU.synchronous_sweep_source()` mode: `'VOLTAGE'` |
| `WT` | `sweep_timing()` |
| `WV` | `SMU.staircase_sweep_source()` mode: `'VOLTAGE'` |
| `XE` | `send_trigger()` |

### Examples

### Initialization of the Instrument

```python
from pymeasure.instruments.agilent import AgilentB1500

# explicitly define r/w terminations; set sufficiently large timeout in milliseconds or None.
b1500=AgilentB1500("GPIB0::17::INSTR", read_termination='\r\n', write_termination='\r\n', timeout=600000)
# query SMU config from instrument and initialize all SMU instances
b1500.initialize_all_smus()
# set data output format (required!)
b1500.data_format(21, mode=1) #call after SMUs are initialized to get names for the channels

```

### IV measurement with 4 SMUs

```python
# choose measurement mode
b1500.meas_mode('STAIRCASE_SWEEP', *b1500.smu_references) #order in smu_references determines order of measurement

# settings for individual SMUs
for smu in b1500.smu_references:
    smu.enable() #enable SMU
    smu.adc_type = 'HRADC' #set ADC to high-resoultion ADC
    smu.meas_range_current = '1 nA'
    smu.meas_op_mode = 'COMPLIANCE_SIDE' # other choices: Current, Voltage, FORCE_SIDE, COMPLIANCE_AND_FORCE_SIDE

# General Instrument Settings
# b1500.adc_averaging = 1
# b1500.adc_auto_zero = True
b1500.adc_setup('HRADC','AUTO',6)
#b1500.adc_setup('HRADC','PLC',1)

#Sweep Settings
b1500.sweep_timing(0,5,step_delay=0.1) #hold,delay
b1500.sweep_auto_abort(False,post='STOP') #disable auto abort, set post measurement output condition to stop value of sweep
# Sweep Source
nop = 11
b1500.smu1.staircase_sweep_source('VOLTAGE','LINEAR_DOUBLE','Auto Ranging',0,1,nop,0.001) #type, mode, range, start, stop, steps, compliance
# Synchronous Sweep Source
b1500.smu2.synchronous_sweep_source('VOLTAGE','Auto Ranging',0,1,0.001) #type, range, start, stop, comp
# Constant Output (could also be done using synchronous sweep source with start=stop, but then the output is not ramped up)
b1500.smu3.ramp_source('VOLTAGE','Auto Ranging',-1,stepsize=0.1,pause=20e-3) #output starts immediately! (compared to sweeps)
b1500.smu4.ramp_source('VOLTAGE','Auto Ranging',0,stepsize=0.1,pause=20e-3)

#Start Measurement
b1500.check_errors()
b1500.clear_buffer()
b1500.clear_timer()
b1500.send_trigger()

# read measurement data all at once
b1500.check_idle() #wait until measurement is finished
data = b1500.read_data(2*nop) #Factor 2 because of double sweep

#alternatively: read measurement data live
meas = []
for i in range(nop*2):
    read_data = b1500.read_channels(4+1) # 4 measurement channels, 1 sweep source (returned due to mode=1 of data_format)
    # process live data for plotting etc.
    # data format for every channel (status code, channel name e.g. 'SMU1', data name e.g 'Current Measurement (A)', value)
    meas.append(read_data)

#sweep constant sources back to 0V
b1500.smu3.ramp_source('VOLTAGE','Auto Ranging',0,stepsize=0.1,pause=20e-3)
b1500.smu4.ramp_source('VOLTAGE','Auto Ranging',0,stepsize=0.1,pause=20e-3)

```

### Sampling measurement with 4 SMUs

```python
# choose measurement mode
b1500.meas_mode('SAMPLING', *b1500.smu_references) #order in smu_references determines order of measurement
number_of_channels = len(b1500.smu_references)

# settings for individual SMUs
for smu in b1500.smu_references:
    smu.enable() #enable SMU
    smu.adc_type = 'HSADC' #set ADC to high-speed ADC
    smu.meas_range_current = '1 nA'
    smu.meas_op_mode = 'COMPLIANCE_SIDE' # other choices: Current, Voltage, FORCE_SIDE, COMPLIANCE_AND_FORCE_SIDE

b1500.sampling_mode = 'LINEAR'
# b1500.adc_averaging = 1
# b1500.adc_auto_zero = True
b1500.adc_setup('HSADC','AUTO',1)
#b1500.adc_setup('HSADC','PLC',1)
nop=11
b1500.sampling_timing(2,0.005,nop) #MT: bias hold time, sampling interval, number of points
b1500.sampling_auto_abort(False,post='BIAS') #MSC: BASE/BIAS
b1500.time_stamp = True

# Sources
b1500.smu1.sampling_source('VOLTAGE','Auto Ranging',0,1,0.001) #MV/MI: type, range, base, bias, compliance
b1500.smu2.sampling_source('VOLTAGE','Auto Ranging',0,1,0.001)
b1500.smu3.ramp_source('VOLTAGE','Auto Ranging',-1,stepsize=0.1,pause=20e-3) #output starts immediately! (compared to sweeps)
b1500.smu4.ramp_source('VOLTAGE','Auto Ranging',-1,stepsize=0.1,pause=20e-3)

#Start Measurement
b1500.check_errors()
b1500.clear_buffer()
b1500.clear_timer()
b1500.send_trigger()

meas=[]
for i in range(nop):
    read_data = b1500.read_channels(1+2*number_of_channels) #Sampling Index + (time stamp + measurement value) * number of channels
    # process live data for plotting etc.
    # data format for every channel (status code, channel name e.g. 'SMU1', data name e.g 'Current Measurement (A)', value)
    meas.append(read_data)

#sweep constant sources back to 0V
b1500.smu3.ramp_source('VOLTAGE','Auto Ranging',0,stepsize=0.1,pause=20e-3)
b1500.smu4.ramp_source('VOLTAGE','Auto Ranging',0,stepsize=0.1,pause=20e-3)

```

### Main Classes

Instrument communication classes:

-

`AgilentB1500`: Main instrument class

-

`SMU`: Created by the main instrument class for each SMU

-

`SPGU`: Created by the main instrument class for each SPGU

-

`SPGUChannel`: Created by SPGU for every channel

-

`CMU`: Created by the main instrument class for CMU

Query commands produce settings as human-readable dict objects. Use them for debugging, logging, or file headers rather than as inputs for paired setting commands.

 *class *pymeasure.instruments.agilent.agilentB1500.AgilentB1500(*adapter*, *name='Agilent B1500 Semiconductor Parameter Analyzer'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent B1500 Semiconductor Parameter Analyzer and exposes high-level measurement operations.

 *property *smu_references

Return all SMU instances as dict_values.

 *property *smu_names

Return all SMU names as a dict.

 query_learn(*query_type*)

Read the instrument settings. (`*LRN?`)

Parameters:

**query_type** (*int** or **str*) â€“ Query category, using the manual's numeric code

Return type:

dict

 query_learn_header(*query_type*, ***kwargs*)

Fetch instrument settings. (`*LRN?`)

Return a human-readable settings dict suitable for debugging output or file headers. Optional arguments follow the underlying `QueryLearn.query_learn_header()` definition.

Parameters:

**query_type** (*int** or **str*) â€“ Query category, using the manual's numeric code

Return type:

dict

 query_modules()

Request module model information from the instrument.

Return a dictionary mapping channels to module types.

Returns:

Channel:Module Type

Return type:

dict

 initialize_all_smus()

Initialize all SMUs.

Discover available modules and build one `SMU` instance for each. The created SMUs can be reached through attributes like `.smu1`, etc.

 initialize_all_spgus()

Initialize all SPGUs.

Discover available modules and build one `SPGU` instance for each. The created SPGUs can be reached through attributes like `.spgu1`, etc.

 initialize_cmu()

Initialize CMU.

Discover available modules and build the `CMU` instance for the CMU. Access it through `.cmu`.

 pause(*pause_seconds*)

Suspend command processing for the requested number of seconds. (`PA`)

Parameters:

**pause_seconds** (*int*) â€“ Pause duration in seconds

 abort()

Stop the current operation; channels may continue sourcing current/voltage. (`AB`)

 force_gnd()

Immediately drive every channel to 0 V. Use `restore_settings()` to return settings afterward. (`DZ`)

 restore_settings()

Bring all channels back to the settings that were active before `force_gnd()` was used. (`RZ`)

 *property *io_control_mode*: Any*

Set the digital I/O port control mode (`ControlMode`). (`ERMOD`)

 set_port_connection(*port*, *status*)

Change the connection state for a selected port. (`ERSSP`)

Parameters:

-

**port** (*PgSelectorPort*) – Port number

-

**status** (*PgSelectorConnectionStatus*) – Connection status

 check_errors()

Check for errors. (`ERRX?`)

 check_idle()

Determine whether the instrument is idle. (`*OPC?`)

Alternate name for [`complete()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.complete).

 clear_buffer()

Clear output data buffer. (`BC`)

 clear_timer()

Clear timer count. (`TSR`)

 send_trigger()

Issue the measurement-start trigger, excluding High Speed Spot. (`XE`)

 *property *auto_calibration

Control SMU auto-calibration every 30 minutes (bool). (`CM`)

 data_format(*output_format*, *mode=0*)

Choose the data output format; see parameter documentation. (`FMT`)

Call this once during a session so later measurement values read from the instrument can be parsed with the selected data format.

Currently implemented are format 1, 11, and 21.

Parameters:

-

**output_format** (*str*) – Output format string, e.g. `FMT21`

-

**mode** (*int*) â€“ Data output mode; defaults to 0, returning only measurement data

 *property *parallel_meas

Turn parallel measurements on or off (bool). (`PAD`)

Applies to SMUs that use HSADC with measurement modes 1, 2, 10, 18.

Type:

bool

 query_meas_settings()

Retrieve instrument settings for `TM`, `AV`, `CM`, `FMT`, and `MM` commands (31).

 query_meas_mode()

Retrieve the `MM` command settings, which are part of 31, from the instrument.

 meas_mode(*mode*, **args*)

Configure channel measurement mode. (`MM`)

The SMU or CMU references determine the order in which measurements run.

Parameters:

-

**mode** (*MeasMode*) – Measurement mode

-

**args** (*SMU*) â€“ References to SMU or CMU objects

 query_adc_setup()

Retrieve ADC settings (55, 56) from the instrument.

 adc_setup(*adc_type*, *mode*, *N=''*)

Configure ADC operation mode and parameters for each ADC type. (`AIT`)

Defaults:

>
-

HSADC: Auto N=1, Manual N=1, PLC N=1, Time N=0.000002(s)

-

HRADC: Auto N=6, Manual N=3, PLC N=1

Parameters:

-

**adc_type** (*ADCType*) – ADC type

-

**mode** (*ADCMode*) – ADC mode

-

**N** (*str*) â€“ Extra parameter; see documentation, defaults to `''`

 adc_averaging(*number*, *mode='Auto'*)

Configure the HSADC averaging sample count. (`AV`)

Defaults: N=1, Auto

Parameters:

-

**number** (*int*) – Number of averages

-

**mode** (*AutoManual*) â€“ Operating mode (`'Auto','Manual'`), defaults to â€˜Autoâ€™

 *property *adc_auto_zero

Control ADC zero function (bool). (`AZ`)

When disabled, the integration time is reduced by half.

 *property *time_stamp

Control Time Stamp function (bool). (`TSC`)

 query_time_stamp_setting()

Retrieve time stamp settings (60) from the instrument.

 wait_time(*wait_type*, *N*, *offset=0*)

Configure wait time. (`WAT`)

Parameters:

-

**wait_type** (*WaitTimeType*) – Wait time type

-

**N** (*float*) â€“ Initial-wait-time coefficient, default: 1

-

**offset** (*int*) â€“ Wait-time offset, defaults to 0

 query_staircase_sweep_settings()

Retrieve Staircase Sweep Measurement settings (33) from the instrument.

 sweep_timing(*hold*, *delay*, *step_delay=0*, *step_trigger_delay=0*, *measurement_trigger_delay=0*)

Configure timing values for staircase or multi channel sweep operation. (`WT`)

Parameters:

-

**hold** (*float*) – Hold time

-

**delay** (*float*) – Delay time

-

**step_delay** (*float*) â€“ Step delay duration, defaults to 0

-

**step_trigger_delay** (*float*) â€“ Trigger delay duration, defaults to 0

-

**measurement_trigger_delay** (*float*) â€“ Measurement trigger delay duration, defaults to 0

 sweep_auto_abort(*abort*, *post='START'*)

Turn the automatic abort function on or off. (`WM`)

The post measurement condition is configured as well.

Parameters:

-

**abort** (*bool*) – Enable/Disable automatic abort

-

**post** (*StaircaseSweepPostOutput*) â€“ Post-measurement output, defaults to â€˜Startâ€™

 query_sampling_settings()

Retrieve sampling measurement settings (47) from the instrument.

 *property *sampling_mode

Choose linear or logarithmic sampling mode. (`ML`)

Type:

`SamplingMode`

 sampling_timing(*hold_bias*, *interval*, *number*, *hold_base=0*)

Configure timing values for the sampling measurement. (`MT`)

Parameters:

-

**hold_bias** (*float*) – Bias hold time

-

**interval** (*float*) – Sampling interval

-

**number** (*int*) – Number of Samples

-

**hold_base** (*float*) â€“ Base hold duration, defaults to 0

 sampling_auto_abort(*abort*, *post='Bias'*)

Turn the automatic abort function on or off. (`MSC`)

The post measurement condition is configured as well.

Parameters:

-

**abort** (*bool*) – Enable/Disable automatic abort

-

**post** (*SamplingPostOutput*) â€“ Post-measurement output, defaults to â€˜Biasâ€™

 read_data(*number_of_points*)

Read the full buffer and return the contents as a Pandas DataFrame.

Provide the measurement-point count so the data list can be split correctly.

Parameters:

**number_of_points** (*int*) â€“ Count of measurement points

Returns:

Measurement Data

Return type:

pd.DataFrame

 read_channels(*nchannels*)

Read one measurement point from the buffer for the requested channel count.

Parameters:

**nchannels** (*int*) â€“ Count of channels returning data, including measurement channels and sweep sources according to data output settings

Returns:

Measurement data

Return type:

tuple

 query_series_resistor()

Retrieve series resistor status (53) across all SMUs.

 query_meas_range_current_auto()

Retrieve auto ranging mode status (54) across all SMUs.

 query_meas_op_mode()

Retrieve SMU measurement operation mode (46) across all SMUs.

 query_meas_ranges()

Retrieve measurement ranging status (32) across all SMUs.

 *class *pymeasure.instruments.agilent.agilentB1500.SMU(*parent*, *index*, *smu_type*, *name*, *slot*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Expose SMU-specific operations for the Agilent B1500 mainframe.

Parameters:

-

**parent** (*AgilentB1500*) â€“ B1500 mainframe class instance

-

**index** (*int*) â€“ SMU index

-

**smu_type** (*str*) â€“ SMU type

-

**name** (*str*) â€“ SMU name

-

**slot** (*int*) â€“ SMU slot number

 query_learn(*query_type*, *command*)

Forward to the B1500 `query_learn()` method.

 check_errors()

Forward to the B1500 `check_errors()` method.

 *property *status

Get status of the SMU.

 enable()

Enable source/measurement channel. (`CN`)

 disable()

Disable source/measurement channel. (`CL`)

 force_gnd()

Immediately force the output to 0 V. (`DZ`)

Use `restore_settings()` to recover the current settings.

 restore_settings()

Return the channel to the settings present before `force_gnd()` was called. (`RZ`)

 *property *filter

Control SMU filter enable/disable state (bool). (`FL`)

 *property *series_resistor

Control 1 MOhm series resistor enable/disable state (bool). (`SSR`)

 *property *meas_op_mode

Control SMU measurement operation mode. (`CMM`)

Type:

`MeasOpMode`

 *property *adc_type

Select ADC type for an individual measurement channel. (`AAD`)

Type:

`ADCType`

 force(*source_type*, *source_range*, *output*, *comp=''*, *comp_polarity=''*, *comp_range=''*)

Immediately source DC current or voltage from the SMU. (`DI`, `DV`)

Parameters:

-

**source_type** (*str*) – Source type (`'Voltage','Current'`)

-

**source_range** (*int** or **str*) â€“ Output range index or range name

-

**output** (*float*) â€“ Value sourced at the output in A or V

-

**comp** (*float*) â€“ Compliance value; defaults to the previous setting

-

**comp_polarity** (*CompliancePolarity*) â€“ Compliance polarity; defaults to auto

-

**comp_range** (*int** or **str*) â€“ Compliance range selection; defaults to auto

 ramp_source(*source_type*, *source_range*, *target_output*, *comp=''*, *comp_polarity=''*, *comp_range=''*, *stepsize=0.001*, *pause=0.02*)

Move from the configured value to a target output using the supplied step size.

A pause interval is inserted between successive steps.

Parameters:

-

**source_type** (*str*) â€“ Selected source type (`'Voltage'` or `'Current'`)

-

**source_range** (*int** or **str*) â€“ Output range index or range name

-

**target_output** (*float*) â€“ Target voltage or current at the output

-

**comp** (*float*) â€“ Compliance; defaults to the previous setting

-

**comp_polarity** (*CompliancePolarity*) â€“ Compliance polarity; defaults to auto

-

**comp_range** (*int** or **str*) â€“ Compliance range selection; defaults to auto

-

**stepsize** (*float*) â€“ Largest permitted step size

-

**pause** (*float*) â€“ Wait time in seconds between steps

 *property *meas_range_current

Control current measurement range index. (`RI`)

Available settings vary by SMU type, for example `0` for Auto Ranging: `SMUCurrentRanging`

 *property *meas_range_voltage

Control voltage measurement range index. (`RV`)

Available settings vary by SMU type, for example `0` for Auto Ranging: `SMUVoltageRanging`

 meas_range_current_auto(*mode*, *rate=50*)

Configure auto range operation; consult the documentation. (`RM`)

Parameters:

-

**mode** (*int*) – Range changing operation mode

-

**rate** (*int*) â€“ Parameter for calculating the *current* value, defaults to 50

 staircase_sweep_source(*source_type*, *mode*, *source_range*, *start*, *stop*, *steps*, *comp*, *Pcomp=''*)

Configure staircase sweep source parameters. (`WV` or `WI`)

Parameters:

-

**source_type** (*str*) – Source type (`'Voltage', 'Current'`)

-

**mode** (*SweepMode*) – Sweep mode

-

**source_range** (*int*) – Source range index

-

**start** (*float*) – Sweep start value

-

**stop** (*float*) – Sweep stop value

-

**steps** (*int*) â€“ Sweep step count

-

**comp** (*float*) – Compliance value

-

**Pcomp** (*float*) â€“ Power compliance; defaults to not set

 synchronous_sweep_source(*source_type*, *source_range*, *start*, *stop*, *comp*, *Pcomp=''*)

Configure the synchronous staircase sweep source, current or voltage, and its parameters. (`WSV` or `WSI`)

Parameters:

-

**source_type** (*str*) – Source type (`'Voltage','Current'`)

-

**source_range** (*int*) – Source range index

-

**start** (*float*) – Sweep start value

-

**stop** (*float*) – Sweep stop value

-

**comp** (*float*) – Compliance value

-

**Pcomp** (*float*) â€“ Power compliance; defaults to not set

 sampling_source(*source_type*, *source_range*, *base*, *bias*, *comp*)

Configure the DC current or voltage source used for sampling measurement. (`MV` or `MI`)

`force()` commands on this channel replace the sampling source setting.

Parameters:

-

**source_type** (*str*) – Source type (`'Voltage','Current'`)

-

**source_range** (*int*) – Source range index

-

**base** (*float*) – Base voltage/current

-

**bias** (*float*) – Bias voltage/current

-

**comp** (*float*) – Compliance value

 set_cv_parameters(*mode*, *start*, *stop*, *steps*, *comp=None*)

Configure mode and sweep parameters for `MeasMode.CV_SWEEP` measurement. (`WDCV`)

Parameters:

-

**mode** (`SweepMode`) – Sweep mode

-

**start** (`float`) â€“ Starting voltage for the sweep in V

-

**stop** (`float`) â€“ Ending voltage for the sweep in V

-

**steps** (`int`) â€“ Staircase sweep step count

-

**comp** (`Optional`[`float`]) â€“ Compliance current in A. If not provided, the existing value remains in use. (default: `None`)

Return type:

`None`

 *class *pymeasure.instruments.agilent.agilentB1500.SPGU(*parent*, *channel*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Expose SPGU-module operations for the Agilent B1500 mainframe.

Parameters:

-

**parent** (*AgilentB1500*) â€“ B1500 mainframe class instance

-

**channel** (*int*) â€“ SPGU channel number

 *property *output*: Any*

Set SPGU output state. (`SRP`, `SPP`) Enabling starts SPGU output; disabling stops output and drives channels to the base voltage.

 *property *operation_mode*: Any*

Configure Semiconductor Pulse Generator Unit (SPGU) mode. (`SIM`) This affects every SPGU module installed in the B1500 and also forces 0 V on SPGU channels whose output switch is ON.

 *property *period*: Any*

Configure the SPGU channel pulse period (`SPPER`) in seconds (float). The value applies to all installed SPGU modules.

 set_output_mode(*mode*, *condition=None*)

Configure operating mode for SPGU channel outputs. (`SPRM`)

The setting affects every SPGU module installed in the B1500.

Parameters:

-

**mode** (*SPGUOperationMode*) – SPGU operation mode

-

**condition** (*int** or **float** or **None*) â€“ Pulse count for `SPGUOutputMode.COUNT` or output duration for `SPGUOutputMode.DURATION`; ignored for `SPGUOutputMode.FREE_RUN`

 get_output_mode()

Read the current operating mode and condition for SPGU channel outputs. (`SPRM?`)

Returns:

Tuple of (mode, condition)

Return type:

tuple

 *property *complete*: Any*

Read whether SPGU output is complete. (`SPST?`)

 *class *pymeasure.instruments.agilent.agilentB1500.SPGUChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Agilent B1500 mainframe SPGU Channel.

 *property *enabled*: Any*

Control SPGU channel enable/disable state. (`CN`, `CL`)

 *property *load_impedance*: Any*

Configure load impedance (`SER`) in Ohm (float).

 set_output_voltage(*source=1*, *base_voltage=0*, *peak_voltage=0*)

Configure the SPGU channel output voltage. (`SPV`)

Parameters:

-

**source** (*SPGUSignalSource** or **int*) â€“ Output-voltage signal source, defaults to `SPGUSignalSource.PULSE_SIGNAL_1`

-

**base_voltage** (*float*) â€“ Pulse base voltage or DC output voltage in V; defaults to 0

-

**peak_voltage** (*float*) â€“ Pulse peak voltage in V; defaults to 0

 get_output_voltage(*source=1*)

Read output voltage for the selected signal source. (`SPV?`)

Parameters:

**source** (*SPGUSignalSource** or **int*) â€“ Selected signal source

Returns:

Return tuple format: (base_voltage, peak_voltage)

Return type:

tuple

 *property *output_mode*: Any*

Configure SPGU channel output mode. (`SPM`) Before setting this mode, set the SPGU operating mode to PG with the SIM 0 command.

 set_pulse_timings(*source=1*, *delay=0*, *width=1e-07*, *rise_time=2e-08*, *fall_time=None*)

Configure SPGU channel timing parameters. (`SPT`)

Before assigning pulse timings, set the SPGU operating mode to PG with the `SIM 0` command.

Parameters:

-

**source** (*SPGUSignalSource** or **int*) â€“ Pulse-timing signal source, defaults to `SPGUSignalSource.PULSE_SIGNAL_1`

-

**delay** (*float*) â€“ Pulse delay in seconds; defaults to 0

-

**width** (*float*) â€“ Pulse width in seconds; defaults to 1e-7

-

**rise_time** (*float*) â€“ Pulse rise time in seconds; defaults to 2e-8

-
