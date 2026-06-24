# Lakeshore421, Lakeshore331

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Lake Shore 421 Gaussmeter; Lake Shore 331 Temperature Controller.

## Lake Shore 421 Gaussmeter

### Lake Shore 421 Gaussmeter

 *class *pymeasure.instruments.lakeshore.LakeShore421(*adapter*, *name='Lake Shore 421 Gaussmeter'*, *baud_rate=9600*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Lake Shore 421 Gaussmeter and exposes a high-level interface for working with the instrument.

```python
gaussmeter = LakeShore421("COM1")
gaussmeter.unit = "T"               # Set units to Tesla
gaussmeter.auto_range = True        # Turn on auto-range
gaussmeter.fast_mode = True         # Turn on fast-mode

```

The driver inserts 50 ms between writes because the instrument cannot reliably process faster write timing.

 *property *alarm_active*: Any*

Reports whether the alarm is triggered.

 *property *alarm_audible*: Any*

Control the audible alarm beeper.

 *property *alarm_high

Controls the alarm mode upper setpoint in the current units, with the field multiplier applied.

 *property *alarm_high_multiplier*: Any*

Returns the upper alarm setpoint field multiplier.

 *property *alarm_high_raw*: Any*

Controls the alarm mode upper setpoint using the current unit and multiplier.

 *property *alarm_in_out*: Any*

Selects whether an active alarm occurs when the field reading lies inside ("Inside") or outside ("Outside") the high and low setpoint values.

 *property *alarm_low

Controls the alarm mode lower setpoint in the current units, with the field multiplier applied.

 *property *alarm_low_multiplier*: Any*

Returns the lower alarm setpoint field multiplier.

 *property *alarm_low_raw*: Any*

Controls the alarm mode lower setpoint using the current units and multiplier.

 *property *alarm_mode_enabled*: Any*

Control the alarm mode.

 *property *alarm_sort_enabled*: Any*

Configures the alarm Sort Pass/Fail function.

 *property *auto_range*: Any*

Enables or disables the meter's auto-range option. Valid values are True and False. Auto-range is relatively slow and may not be sufficient for rapid measurements.

 *property *display_filter_enabled*: Any*

Configures the display filter for clearer readings when the probe sees a noisy field. The filter computes a linear average of 8 readings and settles in approximately 2 seconds.

 *property *fast_mode*: Any*

Enables or disables the meter's fast-mode option. Valid values are True and False. When it is enabled, relative mode, Max Hold mode, alarms, and autorange are disabled.

 *property *field

Returns the field in current units, applying the field multiplier. If the field is out of range, returns np.nan.

 *property *field_mode*: Any*

Sets the gaussmeter measurement mode for AC or DC magnetic fields. Allowed values are "AC" and "DC".

 *property *field_multiplier*: Any*

Returns the field multiplier associated with the returned magnetic field.

 *property *field_range

Configures the meter's floating field range in the current unit (G or T). In Gauss, valid values are 30e3, 3e3, 300, 30; in Tesla, valid values are 0.003, 0.03, 0.3, and 3.

 *property *field_range_raw*: Any*

Configures the meter's integer field range. Valid values run from 0 (highest) to 3 (lowest).

 *property *field_raw*: Any*

Returns the field in the current units and multiplier.

 *property *front_panel_brightness*: Any*

Integer control for brightness on the from panel display. Range: 0 (dimmest) through 7 (brightest).

 *property *front_panel_locked*: Any*

Sets the lock state for all front panel entries, except Alarm key presses used to silence alarms.

 *property *max_hold_enabled*: Any*

Controls the Max Hold function, which stores the largest field since the last reset (with max_hold_reset).

 *property *max_hold_field

Returns the largest field since the last reset in current units, with the field multiplier applied. Returns np.nan if the field is out of range.

 *property *max_hold_field_raw*: Any*

Returns, in the current units and multiplier, the largest field recorded since the last reset.

 *property *max_hold_multiplier*: Any*

Returns the multiplier for the max hold field that is returned.

 max_hold_reset()

Clears the stored Max Hold value.

 *property *probe_type*: Any*

Reports the gaussmeter's field-probe type. Possible values are High Sensitivity, High Stability, or Ultra-High Sensitivity.

 *property *relative_field

Returns the relative field in current units, with the field multiplier applied. Returns np.nan if the field is out of range.

 *property *relative_field_raw*: Any*

Returns the relative field in current units together with the current multiplier.

 *property *relative_mode_enabled*: Any*

Configures relative mode for viewing small variations relative to a specified setpoint.

 *property *relative_multiplier*: Any*

Returns the relative field multiplier associated with the returned magnetic field.

 *property *relative_setpoint

Configures the relative field mode setpoint in current units, applying the field multiplier.

 *property *relative_setpoint_multiplier*: Any*

Returns the multiplier for the setpoint field.

 *property *relative_setpoint_raw*: Any*

Configures the relative field mode setpoint using the current units and multiplier.

 *property *serial_number*: Any*

Returns the probe serial number.

 shutdown()

Closes the serial connection to the system.

 *property *unit*: Any*

Configures the gaussmeter units as a string. Valid values are G (Gauss), T (Tesla).

 write(*command*)

Sends a string command to the instrument, appending write_termination.

Parameters:

-

**command** - command string sent to the instrument

-

**kwargs** - Keyword arguments passed to the adapter.

 zero_probe(*wait=True*)

Resets the probe value to 0. Normally this is done with a zero gauss chamber, but an open probe can also be used to cancel the Earth magnetic field. Use relative mode instead when cancelling larger magnetic fields.

Parameters:

**wait** (*bool*) - after issuing the command, wait for 20 seconds so the reset can finish.

## Lake Shore 331 Temperature Controller

### Lake Shore 331 Temperature Controller

 *class *pymeasure.instruments.lakeshore.LakeShore331(*adapter*, *name='Lakeshore Model 331 Temperature Controller'*, *read_termination='\r\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Lake Shore 331 Temperature Controller for instrument access through a high-level interface. The 331 includes two input channels (A and B) plus two output channels (1 and 2). This driver uses the [LakeShore Channel Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#lakeshorechannels).

```python
controller = LakeShore331("GPIB::1")

print(controller.output_1.setpoint)         # Print the current setpoint for loop 1
controller.output_1.setpoint = 50           # Change the loop 1 setpoint to 50 K
controller.output_1.heater_range = 'low'    # Change the heater range to low.
controller.input_A.wait_for_temperature()   # Wait for the temperature to stabilize.
print(controller.input_A.kelvin             # Print the temperature at sensor A.

```

Deprecated since version 0.16.0: LakeShore3xx is the replacement.

 input_A

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_B

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 output_1

Channel:

[`LakeShoreHeaterChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreHeaterChannel)

 output_2

Channel:

[`LakeShoreHeaterChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreHeaterChannel)
