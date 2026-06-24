# Ips120 10, Mercuryitc

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Scope: Oxford Instruments Intelligent Power Supply 120-10 for superconducting magnets and Oxford Instruments Mercury Intelligent Temperature Controller.

## Oxford Instruments Intelligent Power Supply 120-10 for superconducting magnets

### Oxford Instruments Intelligent Power Supply 120-10 for superconducting magnets

 *class *pymeasure.instruments.oxfordinstruments.IPS120_10(*adapter*, *name='Oxford IPS'*, *clear_buffer=True*, *switch_heater_heating_delay=None*, *switch_heater_cooling_delay=None*, *field_range=None*, ***kwargs*)

Bases: [`OxfordInstrumentsBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/base.html#pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase)

Models the Oxford Superconducting Magnet Power Supply IPS 120-10.

```python
ips = IPS120_10("GPIB::25")  # Default channel for the IPS

ips.enable_control()         # Enables the power supply and remote control

ips.train_magnet([           # Train the magnet after it has been cooled-down
    (11.8, 1.0),
    (13.9, 0.4),
    (14.9, 0.2),
    (16.0, 0.1),
])

ips.set_field(12)           # Bring the magnet to 12 T. The switch heater will
                            # be turned off when the field is reached and the
                            # current is ramped back to 0 (i.e. persistent mode).

print(self.field)           # Print the current field (whether in persistent or
                            # non-persistent mode)

ips.set_field(0)            # Bring the magnet to 0 T. The persistent mode will be
                            # turned off first (i.e. current back to set-point and
                            # switch-heater on); afterwards the switch-heater will
                            # again be turned off.

ips.disable_control()       # Disables the control of the supply, turns off the
                            # switch-heater and clamps the output.

```

Parameters:

-

**clear_buffer** - Boolean setting for whether the instrument buffer gets cleared during initialisation. (default: `True`)

-

**switch_heater_heating_delay** - Seconds to wait after enabling the switch-heater before considering the heater heated; the usual value is 20s. (default: `None`)

-

**switch_heater_cooling_delay** - Seconds to wait after disabling the switch-heater before treating the heater as cooled down; the usual value is 20s. (default: `None`)

-

**field_range** - Numeric limit or two-value tuple giving the minimum and maximum allowed magnetic fields. With one numeric value, the valid span is `-field_range` through `+field_range`. The default range is -7 to +7 Tesla. (default: `None`)

 *property *activity*: Any*

String-valued activity selector for the IPS. Valid values are "hold", "to setpoint", "to zero" and "clamp"

 *property *control_mode*: Any*

String setting that places the IPS into local or remote mode and locked or unlocked mode, including locking the LOC/REM button. Allowed values are:

| value | state |
| --- | --- |
| LL | local & locked |
| RL | remote & locked |
| LU | local & unlocked |
| RU | remote & unlocked |

 *property *current_measured*: Any*

Floating point readback for the measured IPS magnet current, in amps. (dynamic)

 *property *current_setpoint*: Any*

Floating point control for the IPS magnet current set-point, in ampere. (dynamic)

 *property *demand_current*: Any*

Floating point readback for the IPS demand magnet current, in amps. (dynamic)

 *property *demand_field*: Any*

Floating point readback for the IPS demand magnetic field, in Tesla. (dynamic)

 disable_control()

When the field is at 0T, disables IPS active control by switching off the switch heater, clamping the output, and placing control in local mode. If the field is not at 0T, raises `MagnetError`.

 disable_persistent_mode()

Turns off persistent magnetic field mode. If the magnet is not at rest, raises `MagnetError`.

 enable_control()

Enables IPS active control by setting control to remote and turning off the clamp.

 enable_persistent_mode()

Turns on persistent magnetic field mode. If the magnet is not at rest, raises `MagnetError`.

 *property *field

Returns the present magnetic field value in Tesla.

 *property *field_setpoint*: Any*

Floating point control for the IPS magnetic field set-point, in Tesla. (dynamic)

 *property *persistent_field*: Any*

Floating point readback for the IPS persistent magnetic field, in Tesla. (dynamic)

 set_field(*field*, *sweep_rate=None*, *persistent_mode_control=True*)

Sweeps the applied magnetic field to a requested magnitude. When `persistent_mode_control` permits it, persistent mode is disabled as necessary before the sweep and re-enabled once the target field is reached. For a new field set-point of 0, the instrument set-point is left unchanged and the IPS to zero function is used instead. In that 0T case, persistent mode is not re-enabled after the target is reached.

Parameters:

-

**field** - New magnetic field set-point, in Tesla.

-

**sweep_rate** - Numeric control for how quickly the magnetic field changes, in Tesla/minute. (default: `None`)

-

**persistent_mode_control** - Boolean permission for switching persistent mode off before sweeping when needed and back on after the field is reached; if this is `False` while the system is already in persistent mode, `MagnetError` is raised and the magnetic field remains unchanged. (default: `True`)

 *property *sweep_rate*: Any*

Floating point control for the IPS sweep-rate, in Tesla/minute. (dynamic)

 *property *sweep_status*: Any*

String readback for the IPS current sweeping mode.

 *property *switch_heater_enabled

Boolean control/readback indicating switch-heater enablement. For `True`, magnet-current control is possible; the stated switch condition is both closed and open. For `False`, the switch is closed and magnet current cannot be controlled.

When setting the switch heater to `True`, activation occurs only if the power-supply current matches the magnet's last recorded current.

Warning

Using `"Force"` instead of `True` omits these checks. Caution: skipping them can seriously damage both the power supply and the magnet.

After the switch heater is turned on, wait several seconds for the switch to respond.

Raises `SwitchHeaterError` if, when status is read, the system reports a 'heater fault' or reports that no switch is fitted.

 *property *switch_heater_status*: Any*

Integer readback for the IPS switch heater status. Use `switch_heater_enabled` to read and control the switch heater. For this property, consult the IPS120-10 manual for the meaning of each integer value.

 train_magnet(*training_scheme*)

Trains the magnet after cooling down, then returns the field to 0 tesla using the last-used ramp-rate.

Parameters:

**training_scheme** - Training schedule given as a list of tuples; every tuple contains a (field [T], ramp-rate [T/min]) pair.

 *property *version*: Any*

String readback for the IPS version.

 wait_for_idle(*delay=1*, *max_wait_time=None*, *should_stop=<function IPS120_10.<lambda>>*)

Blocks until the system is idle, meaning the current or field is not ramping.

Parameters:

-

**delay** - Seconds between successive state queries to the instrument. (default: `1`)

-

**max_wait_time** - Maximum number of seconds to wait for the system to become at rest. If it is still not at rest after this time, `TimeoutError` is raised. `None` means there is no maximum time. (default: `None`)

-

**should_stop** - Function returning `True` when `wait_for_idle` should return before normal completion. (default: `<function IPS120_10.<lambda> at 0x7aa57f5de140>`)

 *class *pymeasure.instruments.oxfordinstruments.ips120_10.MagnetError

Bases: `ValueError`

Exception raised for problems with the magnet state or the power-supply state.

 *class *pymeasure.instruments.oxfordinstruments.ips120_10.SwitchHeaterError

Bases: `ValueError`

Exception raised when the superconducting switch state causes an issue.

## Oxford Instruments Mercury Intelligent Temperature Controller

### Oxford Instruments Mercury Intelligent Temperature Controller

 *class *pymeasure.instruments.oxfordinstruments.MercuryiTC(*adapter*, *name='Oxford MercuryiTC'*, ***kwargs*)

Provides a high-level interface for the Oxford Instruments Mercury iTC (Intelligent Temperature Controller). Its GPIB behavior is not fully SCPI-compliant; the only supported command is `*IDN?`. A Mercury iTC may use either a so-called SCPI instruction set, which is still not a true SCPI implementation, or a legacy instruction set. This implementation uses the so-called SCPI instruction set.

The iTC can be expanded with daughter boards for mixed temperature sensors, heaters, pressure sensors, cryogen level sensors, and auxiliary I/O. At present, this implementation covers only temperature sensors and heaters.

By default, one temperature sensor channel with Unique Identifier (`UID`) `'MB1.T1'` and one heater channel with UID `'MB0.H1'` are installed. Controller instantiation creates both channels automatically. They are available as `.TS_MB` and `.HTR_MB`, and also through the dictionary collections `.TS['MB1.T1']` and `.HTR['MB0.H1']`.

Additional daughter boards can host other sensors and heaters with specific `UID` values, for example `'DBX.T1'`, `'DBX.H1'` etc. After a MercuryiTC instance already exists, add them manually with `.add_temperature_sensor(UID)` and `.add_heater(UID)`. Use the correct UID reported by the Mercury iTC itself, because communication addresses channels by that UID. Access for these added channels is **only** through `.TS[UID]` and `.HTR[UID]`.

```python
controller = MercuryiTC("GPIB::1")

# Print the current measured temperature of the motherboard temperature sensor aka 'MB1.T1'
print(controller.TS_MB.temperature)

# Print the motherboard temperature sensor control-loop setpoint
print(controller.TS['MB1.T1'].loop_T_setpoint)

# Add new temperature sensor with UID 'DB6.T1'
controller.add_temperature_sensor('DB6.T1')

# Print the new sensor's temperature
print(controller.TS['DBS.T1'].temperature)

```

 HTR_MB

Channel:

`Heater`

 TS_MB

Channel:

`TemperatureSensor`

 add_heater(*id*, *prefix='HTR'*, ***kwargs*)

Adds a heater identified by `id` to the addressable-heater collection `.HTR[id]`.

 add_temperature_sensor(*id*, *prefix='TS'*, ***kwargs*)

Adds a temperature sensor identified by `id` to the addressable-temperature-sensor collection `.TS[id]`.

 *property *identity*: Any*

Get identity of unit.

 *class *pymeasure.instruments.oxfordinstruments.mercuryitc.TemperatureSensor(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Temperature sensor channel for the Oxford Instruments Mercury iTC.

Because validity depends on sensor type, such as diode or NTC/PTC resistor, some properties may not apply. Sensor configuration therefore has to be known and configured a priori. Currently, only diode sensor types are implemented.

Loop control is grouped with temperature sensor properties because control loops are reached through temperature sensors rather than through heaters.

 check_set_errors()

For every MercuryiTC get or set communication, the instrument sends a response. Setting a property therefore reads the response back.

 *property *control_loop_D*: Any*

Controls the control-loop derivative term, D.

 *property *control_loop_I*: Any*

Controls the control-loop integral term, I.

 *property *control_loop_P*: Any*

Controls the control-loop proportional term, P.

 *property *control_loop_PID_enabled*: Any*

Selects whether the control-loop heater follows the PID loop (`True`) or manual heater percentage (`False`).

 *property *control_loop_heater_percent*: Any*

Sets the heater percentage when the output is in manual mode, using the range 0 to 100.

 *property *control_loop_ramp_enabled*: Any*

Enables (`True`) or disables (`False`) the temperature ramping function.

 *property *control_loop_ramp_rate*: Any*

Sets the enabled control-loop ramp rate in K/min, within the range 0 to 100000.

 *property *control_loop_temperature_setpoint*: Any*

Sets the control-loop temperature setpoint in Kelvin, within the range 0 to 2000.

 *property *temperature*: Any*

Returns the measured temperature in Kelvin.

 *property *voltage*: Any*

Returns the sensor voltage in Volts.

 *class *pymeasure.instruments.oxfordinstruments.mercuryitc.Heater(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Heater channel for the Oxford Instruments Mercury iTC.

The heater output exposes several parameters, and some properties are configurable. PID control is handled through an associated temperature sensor. The heater is assumed to already be linked to a temperature sensor control loop, or else configured for open-loop operation.

 check_set_errors()

MercuryiTC replies to every get and set exchange, so setting a property is followed by reading back the response.

 *property *current*: Any*

Returns the heater excitation current in Amps.

 *property *max_power*: Any*

Returns the heater's provisional maximum power in Watts.

 *property *power*: Any*

Returns the heater power dissipation in Watts.

 *property *resistance*: Any*

Sets the programmed heater resistance in Ohms; the float must be strictly in the range of 10 to 2000.

 *property *voltage*: Any*

Returns the heater excitation voltage in Volts.

 *property *voltage_limit*: Any*

Sets the heater-output voltage limit in Volts; the float must be strictly from 0 to 40.
