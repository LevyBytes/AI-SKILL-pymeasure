# Texio, Temptronic, Kepco, Edwards

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covered entries by family: TEXIO; power supply TEXIO PSW-360L30 Power Supply; Thermostream model Temptronic ATS525 Thermostream; Thermostream model Temptronic ECO560 Thermostream; Temptronic; Thermostream model Temptronic ATS545 Thermostream; base API Temptronic Base Class; vendor KEPCO INC.; supply interface BOP Bipolar Power Supply with BIT 4886 Digital Interface Card; vendor Edwards; pump Edwards nxds vacuum pump.

## TEXIO

### TEXIO

Implemented TEXIO instrument documentation is grouped here. For another model, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [TEXIO PSW-360L30 Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/texio/texioPSW360L30.html)
  - [`TexioPSW360L30`](https://pymeasure.readthedocs.io/en/latest/api/instruments/texio/texioPSW360L30.html#pymeasure.instruments.texio.TexioPSW360L30)

## TEXIO PSW-360L30 Power Supply

### TEXIO PSW-360L30 Power Supply

 *class *pymeasure.instruments.texio.TexioPSW360L30(*adapter*, *name='TEXIO PSW-360L30 Power Supply'*, ***kwargs*)

Bases: [`Keithley2260B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2260B.html#pymeasure.instruments.keithley.Keithley2260B)

Provides a minimal TEXIO PSW-360L30 Power Supply representation and a high-level interface for instrument operations.

When using tcpip, this device listens only on port 2268; that port is not configurable. example connection string: ?TCPIP::xxx.xxx.xxx.xxx::2268::SOCKET?

On Linux USB connections, the kernel automatically creates a /dev/ttyACMX device. The serial settings are fixed at 9600?8-N-1.

This interface terminates reads with Line-Feed n.

This driver derives from the Keithley2260B implementation, so every instruction supported by the Keithley 2260B driver is available on the TEXIO PSW-360L30 power supply.

It adds only the ?output? property, an alias for the Keithley 2260B ?enabled? property. The name ?enabled? can be ambiguous because it does not say whether it affects the whole device or just the output.

```python
source = TexioPSW360L30("TCPIP::xxx.xxx.xxx.xxx::2268::SOCKET")
source.voltage = 1
print(source.voltage)
print(source.current)
print(source.power)
print(source.applied)

```

 *property *applied*: Any*

Set voltage (volts) and current (amps) together by passing a tuple of (voltage, current). Constant current or constant voltage mode determines whether the instrument reaches the requested values.

 check_errors()

Log all system errors returned by the instrument.

 check_get_errors()

After reading a property, check for errors and log anything reported.

Invoked for a property when `check_get_errors=True` is configured.

Overrides may raise an Exception for selected error conditions.

Returns:

`list` – List of error entries.

 check_set_errors()

After writing a property, check for errors and log anything reported.

Invoked for a property when `check_set_errors=True` is configured.

An override may raise an Exception for chosen error conditions.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. The Operation Complete query puts ASCII character 1 in the device?s Output Queue after all pending selected device operations finish.

 *property *current*: Any*

Return the current (in Ampere) delivered by the dc power supply.

 *property *current_limit*: Any*

Set source current in amps without validating it against the allowed range. In constant current or constant voltage operation, the actual current achieved can differ from the requested value. (float)

 *property *enabled

Enable or disable the output; see `output_enabled`.

 *property *error

Return the instrument?s next error as a list containing code and message.

 *property *id*: Any*

Return the instrument identification string.

 *property *next_error*: Any*

Read the next queued error. To read and log the whole error queue, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *output_enabled*: Any*

Enable or disable the source, accepting True or False. (bool)

 *property *power*: Any*

Return the power (in Watt) currently produced by the dc power supply.

 read(***kwargs*)

Read until, but not including, read_termination, or consume the entire read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) ? Byte count to read; -1 means the entire read buffer is read.

-

**kwargs** ? Keyword arguments passed to the adapter.

Returns bytes:

Bytes returned by the instrument, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Disable output, call parent function

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 *property *voltage*: Any*

Return the voltage (in Volt) delivered by the dc power supply.

 *property *voltage_setpoint*: Any*

Set source voltage in volts without validating it against the allowed range. In constant current or constant voltage operation, the actual voltage achieved can differ from the requested value. (float)

 wait_for(*query_delay=None*)

Pause for a short interval; ?ask? uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) ? Time to wait between writing and reading in seconds. None uses the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) ? command string sent to the instrument

-

**kwargs** ? Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) ? Values that should be transmitted.

-

****kwargs** (**args**,*) ? Additional arguments forwarded to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send the supplied bytes content to the instrument.

Return type:

`None`

## Temptronic ATS525 Thermostream

### Temptronic ATS525 Thermostream

 *class *pymeasure.instruments.temptronic.ATS525(*adapter*, *name='Temptronic ATS-525 Thermostream'*, ***kwargs*)

Bases: [`ATSBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_base.html#pymeasure.instruments.temptronic.ATSBase)

Represent the TemptronicATS525 instruments.

 *property *system_current*: Any*

Get operating current.

## Temptronic ECO560 Thermostream

### Temptronic ECO560 Thermostream

 *class *pymeasure.instruments.temptronic.ECO560(*adapter*, *name='Temptronic ECO-560 Thermostream'*, ***kwargs*)

Bases: [`ATSBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_base.html#pymeasure.instruments.temptronic.ATSBase)

Represent the TemptronicECO560 instruments.

## Temptronic

### Temptronic

Implemented temptronic instrument documentation is grouped here. For another model, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Temptronic Base Class](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_base.html)
  - [`ATSBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_base.html#pymeasure.instruments.temptronic.ATSBase)
  - [`TemperatureStatusCode`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_base.html#pymeasure.instruments.temptronic.temptronic_base.TemperatureStatusCode)
  - [`ErrorCode`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_base.html#pymeasure.instruments.temptronic.temptronic_base.ErrorCode)

- [Temptronic ATS525 Thermostream](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_ats525.html)
  - [`ATS525`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_ats525.html#pymeasure.instruments.temptronic.ATS525)

- [Temptronic ATS545 Thermostream](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_ats545.html)
  - [`ATS545`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_ats545.html#pymeasure.instruments.temptronic.ATS545)

- [Temptronic ECO560 Thermostream](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_eco560.html)
  - [`ECO560`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_eco560.html#pymeasure.instruments.temptronic.ECO560)

## Temptronic ATS545 Thermostream

### Temptronic ATS545 Thermostream

 *class *pymeasure.instruments.temptronic.ATS545(*adapter*, *name='Temptronic ATS-545 Thermostream'*, ***kwargs*)

Bases: [`ATSBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_base.html#pymeasure.instruments.temptronic.ATSBase)

Represents the TemptronicATS545 instrument.

Coding example

```python
ts = ATS545('ASRL3::INSTR')  # replace adapter address
ts.configure()  # basic configuration (defaults to T-DUT)
ts.start()  # starts flow (head position not changed)
ts.set_temperature(25)  # sets temperature to 25 degC
ts.wait_for_settling()  # blocks script execution and polls for settling
ts.shutdown(head=False)  # disables thermostream, keeps head down

```

 next_setpoint()

not implemented in ATS545

set `self.set_point_number` instead

## Temptronic Base Class

### Temptronic Base Class

 *class *pymeasure.instruments.temptronic.ATSBase(*adapter*, *name='ATSBase'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Base implementation for Temptronic ATSXXX instruments.

 *property *air_temperature*: Any*

Return air temperature using 0.1 ?C increments.

Type:

float

 at_temperature()

Returns:

`True` if at temperature.

 *property *auxiliary_condition_code*: Any*

Get out auxiliary condition status register.

Type:

int

Relevant flags are:

| Bit | Meaning |
| --- | --- |
| 10 | None |
| 9 | Ramp mode |
| 8 | Mode: 0 programming, 1 manual |
| 7 | None |
| 6 | TS status: 0 start-up, 1 ready |
| 5 | Flow: 0 off, 1 on |
| 4 | Sense mode: 0 air, 1 DUT |
| 3 | Compressor: 0 on, 1 off (heating possible) |
| 2 | Head: 0 lower, upper |
| 1 | None |
| 0 | None |

Consult chapter 4 in the manual

 clear()

Clear device-specific errors.

Additional details are in `error_code`.

 *property *compressor_enable*: Any*

Set compressor operation: `True` enables compressors, while `False` disables it.

Type:

Boolean

 configure(*temp_window=1*, *dut_type='T'*, *soak_time=30*, *dut_constant=100*, *temp_limit_air_low=-60*, *temp_limit_air_high=220*, *temp_limit_air_dut=50*, *maximum_test_time=1000*)

Helper for the key configuration properties.

Parameters:

-

**dut_type** ? string: selects which DUT type to use (default: `'T'`)

-

**soak_time** ? float: elapsed time in soak_window before settling is reported (default: `30`)

-

**soak_window** ? float: Soak window size, also used as the temperature settling bounds (K)

-

**dut_constant** ? float: DUT time constant; higher values indicate higher thermal mass (default: `100`)

-

**temp_limit_air_low** – float: minimum flow temperature limit (°C) (default: `-60`)

-

**temp_limit_air_high** – float: maximum flow temperature limit (°C) (default: `220`)

-

**temp_limit_air_dut** ? float: maximum allowed DUT-to-Flow temperature difference (K) (default: `50`)

-

**maximum_test_time** ? float: maximum test time (seconds) for one temperature point, used as safety limit (default: `1000`)

Returns:

self

 *property *copy_active_setup_file*: Any*

Choose active setup file (0) as the source copied into setup n (1 - 12).

Type:

int

 *property *current_cycle_count*: Any*

Return how many cycles are to be run

Type:

int

 *property *cycling_enable*: Any*

Control whether cycling is enabled.

Type:

bool

cycling_enable = True (start cycling) cycling_enable = False (stop cycling)

 cycling_stopped()

Returns:

`True` if cycling has stopped.

 *property *dut_constant*: Any*

Set the DUT thermal constant (default 100).

Type:

float

Lower values indicate lower thermal mass, higher values indicate higher thermal mass respectively.

 *property *dut_mode*: Any*

Set DUT mode to ?On? or ?OFF?

Type:

string

 *property *dut_temperature*: Any*

Return DUT temperature in 0.1 ?C increments.

Type:

float

 *property *dut_type*: Any*

Control DUT sensor type.

Type:

string

Possible values are:

| String | Meaning |
| --- | --- |
| ‘’ | no DUT |
| ‘T’ | T-DUT |
| ‘K’ | K-DUT |

Warning: Running in DUT mode without a connected DUT makes TS flag a DUT error

 *property *dynamic_temperature_setpoint*: Any*

Get the dynamic temperature setpoint.

Type:

float

 *property *enable_air_flow*: Any*

Set TS air flow.

`True` starts air flow, and `False` stops it

Type:

bool

 end_of_all_cycles()

Returns:

`True` if cycling has stopped.

 end_of_one_cycle()

Returns:

`True` means TS has reached the end of one cycle.

 end_of_test()

Returns:

`True` means TS has reached the end of test.

 enter_cycle()

Enter Cycle by sending `RMPC 1`.

Returns:

self

 enter_ramp()

Enter Ramp by sending `RMPS 0`.

Returns:

self

 *property *error_code*: Any*

Return the device-specific error register, which is 16 bits.

Type:

`ErrorCode`

 error_status()

Return an error status code, for example for logging.

Returns:

`ErrorCode`

 *property *head*: Any*

Control TS head position.

Type:

string

`down`: move transfer head to lower position `up`: move transfer head to elevated position

 *property *learn_mode*: Any*

Control DUT automatic tuning (learning).

Type:

bool `False`: off `True`: automatic tuning enabled

 *property *load_setup_file*: Any*

Select a setup file and load it.

Valid range is between 1 to 12.

Type:

int

 *property *local_lockout*: Any*

Set local lock behavior: `True` disables TS GUI, and `False` enables it.

 *property *main_air_flow_rate*: Any*

Return the main nozzle air flow rate in liters/sec.

 *property *maximum_test_time*: Any*

Control maximum allowed test time (s).

Type:

float

This keeps TS from remaining at one temperature indefinitely. Valid range: 0 to 9999

 *property *mode*: Any*

Return a string describing the system activity when the query is handled.

Type:

string

(dynamic)

 next_setpoint()

Advance to the next setpoint while temperature cycling is active.

 not_at_temperature()

Returns:

`True` if not at temperature.

 *property *nozzle_air_flow_rate*: Any*

Return main nozzle air flow rate in scfm.

 *property *ramp_rate*: Any*

Control ramp rate (K / min).

Type:

float

allowed values: nn.n means 0 to 99.9 in 0.1 K per minute steps; nnnn means 100 to 9999 in 1 K per minute steps.

 *property *remote_mode*: Any*

Set whether remote mode is active.

 reset()

Force the System back to the Operator screen.

Returns:

self

 *property *set_point_number*: Any*

Set the setpoint index that becomes the current setpoint.

Type:

int

Valid range is 0 to 17 on the Cycle screen, or 0 to 2 on the operator screen (0=hot, 1=ambient, 2=cold).

 set_temperature(*set_temp*)

sweep to a specified setpoint.

Parameters:

**set_temp** ? target DUT temperature (float)

Returns:

self

 shutdown(*head=False*)

Shut down TS by disabling flow and remote operation.

Parameters:

**head** ? Lift head when `True` (default: `False`)

Returns:

self

 start(*enable_air_flow=True*)

start TS in remote mode.

Parameters:

**enable_air_flow** ? flow begins when `True` (default: `True`)

Returns:

self

 *property *temperature*: Any*

Return current temperature at 0.1 ?C resolution.

Type:

float

Temperature reading source is determined by `dut_mode`; values higher than 400 (?C) indicate invalidity.

 *property *temperature_condition_status_code*: Any*

Get temperature condition status register.

Type:

`TemperatureStatusCode`

 *property *temperature_event_status*: Any*

Get temperature event status register.

Type:

`TemperatureStatusCode`

Hint: Reading this clears the register content.

 *property *temperature_limit_air_dut*: Any*

Return the air to DUT temperature limit.

Type:

float

Allowed nozzle-air-to-DUT temperature difference while settling. Accept values from 10 to 300 ?C, stepping by 1 degree.

 *property *temperature_limit_air_high*: Any*

Control upper air temperature limit.

Type:

float

Valid range between 25 to 255 (?C). Setpoints above the current value trigger an ?out of range? error in TS.

 *property *temperature_limit_air_low*: Any*

Control lower air temperature limit.

Type:

float

Valid range between -99 to 25 (?C). Setpoints below the current value trigger an ?out of range? error in TS. (dynamic)

 *property *temperature_setpoint*: Any*

Control selected setpoint’s temperature.

Type:

float

Valid range is -99.9 to 225.0 (?C), or the range specified by `temperature_limit_air_high` and `temperature_limit_air_low`. Use convenience function `set_temperature()` to avoid unexpected behavior.

 *property *temperature_setpoint_window*: Any*

Control setpoint’s temperature window.

Type:

float

Valid range is between 0.1 to 9.9 (?C). The temperature status register flags `at temperature` once soak time has elapsed while temperature remains within this value?s bounds around the current setpoint.

 *property *temperature_soak_time*: Any*

Set the soak time for the currently selected setpoint.

Type:

float

Valid range is between 0 to 9999 (s). Lower values reduce cycle times; higher values lengthen cycles but can reduce settling errors. See `temperature_setpoint_window` for details.

 *property *total_cycle_count*: Any*

Control current cycle count (1 - 9999).

Type:

int

Sending 0 will stop cycling

 wait_for(*query_delay=None*)

Pause for a short interval; ?ask? uses it before reading.

Parameters:

**query_delay** ? Wait time between writing and reading in seconds. None uses the default delay. (default: `None`)

 wait_for_settling(*time_limit=300*)

block script execution until TS reports settled.

Parameters:

**time_limit** ? maximum blocking time allowed for TS to settle (float). (default: `300`)

Returns:

self

Script execution remains blocked until TS settles or time_limit is exceeded (float).

 *class *pymeasure.instruments.temptronic.temptronic_base.TemperatureStatusCode(**values*)

Temperature status enums derived from `IntFlag`

Used together with `temperature_condition_status_code`.

>
| Value | Enum |
| --- | --- |
| 32 | CYCLING_STOPPED |
| 16 | END_OF_ALL_CYCLES |
| 8 | END_OF_ONE_CYCLE |
| 4 | END_OF_TEST |
| 2 | NOT_AT_TEMPERATURE |
| 1 | AT_TEMPERATURE |
| 0 | NO_STATUS |

 *class *pymeasure.instruments.temptronic.temptronic_base.ErrorCode(**values*)

Error code enums derived from `IntFlag`.

Used together with `error_code`.

>
| Value | Enum |
| --- | --- |
| 16384 | NO_DUT_SENSOR_SELECTED |
| 4096 | BVRAM_FAULT |
| 2048 | NVRAM_FAULT |
| 1024 | NO_LINE_SENSE |
| 512 | FLOW_SENSOR_HARDWARE_ERROR |
| 128 | INTERNAL_ERROR |
| 32 | AIR_SENSOR_OPEN |
| 16 | LOW_INPUT_AIR_PRESSURE |
| 8 | LOW_FLOW |
| 2 | AIR_OPEN_LOOP |
| 1 | OVERHEAT |
| 0 | OK |

## KEPCO INC.

### KEPCO INC.

Implemented Kepco Inc. power supply instrument documentation is grouped here. For another model, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [BOP Bipolar Power Supply with BIT 4886 Digital Interface Card](https://pymeasure.readthedocs.io/en/latest/api/instruments/kepco/KepcoBOP.html): API reference page
  - [`KepcoBOP3612`](https://pymeasure.readthedocs.io/en/latest/api/instruments/kepco/KepcoBOP.html#pymeasure.instruments.kepco.KepcoBOP3612)

## BOP Bipolar Power Supply with BIT 4886 Digital Interface Card

### BOP Bipolar Power Supply with BIT 4886 Digital Interface Card

 *class *pymeasure.instruments.kepco.KepcoBOP3612(*adapter*, *name='Kepco BOP 36-12 Bipolar Power Supply'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a minimal high-level interface for a Kepco BOP 36-12 (M or D) 400 W bipolar power supply using a BIT 4886 digital interface card.

 beep()

Make the unit produce a short audible tone.

 *property *bop_test*: Any*

Return the error code from a full power supply self-test.

Returns 0 when every test passes; otherwise returns the manual?s matching error code. Caution: disconnect any load before testing, because Output will switch on and swing to maximum values.

 *property *confidence_test*: Any*

Return the error code from the interface self-test procedure.

Returns 0 when every test passes; otherwise returns the manual?s matching error code.

 *property *current*: Any*

Measure output-terminal current in Amps.

 *property *current_setpoint*: Any*

Control the output current setpoint.

Behavior changes with operating mode. In current mode, this programs the output current setpoint; achieved current is constrained by voltage compliance and load conditions (see: current). In voltage mode, it programs the compliance current for the related voltage set point. Queries return the programmed value, whose meaning depends on the power supply operating context (see: operating_mode).

The output still has to be enabled separately (see: output_enabled)

 *property *operating_mode*: Any*

Set or query the BOP operating mode.

For commands, send the string VOLT or CURR. Queries return 0 or 1, corresponding respectively to VOLT or CURR; the driver maps that value back to the matching string.

 *property *output_enabled*: Any*

Enable or disable the source, accepting True or False (bool)

 *property *voltage*: Any*

Measure the voltage across the output terminals in Volts.

 *property *voltage_setpoint*: Any*

Control the output voltage setpoint.

Behavior changes with operating mode. In voltage mode, this programs the output voltage setpoint; achieved voltage is constrained by current compliance and load conditions (see: voltage). In current mode, it programs the compliance voltage for the related current set point. Queries return the programmed value, whose meaning depends on the power supply operating context (see: operating_mode).

The output still has to be enabled separately (see: output_enabled)

 wait_to_continue()

Make the power supply wait until all earlier commands and queries finish before later commands or queries run.

## Edwards

### Edwards

Implemented Edwards instrument documentation is grouped here. For another model, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Edwards nxds vacuum pump](https://pymeasure.readthedocs.io/en/latest/api/instruments/edwards/nxds.html)
  - [`Nxds`](https://pymeasure.readthedocs.io/en/latest/api/instruments/edwards/nxds.html#pymeasure.instruments.edwards.Nxds)

## Edwards nxds vacuum pump

### Edwards nxds vacuum pump

 *class *pymeasure.instruments.edwards.Nxds(*adapter*, *name='Edwards NXDS Vacuum Pump'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents the Edwards nXDS (10i) Vacuum Pump and exposes low-level instrument interaction. It may also work with an Edwards pump that has a RS232 interface. This driver is built only to start and stop pump.

 *property *enable*: Any*

Apply the default settings while setting the pump enabled state.
