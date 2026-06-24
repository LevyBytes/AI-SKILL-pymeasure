# Thermotron, Deltaelektronica, Ptw, Anapico ...

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Thermotron 3800 Oven; Thermotron; Delta Elektronica SM7045D Power source; Delta Elektronika; PTW Freiburg; PTW UNIDOS Tango/Romeo dosemeters; PTW DIAMENTOR DAP dosemeters; Anapico; Anapico APSIN12G Signal Generator; FormFactor; FormFactor Velox Wafer Prober.

## Thermotron 3800 Oven

### Thermotron 3800 Oven

 *class *pymeasure.instruments.thermotron.Thermotron3800(*adapter*, *name='Thermotron 3800'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Thermotron 3800 Oven. This driver currently addresses only Control Channel 1, and each write command is followed by a built-in 1000ms delay.

 *class *Thermotron3800Mode(**values*)

Bases: `IntFlag`

| Bit | Mode |
| --- | --- |
| 0 | Program mode |
| 1 | Edit mode with the controller in stop mode. |
| 2 | View program mode |
| 3 | Edit mode with the controller in hold mode. |
| 4 | Manual mode |
| 5 | Delayed start mode |
| 6 | Unused |
| 7 | Calibration mode |

 *property *id*: Any*

Get the instrument identification

Returns:

String

 initalize_oven(*wait=True*)

Initialize the oven. :rtype: `None`

Deprecated since version 0.17.0: Use `initialize_oven()` instead.

 initialize_oven(*wait=True*)

Initialize the oven, with an optional delay before continuing.

After oven initialization, the manufacturer advises waiting 3 seconds. Keep the optional `wait` variable true unless user code already provides that 3 second pause. Timing is divided as 1 second in the write function plus 2 seconds from this initialize_oven wait option.

Returns:

`None` – None

 *property *mode*: Any*

Return the oven operating mode.

Returns:

Tuple(String, int)

 run()

Begin temperature forcing so the oven ramps toward the setpoint.

Returns:

None

 *property *setpoint*: Any*

Set the oven setpoint in Celsius. The float `setpoint` value is not applied until `run()` is invoked; after changing it, call `run()` so the oven moves to the requested temperature.

Returns:

None

 stop()

End temperature forcing for the oven.

Returns:

None

 *property *temperature*: Any*

Read the current oven temperature from the built-in thermocouple. Unless the user changes it, the unit is Celsius.

Returns:

float

 write(*command*)

Send a string command to the instrument with write_termination appended.

Parameters:

-

**command** - command string transmitted to the instrument

-

**kwargs** - Keyword arguments passed to the adapter.

## Thermotron

### Thermotron

This section documents the implemented Thermotron instruments. For unsupported models, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Thermotron 3800 Oven](https://pymeasure.readthedocs.io/en/latest/api/instruments/thermotron/thermotron3800.html)
  - [`Thermotron3800`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thermotron/thermotron3800.html#pymeasure.instruments.thermotron.Thermotron3800)

## Delta Elektronica SM7045D Power source

### Delta Elektronica SM7045D Power source

 *class *pymeasure.instruments.deltaelektronika.SM7045D(*adapter*, *name='Delta Elektronika SM 70-45 D'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the SM 70-45 D power supply.

```python
source = SM7045D("GPIB::8")

source.ramp_to_zero(1)               # Set output to 0 before enabling
source.enable()                      # Enables the output
source.current = 1                   # Sets a current of 1 Amps

```

 *property *current*: Any*

Settable floating-point property for the power supply output current in Amps.

 disable()

Enable remote shutdown, which disables the input.

 enable()

Turn off remote shutdown, enabling the output.

 *property *max_current*: Any*

Settable floating-point property for the power supply maximum output current in Amps.

 *property *max_voltage*: Any*

Settable floating-point property for the power supply maximum output voltage in Volts.

 *property *measure_current*: Any*

Measure the power supply actual output current in Amps.

 *property *measure_voltage*: Any*

Measure the power supply actual output voltage in Volts.

 ramp_to_current(*target_current*, *current_step=0.1*)

Ramp current upward or downward until it reaches the target current.

Parameters:

-

**target_current** - Float defining the target current (in A)

-

**current_step** - Optional float defining the current step size / ramp rate (in A/s) (default: `0.1`)

 ramp_to_zero(*current_step=0.1*)

Ramp the current down to zero.

Parameters:

**current_step** - Optional float defining the current step size / ramp rate (in A/s) (default: `0.1`)

 *property *rsd*: Any*

Report whether remote shutdown is enabled or disabled, indicating whether the power supply output is disabled or enabled.

 shutdown()

Set current to 0 A and switch off the power source output.

 *property *voltage*: Any*

Settable floating-point property for the power supply output voltage setting in Volts.

## Delta Elektronika

### Delta Elektronika

This section documents the implemented Delta Elektronika instruments. For unsupported models, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Delta Elektronica SM7045D Power source](https://pymeasure.readthedocs.io/en/latest/api/instruments/deltaelektronica/sm7045d.html)
  - [`SM7045D`](https://pymeasure.readthedocs.io/en/latest/api/instruments/deltaelektronica/sm7045d.html#pymeasure.instruments.deltaelektronika.SM7045D)

## PTW Freiburg

### PTW Freiburg

This section documents the implemented PTW Freiburg GmbH instruments. For unsupported models, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [PTW DIAMENTOR DAP dosemeters](https://pymeasure.readthedocs.io/en/latest/api/instruments/ptw/ptwDIAMENTOR.html)
  - [`ptwDIAMENTOR`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ptw/ptwDIAMENTOR.html#pymeasure.instruments.ptw.ptwDIAMENTOR)

- [PTW UNIDOS Tango/Romeo dosemeters](https://pymeasure.readthedocs.io/en/latest/api/instruments/ptw/ptwUNIDOS.html)
  - [`ptwUNIDOS`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ptw/ptwUNIDOS.html#pymeasure.instruments.ptw.ptwUNIDOS)

## PTW UNIDOS Tango/Romeo dosemeters

### PTW UNIDOS Tango/Romeo dosemeters

 *class *pymeasure.instruments.ptw.ptwUNIDOS(*adapter*, *name='PTW UNIDOS dosemeter'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for PTW UNIDOS Tango/Romeo dosemeters.

 *property *autoreset_enabled*: Any*

Set the measurement autoreset behavior (bool).

 *property *autostart_enabled*: Any*

Set the measurement autostart behavior (bool).

 *property *autostart_level*: Any*

Set the autostart measurement threshold level (str, strictly `LOW`, `MEDIUM` or `HIGH`).

 check_set_errors()

After a command is sent, check for errors.

Return type:

`list`[`str`]

 clear()

Erase the full measurement history. :rtype: `None`

Note

Write permission is required.

 *property *electrical_units_enabled*: Any*

Set whether electrical units are active (bool).

 errorflags_to_text(*flags*)

Translate error flags into error message(s).

Parameters:

**flags** (*str*)

Return type:

`list`[`str`]

 hold()

Place the measurment in HOLD state. :rtype: `None`

Note

Write permission is required.

 *property *id*: Any*

Return the dosemeter ID (list[str]).

 *property *integration_time*: Any*

Set interval measurement time in seconds (int, strictly from `1` to `3599999`).

 interval_measurement(*interval=None*)

Execute an interval measurement.

Parameters:

**interval** (`Optional`[`int`]) - optional measurement interval in seconds (default: `None`)

Return type:

`None`

When *interval* is omitted, measurement runs using the current `integration_time` setting.

Note

Write permission is required.

 intervall(*intervall=None*)

Run an interval measurement. :rtype: `None`

Deprecated since version 0.16.0: Use `interval_measurement()` instead.

 *property *lan_config*: Any*

Get the ethernet configuration (dict).

Dict keys:

`dns`, `ipv4`, `ipv6`

 *property *mac_address*: Any*

Return the dosemeter MAC address (str).

 measure()

Begin the dose or charge measurement. :rtype: `None`

Note

Write permission is required.

 *property *measurement_history*: Any*

Return measurement history (list[dict]).

Dict keys:

`date`, `detector`, `dose`, `flags`, `id`, `kTotal`

 *property *measurement_parameters*: Any*

Get the measurement parameters (dict).

Dict keys:

`correction`, `detectorGuid`, `highResolution`, `hv`, `integrationTime`, `isElectrical`, `limitDose`, `limitDoseEnabled`, `limitDoseRate`, `limitDoseRateEnabled`, `range`, `triggerAuto`, `triggerReset`, `triggerSensitivity`

 *property *measurement_result*: Any*

Get the measurement results (dict).

Dict keys:

`status`, `charge`, `dose`, `current`, `doserate`, `timebase`, `time`, `voltage`, `error`

 *property *range*: Any*

Set measurement range (str, strictly `VERY_LOW`, `LOW`, `MEDIUM` or `HIGH`).

 *property *range_max*: Any*

Return the maximum value for the active measurement range (dict).

Dict keys:

`range`, `current`, `doserate`, `timebase`

 *property *range_res*: Any*

Return the measurement range resolution (dict).

Dict keys:

`range`, `charge`, `dose`, `current`, `doserate`, `timebase`

 read()

Read the device response, then validate it for errors.

Returns:

`str` - String read with semicolons converted to comma

Raises:

*ValueError* on an error response, or *ConnectionError* when the error is unknown

 read_detector(*guid='ALL'*)

Read properties for the requested detector.

Parameters:

**guid** (*str*) - optional detector ID. If *guid* is not provided, returns every detector.

Type:

dict or list[dict]

Dict keys:

`calibrationFactor`, `calibrationFactorUnit`, `calibrationLab`, `calibrationProcedure`, `calibrationTemp`, `calibrationType`, `calibrationUser`, `comment`, `guid`, `manufacturer`, `maxHv`, `measuredQuantity`, `minHv`, `name`, `nominalHv`, `polarity`, `radiationQuality`, `range`, `serialNumber`, `testDate`, `testLimits`, `testResult`, `testTarget`, `timebase`, `type`, `typeNumber`

Return type:

`Union`[`dict`, `list`[`dict`]]

 reset()

Reset the dose and charge measurement values. :rtype: `None`

Note

Write permission is required.

 selftest()

Execute the electrometer selftest.

The function exits before selftest completion. Request both completion and result through the `selftest_result` property. :rtype: `None`

Note

Write permission is required.

 *property *selftest_result*: Any*

Return the dosemeter selftest status and result (dict).

Dict keys:

`status`, `time_remaining`, `time_total`, `low`, `medium`, `high`

 *property *serial_number*: Any*

Return the dosemeter serial number (int).

 *property *status*: Any*

Get the measurement status (str).

The status string must match one listed value: `RES`; `MEAS`; `HOLD`; `INT`; `INTHLD`; `ZERO`; `AUTO`; `AUTO_MEAS`; `AUTO_HOLD`; `EOM`; `WAIT`; `INIT`; `ERROR`; `SELF_TEST`; or `TST`

 *property *system_info*: Any*

Get the system information (dict).

Dict keys:

`calibrationDate`, `debugBuild`, `features`, `hardwareVersion`, `hostname`, `lastTest`, `macAddress`, `nextCalibration`, `serialNumber`, `softwareVersion`, `testTemperature`, `typeNumber`

 *property *system_settings*: Any*

Get the system settings (dict).

Dict keys:

`brightness`, `date`, `keyboardSound`, `locale`, `mark`, `startAsMaster`, `time`, `timezone`, `volume`

 *property *tfi*: Any*

Return telegram failure information (str).

This property reports the most recent failed command involving an HTTP request.

 *property *voltage*: Any*

Set detector voltage in Volts (int, strictly from `-400` to `400`)

The detector limits are enforced.

 *property *wlan_config*: Any*

Return the WLAN access point configuration (dict).

Dict keys:

`enabled`, `ssid`

 *property *write_enabled*: Any*

Control the write permission (bool).

Afterwards, check the request/release result.

Important

UNIDOS must be in viewer mode, shown by the closed lock symbol on the display.

 zero()

Execute a zero correction measurement.

The function exits before the zero correction measurement finishes. Request completion through the `zero_status` property. :rtype: `None`

Note

Write permission is required.

 *property *zero_status*: Any*

Return zero correction measurement status (dict).

Dict keys:

`status`, `time_remaining`, `time_total`

## PTW DIAMENTOR DAP dosemeters

### PTW DIAMENTOR DAP dosemeters

 *class *pymeasure.instruments.ptw.ptwDIAMENTOR(*adapter*, *name='PTW DIAMENTOR DAP dosemeter'*, *baud_rate=9600*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for PTW DIAMENTOR DAP dosemeters.

 *property *baudrate*: Any*

Set the baudrate (int, strictly `9600`, `19200`, `38400`, `57600` or `115200`).

The baudrate changes after the response is sent.

 *property *calibration_factor*: Any*

Set the measurement chamber calibration factor in ÂµGy*mÂ²/s (float, strictly from `1E8` to `9.999E12`, default: `1.0E9`).

The calibration factor unit is always ÂµGy*mÂ²/s and does not depend on the selected `dap_unit`.

Warning

Changing the calibration factor can produce incorrect measurements!

Find the last calibration factor on the case label or in the DIAMENTOR chamber calibration certificate.

 check_set_errors()

After a command is sent, check for errors.

Return type:

`list`[`str`]

 *property *constancy_check_passed*: Any*

Return the DIAMENTOR electrical constancy check result (bool).

 *property *correction_factor*: Any*

Set the chamber correction factor (float, strictly from `0` to `9.999`, default: `1.0`).

 *property *dap_unit*: Any*

Set the dose-area-product (DAP) unit (str, strictly `cGycm2`, `Gycm2`, `uGym2` or `Rcm2`).

-

`cGycm2` selects cGy*cm²

-

`Gycm2` selects Gy*cm²

-

`uGym2` selects µGy*m²

-

`Rcm2` selects R*cm²

 execute_selftest()

Execute the DIAMENTOR selftest.

Raises:

*ValueError* if selftest fails

Return type:

`None`

 *property *id*: Any*

Get the firmware version (str).

Example response: `CRS 2.33`

 *property *is_calibrated*: Any*

Get the calibration status (bool).

 *property *is_eeprom_ok*: Any*

Return EEPROM CRC ok status (bool).

 *property *measurement*: Any*

Get the measurement result (dict).

Dict keys:

`dap`, `dap_rate`, `time`

The result includes the dose-area-product (DAP) and dose-area-product rate. Units for `dap` and `dap_rate` are determined by the `dap_unit` property. Time is reported in seconds.

 *property *pressure*: Any*

Set atmospheric pressure in hPa (int, strictly from `500` to `1500`, default: `1013`).

This value is used for air density correction.

 read()

Read the device response, then validate it for errors.

Raises:

*ValueError* on an error response, or *ConnectionError* when the error is unknown

Return type:

`str`

 reset()

Reset the dose and charge measurement values.

Return type:

`None`

 *property *serial_number*: Any*

Get the serial number (int).

 *property *temperature*: Any*

Set the chamber temperature, expressed in degree Celsius (int, strictly from `0` to `70`, default: `20`).

This value is used for air density correction.

## Anapico

### Anapico

This section documents the implemented Anapico instruments. For unsupported models, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Anapico APSIN12G Signal Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/anapico/apsin12G.html)
  - [`APSIN12G`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anapico/apsin12G.html#pymeasure.instruments.anapico.APSIN12G)

## Anapico APSIN12G Signal Generator

### Anapico APSIN12G Signal Generator

 *class *pymeasure.instruments.anapico.APSIN12G(*adapter*, *name='Anapico APSIN12G Signal Generator'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Anapico APSIN12G Signal Generator with option 9K, HP and GPIB.

 *property *blanking*: Any*

Set output-power blanking during frequency changes. ON blanks the output, turning it off while the frequency changes.

 disable_rf()

Disables the RF output.

 enable_rf()

Enables the RF output.

 *property *frequency*: Any*

Set output frequency in Hz. (float)

 *property *power*: Any*

Set output power in dBm. (float)

 *property *reference_output*: Any*

Set the synth 10MHz reference output. (str)

## FormFactor

### FormFactor

This section documents the implemented FormFactor devices. For unsupported models, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [FormFactor Velox Wafer Prober](https://pymeasure.readthedocs.io/en/latest/api/instruments/formfactor/velox.html)
  - [`Velox`](https://pymeasure.readthedocs.io/en/latest/api/instruments/formfactor/velox.html#pymeasure.instruments.formfactor.Velox)
  - [`Chuck`](https://pymeasure.readthedocs.io/en/latest/api/instruments/formfactor/velox.html#pymeasure.instruments.formfactor.velox.Chuck)
  - [`WaferMap`](https://pymeasure.readthedocs.io/en/latest/api/instruments/formfactor/velox.html#pymeasure.instruments.formfactor.velox.WaferMap)

## FormFactor Velox Wafer Prober

### FormFactor Velox Wafer Prober

 *class *pymeasure.instruments.formfactor.Velox(*adapter*, *name='FormFactor Velox'*, *timeout=40000*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the FormFactor Velox wafer prober.

Example showing a full-wafer measurement:

```python
from pymeasure.instruments.formfactor.velox import Velox

prober = Velox("GPIB0::28::INSTR")  # replace the resource to your needs
coordinates = prober.wafermap.step_first_die()  # move to the first die in the wafermap
while not self.wafermap.end_reached:
    prober.chuck.move_contact()  # move to contact height
    # ...
    # code for measurement, processing and storing data
    # ...
    prober.chuck.move_separation()  # move to separation height
    coordinates = prober.wafermap.step_next_die()  # move to the next die in the wafermap

```

 chuck

Channel:

`Chuck`

 wafermap

Channel:

`WaferMap`

 check_errors()

Invoke `read()`.

 *property *options

Return installed options. Raises *NotImplementedError* because command `*OPT?` is not implemented in Velox.

 read()

Read the response and validate it for errors.

Raise:

*ConnectionError* when an error is detected.

 *property *version*: Any*

Return the Velox main software version (str).

 *class *pymeasure.instruments.formfactor.velox.Chuck(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for wafer prober Chuck functions.

 *property *index*: Any*

Set the chuck index (x, y) in micrometer (float, float).

 move(*x*, *y*, *pos_ref='home'*, *unit='microns'*, *velocity=100*)

Move the chuck by the requested distance.

Parameters:

-

**x** (*float*) - Distance in X direction

-

**y** (*float*) - Distance in Y direction

-

**pos_ref** (*str*) - Position reference, strictly `home`, `zero`, `center` or `diehome`.

-

**unit** (*str*) - Unit for **x** and **y**, strictly `micron`, `mils`, `jogs`, `encoder` or `index`.

-

**velocity** (*float*) - Speed in percent, strictly from `0.1` to `100`.

 move_align(*velocity=100*)

Move the chuck to align height.

Parameters:

**velocity** (*float*) - Speed in percent, strictly from `0.1` to `100`.

 move_contact(*velocity=100*)

Move the chuck to contact height.

Parameters:

**velocity** (*float*) - Speed in percent, strictly from `0.1` to `100`.

 move_index(*x_steps*, *y_steps*, *pos_ref='home'*, *velocity=100*)

Move the chuck by index steps.

Parameters:

-

**x_steps** (*int*) - Index steps in X direction

-

**y_steps** (*int*) - Index steps in Y direction

-

**pos_ref** (*str*) - Position reference, strictly `home`, `zero`, `center` or `diehome`.

-

**velocity** (*float*) - Speed in percent, strictly from `0.1` to `100`.

 move_separation(*velocity=100*)

Move the chuck to separation height.

Parameters:

**velocity** (*float*) - Speed in percent, strictly from `0.1` to `100`.

 *class *pymeasure.instruments.formfactor.velox.WaferMap(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for Wafermap module functions.

 *property *enabled*: Any*

Return whether the WaferMap module is loaded (bool).

 end_reached* = False*

Return whether the wafermap end has been reached (bool).

 step_first_die()

Move the chuck to the first die and clear the binning results.

Returns:

List of int values containing the first die coordinates.

-

item[0]: X coordinate

-

item[1]: Y coordinate

-

item[2]: Current subdie index

-

item[3]: Total subdie count for the die

 step_next_die()

Move the chuck to the next logical die.

Returns:

List of int values containing the new die coordinates.

-

item[0]: X coordinate

-

item[1]: Y coordinate

-

item[2]: Current subdie index

-

item[3]: Total subdie count for the die

 step_to_die(*x_pos*, *y_pos*, *s_pos=None*)

Move the chuck to the specified die coordinates.

Parameters:

-

**x_pos** (*int*) – X coordinate.

-

**y_pos** (*int*) – Y coordinate.

-

**s_pos** (*int*) – subdie index.
