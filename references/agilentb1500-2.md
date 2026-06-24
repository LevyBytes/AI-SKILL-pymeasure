# Agilentb1500 (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

**fall_time** (*float*) - Pulse fall time, in seconds; when None, rise_time is used as the default

 get_pulse_timings(*source=1*)

Read SPGU channel timing parameters. (`SPT?`)

Before pulse timings are read, place SPGU operating mode in PG with `SIM 0`.

Parameters:

**source** (*SPGUSignalSource** or **int*) - Pulse timing signal source; default is `SPGUSignalSource.PULSE_SIGNAL_1`

Returns:

Returns (delay, width, rise_time, fall_time) as a tuple

Return type:

tuple

 apply_setup()

Send the present configuration to the SPGU channel. (`SPUPD`)

Behavior follows `SPGU.operation_mode` (`SIM`):

-

PG mode: base output voltage comes from `SPV`

-

ALWG mode: output starts from the waveform initial value

 *class *pymeasure.instruments.agilent.agilentB1500.CMU(*parent*, *slot*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Adds CMU-specific methods for an Agilent B1500 mainframe.

Parameters:

-

**parent** (`AgilentB1500`) - B1500 mainframe class instance

-

**slot** (`int`) - CMU slot number

 *property *enabled*: Any*

Control CMU enable/disable state. (`CN`, `CL`)

 *property *voltage_ac*: Any*

Configure AC voltage amplitude in V. (`ACV`)

 *property *frequency_ac*: Any*

Configure AC voltage frequency in Hz. (`FC`)

 set_measurement_mode(*measurement_mode*)

Configure MFCMU impedance measurement mode. (`IMP`)

Each MFCMU mode measures two parameters. The default is `MFCMUMeasurementMode.CP_G`.

Note

This command has no effect when the output format is binary data (FMT3, FMT4, FMT13, FMT14).

Parameters:

**measurement_mode** (`MFCMUMeasurementMode`) – Measurement mode.

Return type:

`None`

 set_cv_timings(*hold_time*, *delay_time*, *step_delay_time=0.0*, *step_source_trigger_delay_time=0.0*)

Configure timing for `MeasMode.CV_SWEEP` measurement. (`WTDCV`)

Parameters:

-

**hold_time** (`float`) - In seconds, the wait after measurement start before delay time begins for the first step.

-

**delay_time** (`float`) - In seconds, the wait after step output forcing begins before step measurement starts.

-

**step_delay_time** (`float`) –

In seconds, the wait after a step measurement starts before the next step output starts being forced.

When step_delay_time is less than the measurement time, B1500 waits for measurement completion before forcing the next step output. (default: `0.0`)

-

**step_source_trigger_delay_time** (`float`) - In seconds, the wait after step output setup finishes before a step output setup completion trigger is sent. (default: `0.0`)

Return type:

`None`

 set_cv_parameters(*mode*, *start*, *stop*, *steps*)

Configure mode and sweep settings for `MeasMode.CV_SWEEP` measurement. (`WDCV`)

Parameters:

-

**mode** (`SweepMode`) – Sweep mode

-

**start** (`float`) - Start voltage for the sweep in V

-

**stop** (`float`) - Stop voltage for the sweep in V

-

**steps** (`int`) - Staircase sweep step count

Return type:

`None`

 force_dc_bias(*voltage*)

Immediately force DC voltage from the CMU. (`DCV`)

Parameters:

**voltage** (`float`) - DC bias voltage in V

Return type:

`None`

 set_scuu_path(*path*)

Configure the SMU CMU unify unit (SCUU) connection path. (`SSP`)

Use this function only when the CMU and SMU CMU unify unit (SCUU) are installed.

Parameters:

**path** (`SCUUPath`) - SCUU measurement path

Return type:

`None`

### Supporting Classes

Classes that provide additional functionalities:

-

`QueryLearn`: handles readout processing for instrument settings

-

`SMUCurrentRanging`, `SMUVoltageRanging`: range options for SMU types and range-name to index conversion (base: `Ranging`)

 *class *pymeasure.instruments.agilent.agilentB1500.QueryLearn

Bases: `object`

Methods for sending `*LRN?` (learn) and interpreting its response.

 *static *query_learn(*ask*, *query_type*)

Send `*LRN?` (learn) to the instrument to read configuration, returning a dictionary of commands with set values.

Parameters:

**query_type** (*int*) - Query type as defined by the programming guide

Returns:

Dictionary containing commands and set values

Return type:

dict

 *classmethod *query_learn_header(*ask*, *query_type*, *smu_references*, *single_command=False*)

Send `*LRN?` (learn) to the instrument to read configuration, then convert the information into human-readable values for debugging or file headers.

Parameters:

-

**ask** (*Instrument.ask*) - instrument ask method

-

**query_type** (*int** or **str*) - Programming Guide number

-

**smu_references** (*dict*) - SMU references keyed by channel

-

**single_command** (*str*) - return only one command when requested; defaults to False

Returns:

Read configuration

Return type:

dict

 *static *to_dict(*parameters*, *names*, **args*)

Build a dict of named parameters from values returned by `query_learn()` plus an ordered list of matching parameter names and an optional function.

Parameters:

-

**parameters** (*dict*) - Parameters for a single command returned by `query_learn()`

-

**names** (*list*) - ordered names list, or ordered (name, function) tuples

Returns:

Parameter name and (processed) parameter

Return type:

dict

 *class *pymeasure.instruments.agilent.agilentB1500.Ranging(*supported_ranges*, *ranges*, *fixed_ranges=False*)

Bases: `object`

Possible output and measurement range settings for SMU current/voltage.

Converts available voltage/current range names to indices and back.

Parameters:

-

**supported_ranges** (*list*) - Supported ranges, represented as a list of range indices

-

**ranges** (*dict*) - Complete range-name mapping `{Name: Indices}`

-

**fixed_ranges** (*bool*) - Include fixed ranges (negative indices); defaults to False

 __call__(*input_value*)

Return the named tuple (name/index) for the specified Range.

Raises an error when this SMU does not support the range.

Parameters:

**input_value** (*str** or **int*) - Range name or index

Returns:

Range named tuple (name/index)

Return type:

namedtuple

 *class *pymeasure.instruments.agilent.agilentB1500.SMUCurrentRanging(*smu_type*)

Bases: `object`

Converts range names and indices for current measurement/sourcing.

The SMU type is used to check whether ranges are valid.

For current measurement, a range string without 'limited auto ranging'/'range fixed' uses 'limited auto ranging' by default.

Complete form: `'1 nA range fixed'` or `'1 nA limited auto ranging'`

`'1 nA'` uses `'1 nA limited auto ranging'` as the default

 *class *pymeasure.instruments.agilent.agilentB1500.SMUVoltageRanging(*smu_type*)

Bases: `object`

Converts range names and indices for voltage measurement/sourcing.

The SMU type is used to check whether ranges are valid.

For voltage measurement, a range string without 'limited auto ranging'/'range fixed' uses 'limited auto ranging' by default.

Complete form: `'2 V range fixed'` or `'2 V limited auto ranging'`

`'2 V'` uses `'2 V limited auto ranging'` as the default

### Enumerations

Enumerations make available parameters easier to choose where applicable. Methods accept either a member name or number; use the name when readability matters. The instrument receives the member number. Calling string conversion on an enumeration member produces a title case string with whitespace separators (`__str__()`), and that string is not valid for selecting the enumeration member later. It is intended only for logging or documentation.

 *class *pymeasure.instruments.agilent.agilentB1500.CustomIntEnum(*new_class_name*, */*, *names*, ***, *module=None*, *qualname=None*, *type=None*, *start=1*, *boundary=None*)

Bases: `IntEnum`

Provide additional methods to IntEnum:

-

When converted to string, names have `_` replaced by spaces and are changed to title case

-

The get classmethod returns an enum reference from a name or integer

 __str__()

Return the enum value as a title case string.

 *classmethod *get(*input_value*)

Return an Enum member selected by name or value.

Parameters:

**input_value** (*str** or **int*) - Enum name or value

Returns:

Enum member

 *class *pymeasure.instruments.agilent.agilentB1500.ADCType(**values*)

Bases: `CustomIntEnum`

ADC Type.

 HSADC* = 0*

High-speed ADC

 HRADC* = 1*

High-resolution ADC

 HSADC_PULSED* = 2*

High-speed ADC used for pulsed measurements

 *class *pymeasure.instruments.agilent.agilentB1500.ADCMode(**values*)

Bases: `CustomIntEnum`

ADC Mode.

 AUTO* = 0*

 MANUAL* = 1*

 PLC* = 2*

Power line cycle mode

 TIME* = 3*

Measurement time mode

 *class *pymeasure.instruments.agilent.agilentB1500.AutoManual(**values*)

Bases: `CustomIntEnum`

Auto/Manual selection.

 AUTO* = 0*

 MANUAL* = 1*

 *class *pymeasure.instruments.agilent.agilentB1500.ControlMode(**values*)

Bases: `CustomIntEnum`

Digital I/O port control mode.

 GENERAL* = 0*

General purpose control mode (default)

 SMU_PGU_SELECTOR* = 1*

16440A SMU/PGU selector (B1500A-A04) mode control

 N1258A_N1259A* = 2*

N1258A/N1259A module selector mode control

 N1265A* = 4*

N1265A Ultra High Current Expander/Fixture mode control

 N1266A* = 8*

N1266A High Voltage Source Monitor Unit Current Expander mode control

 N1268A* = 16*

N1268A Ultra High Voltage Expander mode control

 N1272A* = 32*

N1272A Device Capacitance Selector mode control

 *class *pymeasure.instruments.agilent.agilentB1500.MeasMode(**values*)

Bases: `CustomIntEnum`

Measurement Mode.

 SPOT* = 1*

 STAIRCASE_SWEEP* = 2*

 SAMPLING* = 10*

 SPOT_C* = 17*

Spot capacitance measurement (MFCMU)

 CV_SWEEP* = 18*

CV (DC bias) sweep measurement (SMU/MFCMU)

 PULSED_SPOT_C* = 19*

Pulsed spot capacitance measurement (MFCMU)

 PULSED_CV_SWEEP* = 20*

Pulsed CV sweep measurement (MFCMU)

 C_F_SWEEP* = 22*

Capacitance frequency sweep (MFCMU)

 CV_AC_SWEEP* = 23*

CV (AC bias) sweep measurement (MFCMU)

 C_T_SAMPLING* = 26*

Capacitance sampling measurement (MFCMU)

 *class *pymeasure.instruments.agilent.agilentB1500.MeasOpMode(**values*)

Bases: `CustomIntEnum`

Measurement Operation Mode.

 COMPLIANCE_SIDE* = 0*

During voltage source operation, measure current; during current source operation, measure voltage.

 CURRENT* = 1*

 VOLTAGE* = 2*

 FORCE_SIDE* = 3*

During current source operation, measure current; during voltage source operation, measure voltage.

 COMPLIANCE_AND_FORCE_SIDE* = 4*

Synchronous current and voltage measurement. Results list compliance side data first, then force side data.

 *class *pymeasure.instruments.agilent.agilentB1500.PgSelectorPort(**values*)

Bases: `CustomIntEnum`

SMU/PG selector output port.

 OUTPUT_1_FIRST* = 0*

Output 1 on the first selector

 OUTPUT_2_FIRST* = 1*

Output 2 on the first selector

 OUTPUT_1_SECOND* = 2*

Output 1 on the second selector

 OUTPUT_2_SECOND* = 3*

Output 2 on the second selector

 *class *pymeasure.instruments.agilent.agilentB1500.PgSelectorConnectionStatus(**values*)

Bases: `CustomIntEnum`

I/O port connection status.

 NO_CONNECTION* = 0*

Everything open. Connection is broken. Initial setting

 SMU_ON* = 1*

SMU on. Connects to the SMU input.

 PGU_ON* = 2*

PGU on. Connects to the PGU input.

 PGU_OPEN* = 3*

PGU open. Produced by opening the semiconductor relay on the PGU on port.

 *class *pymeasure.instruments.agilent.agilentB1500.SCUUPath(**values*)

Bases: `CustomIntEnum`

SMU CMU unify unit (SCUU) connection path

 SMU1* = 1*

Output SMU located in slot cmu.id - 1

 SMU2* = 2*

Output SMU located in slot cmu.id - 2

 SMU_BOTH* = 3*

Output SMU located in slot cmu.id - 1 and cmu.id - 2

 *class *pymeasure.instruments.agilent.agilentB1500.SweepMode(**values*)

Bases: `CustomIntEnum`

Sweep Mode.

 LINEAR_SINGLE* = 1*

Linear sweep with a single stair, from start to stop.

 LOG_SINGLE* = 2*

Log sweep with a single stair, from start to stop.

 LINEAR_DOUBLE* = 3*

Linear sweep with a double stair, from start to stop to start.

 LOG_DOUBLE* = 4*

Log sweep with a double stair, from start to stop to start.

 *class *pymeasure.instruments.agilent.agilentB1500.SamplingMode(**values*)

Bases: `CustomIntEnum`

Sampling Mode.

 LINEAR* = 1*

 LOG_10* = 2*

Logarithmic 10 data points/decade

 LOG_25* = 3*

Logarithmic 25 data points/decade

 LOG_50* = 4*

Logarithmic 50 data points/decade

 LOG_100* = 5*

Logarithmic 100 data points/decade

 LOG_250* = 6*

Logarithmic 250 data points/decade

 LOG_5000* = 7*

Logarithmic 5000 data points/decade

 *class *pymeasure.instruments.agilent.agilentB1500.SamplingPostOutput(**values*)

Bases: `CustomIntEnum`

Output after sampling.

 BASE* = 1*

 BIAS* = 2*

 *class *pymeasure.instruments.agilent.agilentB1500.SPGUChannelOutputMode(**values*)

Bases: `CustomIntEnum`

Output mode of SPGU channel.

 DC* = 0*

DC output mode

 SIGNAL_SOURCE_1* = 1*

2-level pulse output mode that uses pulse signal source 1

 SIGNAL_SOURCE_2* = 2*

2-level pulse output mode that uses pulse signal source 2

 SIGNAL_SOURCE_1_2* = 3*

3-level pulse output mode that uses pulse signal source 1 and 2

 *class *pymeasure.instruments.agilent.agilentB1500.SPGUSignalSource(**values*)

Bases: `CustomIntEnum`

Signal source for SPGU.

 DC* = 0*

 PULSE_SIGNAL_1* = 1*

 PULSE_SIGNAL_2* = 2*

 *class *pymeasure.instruments.agilent.agilentB1500.SPGUOperationMode(**values*)

Bases: `CustomIntEnum`

Semiconductor Pulse Generator Unit (SPGU) operation mode

 PG* = 0*

PG (pulse output) mode

 ALWG* = 1*

ALWG (arbitrary linear wave output) mode

 *class *pymeasure.instruments.agilent.agilentB1500.SPGUOutputMode(**values*)

Bases: `CustomIntEnum`

SPGU channel output operating mode

 FREE_RUN* = 0*

Free Run mode. Output continues until `SPP` is executed. The condition parameter is unnecessary.

 COUNT* = 1*

Count mode. Outputs the number of pulses specified by the condition parameter when PG mode is set with `SIM 0`, or the number of sequences specified by the condition parameter when ALWG mode is set with `SIM 1`.

 DURATION* = 2*

Duration mode. Output lasts for the duration specified by the condition parameter.

 *class *pymeasure.instruments.agilent.agilentB1500.MFCMUMeasurementMode(**values*)

Bases: `CustomIntEnum`

Multi Frequency Capacitance Measurement Unit (MFCMU) measurement mode.

 R_X* = 1*

R (resistance, Ohm) paired with X (reactance, Ohm)

 G_B* = 2*

G (conductance, S) paired with B (susceptance, S)

 Z_PHASE_RAD* = 10*

Z (impedance, Ohm) paired with phase (radian)

 Z_PHASE_DEG* = 11*

Z (impedance, Ohm) paired with phase (degree)

 Y_PHASE_RAD* = 20*

Y (admittance, S) paired with phase (radian)

 Y_PHASE_DEG* = 21*

Y (admittance, S) paired with phase (degree)

 CP_G* = 100*

Cp (parallel capacitance, F) paired with G (conductance, S)

 CP_D* = 101*

Cp (parallel capacitance, F) paired with D (dissipation factor)

 CP_Q* = 102*

Cp (parallel capacitance, F) paired with Q (quality factor)

 CP_RP* = 103*

Cp (parallel capacitance, F) paired with Rp (parallel resistance, Ohm)

 CS_RS* = 200*

Cs (series capacitance, F) paired with Rs (series resistance, Ohm)

 CS_D* = 201*

Cs (series capacitance, F) paired with D (dissipation factor)

 CS_Q* = 202*

Cs (series capacitance, F) paired with Q (quality factor)

 LP_G* = 300*

Lp (parallel inductance, H) paired with G (conductance, S)

 LP_D* = 301*

Lp (parallel inductance, H) paired with D (dissipation factor)

 LP_Q* = 302*

Lp (parallel inductance, H) paired with Q (quality factor)

 LP_RP* = 303*

Lp (parallel inductance, H) paired with Rp (parallel resistance, Ohm)

 LS_RS* = 400*

Ls (series inductance, H) paired with Rs (series resistance, Ohm)

 LS_D* = 401*

Ls (series inductance, H) paired with D (dissipation factor)

 LS_Q* = 402*

Ls (series inductance, H) paired with Q (quality factor)

 *class *pymeasure.instruments.agilent.agilentB1500.StaircaseSweepPostOutput(**values*)

Bases: `CustomIntEnum`

Output after staircase sweep.

 START* = 1*

 STOP* = 2*

 *class *pymeasure.instruments.agilent.agilentB1500.CompliancePolarity(**values*)

Bases: `CustomIntEnum`

Compliance polarity.

 AUTO* = 0*

 MANUAL* = 1*

 *class *pymeasure.instruments.agilent.agilentB1500.WaitTimeType(**values*)

Bases: `CustomIntEnum`

Wait time type.

 SMU_SOURCE* = 1*

wait period before the output value changes

 SMU_MEASUREMENT* = 2*

wait before starting the measurement

 CMU_MEASUREMENT* = 3*

wait before starting the measurement
