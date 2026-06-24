# Hp11713A, Hp437B, Hplegacyinstrument, Hp3437A

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Scope includes the HP 11713A Attenuator/Switch Driver, the HP 437B Power Meter, a Support class for HP legacy devices, and the HP 3437A System-Voltmeter.

## HP 11713A Attenuator/Switch Driver

### HP 11713A Attenuator/Switch Driver

 *class *pymeasure.instruments.hp.HP11713A(*adapter*, *name='Hewlett-Packard HP11713A'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the HP 11713A Switch and Attenuator Driver and exposes a high-level interface for instrument control.

An attenuator is typically connected to X, Y, or both X and Y. For simpler attenuator-driver control, choose an attenuator type with the `ATTENUATOR_X` or `ATTENUATOR_Y` attribute. hp11713a includes separate default attenuator mappings. Once the attenuator type is selected, the `attenuation_x` and/or `attenuation_y` methods can set the switch driver to the value matching the requested attenuation. Attenuation inputs are rounded.

```python
from pymeasure.instruments.hp import HP11713A
from pymeasure.instruments.hp.hp11713a import Attenuator_110dB

sd = HP11713A("GPIB::1")

sd.ATTENUATOR_Y = Attenuator_110dB
sd.attenuation_y(10)
sd.ch_0.enabled = True

```

 channels

Channels:

`ch_0`: `SwitchDriverChannel`, `ch_1`: `SwitchDriverChannel`, `ch_2`: `SwitchDriverChannel`, `ch_3`: `SwitchDriverChannel`, `ch_4`: `SwitchDriverChannel`, `ch_5`: `SwitchDriverChannel`, `ch_6`: `SwitchDriverChannel`, `ch_7`: `SwitchDriverChannel`, `ch_8`: `SwitchDriverChannel`

 attenuation_x(*attenuation*)

Configure the X switches for the requested attenuation in dB

Requested attenuation is rounded to the next available step. Set an attenuation mapping first, e.g.

```python
from pymeasure.instruments.hp.hp11713a import HP11713A, Attenuator_110dB

instr.ATTENUATOR_X = Attenuator_110dB
instr.attenuation_x(10)

```

 attenuation_y(*attenuation*)

Configure the Y switches for the requested attenuation in dB

Requested attenuation is rounded to the next available step. Set an attenuation mapping first, e.g.

```python
from pymeasure.instruments.hp.hp11713a import HP11713A, Attenuator_110dB

instr.ATTENUATOR_Y = Attenuator_110dB
instr.attenuation_y(10)

```

 deactivate_all()

Set every switch inactive at polarity `B`.

 *class *pymeasure.instruments.hp.hp11713a.SwitchDriverChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

 *property *enabled*: Any*

For this channel, True selects polarity `A`; False selects polarity `B`.

 pymeasure.instruments.hp.hp11713a.Attenuator_11dB

Logical-value mapping for 0 - 11 dB attenuators

 pymeasure.instruments.hp.hp11713a.Attenuator_110dB

Logical-value mapping for 0 - 110 dB attenuators

 pymeasure.instruments.hp.hp11713a.Attenuator_70dB_3_Section

Logical-value mapping for 0 - 70 dB attenuators using 3 switching sections

 pymeasure.instruments.hp.hp11713a.Attenuator_70dB_4_Section

Logical-value mapping for 0 - 70 dB attenuators using 4 switching sections

## HP 437B Power Meter

### HP 437B Power Meter

 *class *pymeasure.instruments.hp.HP437B(*adapter*, *name='Hewlett-Packard HP437B'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the HP437B Power Meters.

Note

Most command descriptions are sourced from `Operating Manual 437B Power Meter`.

 activate_auto_range()

For each sensor, the power meter splits the power range into 5 ranges, each 10 dB wide. Range 1 handles the highest sensitivity and lowest power levels, while Range 5 is the lowest sensitivity and highest power levels. If a sensor spans less than 50 dB, Range 5 may be under 10 dB. Range selection supports both automatic and manual control. `activate_auto_range` chooses the correct range automatically for the present measurement.

 *property *automatic_range_enabled*: Any*

Controls automatic ranging. For each sensor, the power meter splits the power range into 5 ranges of 10 dB. Range 1 is used for the most sensitive, lowest-power measurements; Range 5 is used for the least sensitive, highest-power measurements. Range selection can be automatic or manual.

 calibrate(*calibration_factor*)

Calibrate a sensor against the power meter using `calibration_factor`, expressed in percent.

 *property *calibration_factor

Controls the calibration factor for a chosen power sensor at a chosen input frequency. Each sensor and its accompanying data sheet include a chart or table of CAL FACTOR % versus Frequency. Enter `calibration_factor` as a percent value; valid entries are 1.0 to 150.0%.

 check_errors()

Read the instrument error queue and log every error.

Returns:

List of error entries.

 *property *display_all_segments_enabled*: Any*

Enable every display segment on the power meter, or return it to normal operation.

 *property *display_enabled*: Any*

Turn the power meter display on or off.

 *property *display_output*: Any*

Return the string of values currently shown on the power meter display.

```python
print(instr.display_output)
-0.23  dB REL

```

 *property *display_user_message*: Any*

Set a custom user message of up to 12 alpha-numerical chars. Passing an empty string or None disables the user message.

 *property *duty_cycle

Controls the duty cycle used to compute a pulsed input signal. With this function, the power meter reports pulse power for a rectangular pulsed input signal. Valid `duty_cycle` values run from 0.00001 to 0.99999.

The pulse power reported by the power meter is calculated mathematically, not directly measured. The meter measures the pulsed input signal's average power, then divides that reading by the duty cycle value to produce pulse power.

 *property *duty_cycle_enabled*: Any*

Controls whether duty cycle operation is enabled. See `duty_cycle`.

 *property *event_status*: Any*

Return the status byte together with the Master Summary Status bit.

```python
print(instr.request_service_conditions)
StatusRegister.PowerOn|CommandError

```

 *property *filter*: Any*

Controls the averaging filter number. Assigning a value implicitly switches on manual filter mode. A value of 1 effectively turns averaging off.

 *property *filter_automatic_enabled*: Any*

Controls filter mode. Changing from automatic to manual (true to false) makes the instrument implicitly retain, or hold, the automatically selected filter value.

 *property *frequency

Controls input-signal frequency. Setting a frequency makes the power meter choose the sensor-specific calibration factor. Allowed `frequency` values are 0.0001 to 999.9999 GHz at 100 kHz resolution. The unit is Hz.

 *property *group_trigger_mode*: Any*

Controls group execute trigger mode. In remote mode, when addressed to listen, the programmed mode determines how the power meter responds to GET, the Group Execute Trigger bus command delivered as a Trigger message.

 *property *limit_high

Controls the upper limit used by builtin limit checking.

 *property *limit_high_hit*: Any*

Return whether the upper limit check was triggered.

 *property *limit_low

Controls the lower limit used by builtin limit checking.

 *property *limit_low_hit*: Any*

Return whether the lower limit check was triggered.

 *property *limits_enabled*: Any*

Controls limit checking so the power meter can monitor sensor power level and indicate when that power falls outside preset limits.

 *property *linear_display_enabled*: Any*

Controls whether displayed or reported power values use logarithmic or linear units. Set linear_display_enabled to `True` to enable linear readout.

```python
from pymeasure.instruments.hp.hp437b import LogLin

instr.relative_mode_enabled = False
instr.linear_display_enabled = True

```

 *property *measurement_unit*: Any*

Return the measurement unit currently used by the power meter for reported power values.

Dependency: `relative_mode_enabled` and attr:linear_display_enabled

```python
instr.relative_mode_enabled = False
instr.linear_display_enabled = True

print(instr.measurement_unit)
MeasurementUnit.Watts

```

 *property *offset

Controls the offset added to the measured value to compensate for signal gain or loss, such as the loss from a 10 dB directional coupler. Offsets use dB. If `offset_enabled` is false, this automatically returns 0.0.

 *property *offset_enabled*: Any*

Control the offset being applied.

 *property *operating_mode*: Any*

Return the power meter's current operating mode.

 *property *power*: Any*

Measures power at the power sensor connected to the power meter and reports it in the corresponding unit. If the measurement would be invalid, the power meter returns `float('nan')`.

 *property *power_reference_enabled*: Any*

Controls the builtin 1mW @ 50 MHz reference power source.

 preset()

Sets the power meter to a known state. The following table lists the preset conditions.

  Preset values
| Parameter | Value/Condition |
| --- | --- |
| Frequency | 50 MHz |
| Resolution | 0.01 dB |
| Duty Cylce | 1.000%, Off |
| Relative | 0 dB, Off |
| Power Reference | Off |
| Range | Auto |
| Unit | dBm |
| Low Limit | -90.000 dBm |
| High Limit | +90.000 dBm |
| Limit Checking | Off |
| Trigger Mode | Free Run |
| Group Trigger Mode | Trigger with Delay |
| Display Function | Display Enable |

 *property *range*: Any*

Controls the range chosen manually. Valid range numbers are 1 through 5. For more details, see `automatic_range_enabled`.

 *property *relative_mode_enabled*: Any*

Controls relative mode. In that mode, the current measured power value becomes the reference, and later values returned by `power` are relative to it.

 reset()

Resets the instrument.

 *property *resolution

Controls measured-value resolution on the power meter. Three resolution levels are available: 0.1 dB, 0.01 dB, and 0.001 dB; when Watts is the selected unit, the levels are 1%, 0.1%, and 0.001%.

 sensor_data_clear(*sensor_id*)

Clear the Sensor Data table for `sensor_id` before entering new values.

 sensor_data_read_cal_factor_table(*sensor_id*)

Read the Sensor Data calibration table. See `sensor_data_write_cal_factor_table()`. Returns a tuple containing frequencies as a list and calibration factors as a list.

 sensor_data_ref_cal_factor(*sensor_id*, *ref_cal_factor*)

Set the power sensor's reference calibration factor in the Sensor Data table.

 sensor_data_write_cal_factor_table(*sensor_id*, *frequency_table*, *cal_fac_table*)

Write `calibration_table` for `sensor_id` into the Sensor Data table, and write the reference calibration factor for `sensor_id`. Frequency is supplied in Hz. Calibration factor is supplied as percentage.

The power meter memory provides room for 10 tables, numbered 0-9. Tables 0-7 can hold 40 frequency/calibration factor pairs each. Tables 8 and 9 can hold 80 frequency/calibration factor pairs each.

This function clears the sensor table before it writes.

Example table:

```python
calibration_table = {
    10e6: 100.0,
    1e9: 96.5,
    2e9: 97.0
}

instr.sensor_data_cal_factor_table(0, calibration_table.keys(),
calibration_table.values())

```

 sensor_data_write_id_label(*sensor_id*, *label*)

Select a specific power sensor's ID label table for modification. The sensor ID label cannot be longer than 7 characters. Example: identify Sensor Data table #2 with ID number 1234567:

```python
instr.sensor_data_id_label(2, "1234567")

```

 *property *sensor_type*: Any*

Set the sensor type connected to the power meter so the matching calibration factor is selected.

```python
from pymeasure.instruments.hp.hp437b import SensorType

instr.sensor_type = SensorType.HP_8481A

```

 store(*register*)

The power meter can save instrument configurations for later recall. These values can be stored in the internal registers:

-

reference calibration factor value

-

Measurement units (dBm or watts)

-

relative value plus status (on or off)

-

power reference status (on or off)

-

calibration factor value

-

SENSOR ID (sensor data table selection)

-

offset value plus status (on or off)

-

range (Auto or Set)

-

frequency value

-

resolution

-

duty cycle value plus status (on or off)

-

Filter setting (number of readings averaged, auto or manual)

-

Limits value plus status (on or off)

Instrument configurations can be stored in registers 1 through 10.

 trigger_delay()

Trigger with delay.

Triggering with delay works like `trigger_immediate()`, but before the requested measurement the power meter waits for a settling-time delay. That interval lets the internal digital filter refresh with new values, producing valid and accurate measurement results. The command gives the internal amplifiers and filters time to settle; it does not include power sensor delay. For large power changes, the delay may still be too short for full settling. To ensure accurate readings, compare two consecutive measurements. After the measurement result is displayed and read onto the bus, the power meter returns to standby mode.

 trigger_immediate()

Trigger immediate.

On receiving the trigger immediate program code, the power meter adds one more data point to the digital filter, measures the filter reading, and updates the display plus HP-IB. Executing trigger immediate does not clear the internal digital filter. The meter then waits until the controller reads the measurement results. During that wait, most bus commands can be handled without losing the results. If a trigger immediate command is followed by GET (Group Execute Trigger), the trigger immediate command is canceled and a fresh measurement cycle runs. After results are read onto the bus, the meter always returns to standby/hold mode. Measurements from trigger immediate are normally valid only when the power meter is steady and settled.

 *property *trigger_mode*: Any*

Control the trigger mode.

The power meter supports two triggered-operation modes: standby mode and free run mode. In standby mode, measurements continue, but the display and HP-IB update only after a trigger command. In free run, Meter continuously measures and updates both the display and HP-IB.

 zero()

Adjusts the power meter's internal circuitry so it indicates zero power when no power is applied to the sensor.

Note

Make sure no power is applied to the sensor during zeroing. Any RF input power during that operation produces an erroneous reading.

## Support class for HP legacy devices

### Support class for HP legacy devices

This implementation is currently used for these instruments, which lack SCPI support:

-

HP3437A System-Voltmeter

-

HP3478A Digital Multimeter

-

HP6632/33/34A System power supply

 *class *pymeasure.instruments.hp.HPLegacyInstrument(*adapter*, *name='HP legacy instrument'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for legacy HP instruments from the pre-SPCI era, derived from pymeasure.Instrument

 GPIB_trigger()

Initiate a trigger with a low-level GPIB-command (aka GET - group execute trigger)

 reset()

Initiates a reset of the HP3478A, equivalent to a power-on reset

 shutdown()

Offers a graceful way to close the connection to the HP3478A

 *property *status

Return an object that represents the unit's current status.

 status_desc

alias of `StatusBitsBase`

 values(*command*, ***kwargs*)

Send a command to the instrument and return formatted response values as a list.

Parameters:

-

**command** - SCPI command sent to the instrument.

-

**preprocess_reply** - Optional callable that preprocesses the string received from the instrument before it is split. The callable returns that processed string.

-

**separator** - Character used to split the device's returned string into a list. None uses any whitespace, as `str.split` does.

-

**maxsplit** - Splits the device-returned string no more than maxsplit times. -1 (default) means unlimited splitting.

-

**cast** –

Type used to cast each split-string element.

Deprecated since version 0.17.0: if casting fails, that element remains a string. A future version will raise an error instead. To allow mixed types explicitly, pass a dedicated function, for example `cast_or_str()` as the cast function.

-

****kwargs** - Keyword arguments forwarded to the `ask()` method.

Returns:

A list of the desired type, or (deprecated) str values where casting fails.

 write(*command*)

Send a string command to the instrument, appending write_termination.

Parameters:

-

**command** - command string sent to the instrument

-

**kwargs** - Keyword arguments for the adapter.

## HP 3437A System-Voltmeter

### HP 3437A System-Voltmeter

 *class *pymeasure.instruments.hp.HP3437A(*adapter*, *name='Hewlett-Packard HP3437A'*, ***kwargs*)

Bases: [`HPLegacyInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html#pymeasure.instruments.hp.HPLegacyInstrument)

Models the Hewlett Packard 3737A system voltmeter with a high-level interface for instrument interaction.

 *class *SRQ(**values*)

Bases: `IntFlag`

Enum element used when decoding SRQ mask bits

 *property *SRQ_mask

Return the current SRQ mask; this property is settable.

bit assignment for SRQ:

| Bit (dec) | Description |
| --- | --- |
| 1 | SRQ when invalid program |
| 2 | SRQ when trigger is ignored |
| 4 | SRQ when data ready |

 check_errors()

Because this instrument has no error indication bit, this function always returns an empty list.

 *property *delay

Return the delay between two measurements as a float; this property is settable.

valid range: 100ns - 0.999999s

 *property *number_readings

Return the number of consecutive measurements as an int; this property is settable, with valid range 0 - 9999.

 pb_desc

alias of `PackedBits`

 *property *range

Return the active measurement voltage range.

This property is settable; valid values are 0.1, 1, 10 (V).

Note

This instrument has no autorange capability.

Overrange is indicated as 0.99,9.99 or 99.9

 read_data()

Reads measured data from the instrument and returns a np.array.

This function also handles data unpacking when required.

Return data:

np.array containing the data

 status_desc

alias of `Status`

 *property *talk_ascii

Boolean property that is True when the instrument uses ASCII-based communication. This property is settable.

 *property *trigger

Return the currently selected trigger mode; this property is settable.

Possible values are:

| Value | Explanation |
| --- | --- |
| internal | automatic trigger (internal) |
| external | external trigger (back connector or GET) |
| hold/manual | holds the measurement or issues a manual trigger |
