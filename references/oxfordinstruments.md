# Itc503, Base, Ps120 10

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

This reference covers Oxford Instruments Intelligent Temperature Controller 503, the Oxford Instruments topic, Oxford Instruments Base Instrument, and Oxford Instruments Power Supply 120-10 for superconducting magnets.

## Oxford Instruments Intelligent Temperature Controller 503

### Oxford Instruments Intelligent Temperature Controller 503

 *class *pymeasure.instruments.oxfordinstruments.ITC503(*adapter*, *name='Oxford ITC503'*, *clear_buffer=True*, *min_temperature=0*, *max_temperature=1677.7*, ***kwargs*)

Bases: [`OxfordInstrumentsBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/base.html#pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase)

Models the Oxford Intelligent Temperature Controller 503.

```python
itc = ITC503("GPIB::24")        # Default channel for the ITC503

itc.control_mode = "RU"         # Set the control mode to remote
itc.heater_gas_mode = "AUTO"    # Turn on auto heater and flow
itc.auto_pid = True             # Turn on auto-pid

print(itc.temperature_setpoint) # Print the current set-point
itc.temperature_setpoint = 300  # Change the set-point to 300 K
itc.wait_for_temperature()      # Wait for the temperature to stabilize
print(itc.temperature_1)        # Print the temperature at sensor 1

```

 *class *FLOW_CONTROL_STATUS(**values*)

Bases: `IntFlag`

An IntFlag class used to interpret flow control status, with these flags:

| bit | flag | meaning |
| --- | --- | --- |
| 4 | HEATER_ERROR_SIGN | Heater-error sign indicator; True denotes negative |
| 3 | TEMPERATURE_ERROR_SIGN | Temperature-error sign indicator; True denotes negative |
| 2 | SLOW_VALVE_ACTION | Slow valve action occurring |
| 1 | COOLDOWN_TERMINATION | Cooldown-termination occurring |
| 0 | FAST_COOLDOWN | Fast-cooldown occurring |

 *property *auto_pid*: Any*

Boolean property for turning Auto-PID mode on (True) or off (False).

 *property *auto_pid_table*: Any*

Property for manipulating entries in the auto-pid table. `ITC503.x_pointer` and `ITC503.y_pointer` (or `ITC503.pointer`) choose the table location to write or read.

The x-pointer identifies the table entry (1 to 16), while the y-pointer chooses the parameter:

| y-pointer | parameter |
| --- | --- |
| 1 | upper temperature limit |
| 2 | proportional band |
| 3 | integral action time |
| 4 | derivative action time |

 *property *control_mode*: Any*

String property for placing the ITC in local or remote control and in locked or unlocked state, including locking the LOC/REM button. Allowed values are:

| value | state |
| --- | --- |
| LL | local & locked |
| RL | remote & locked |
| LU | local & unlocked |
| RU | remote & unlocked |

 *property *derivative_action_time*: Any*

Floating point property for the PID controller derivative action time, measured in minutes. Setting it requires manual mode for the PID controller. Accepted range: 0 [min.] to 273 [min.].

 *property *front_panel_display*: Any*

String property selecting the value shown on the ITC front panel. Accepted values include 'temperature setpoint', 'temperature 1', 'temperature 2', 'temperature 3', 'temperature error', 'heater', and 'heater voltage'. Other choices include 'gasflow', 'proportional band', and 'integral action time'. The remaining display choices are 'derivative action time', 'channel 1 freq/4', 'channel 2 freq/4', and 'channel 3 freq/4'.

 *property *gasflow*: Any*

Floating point property for manual-mode gas flow control. The value is expressed as a percentage of maximum gas flow; accepted range: 0 [off] to 99.9 [%].

 *property *gasflow_configuration_parameter*: Any*

Property for gas flow configuration parameters. `ITC503.x_pointer` selects which parameter is written or read:

| x-pointer | parameter |
| --- | --- |
| 1 | valve gearing |
| 2 | target table & features configuration |
| 3 | gas flow scaling |
| 4 | temperature error sensitivity |
| 5 | heater voltage error sensitivity |
| 6 | minimum gas valve in auto |

 *property *gasflow_control_status*: Any*

Property that reads gas-flow control status and returns it as a `ITC503.FLOW_CONTROL_STATUS` IntFlag.

 *property *heater*: Any*

Floating point property for heater output power as a percentage of maximum voltage. It is writable when the heater is in manual mode. Accepted range: 0 [off] to 99.9 [%].

 *property *heater_gas_mode*: Any*

String property for switching heater and gas flow control between auto and manual operation. Allowed values are:

| value | state |
| --- | --- |
| MANUAL | heater & gas manual |
| AM | heater auto, gas manual |
| MA | heater manual, gas auto |
| AUTO | heater & gas auto |

 *property *heater_voltage*: Any*

Floating point property reporting heater output power in volts. To control the heater, use `ITC503.heater`.

 *property *integral_action_time*: Any*

Floating point property for the PID controller integral action time, in minutes. Changing it requires the PID controller to be in manual mode. Accepted range: 0 [min.] to 140 [min.].

 *property *pointer*: Any*

Tuple property, in the form (x, y), for pointing into tables when loading or inspecting table values. Which pointer values are meaningful, and which values are allowed, depends on the property being read or written. x and y can each be in the range 0 to 128.

 program_sweep(*temperatures*, *sweep_time*, *hold_time*, *steps=None*)

Programs a temperature sweep in the controller and stops any sweep already running. Once the sweep has been programmed, start it with OxfordITC503.sweep_status = 1.

Parameters:

-

**temperatures** - Array containing the temperatures used for the sweep

-

**sweep_time** - Time, or array of times, for sweeping to a set-point in minutes (between 0 and 1339.9).

-

**hold_time** - Time, or array of times, to remain at a set-point in minutes (between 0 and 1339.9).

-

**steps** - Number of steps in the sweep; when supplied, temperatures, sweep_time and hold_time are interpolated into approximately equal segments (default: `None`)

 *property *proportional_band*: Any*

Floating point property for the PID controller proportional band, measured in Kelvin. It is writable only with the PID controller in manual mode. Accepted range: 0 [K] to 1677.7 [K].

 *property *sweep_status*: Any*

Integer property used to set sweep status. Values are:

| value | meaning |
| --- | --- |
| 0 | Sweep not running |
| 1 | Begin sweep / sweeping to first set-point |
| 2P - 1 | Sweeping to set-point P |
| 2P | Holding at set-point P |

 *property *sweep_table*: Any*

Property for working with entries in the sweep table. `ITC503.x_pointer` and `ITC503.y_pointer` (or `ITC503.pointer`) select the table location to read or set.

The x-pointer chooses the sweep step (1 to 16), and the y-pointer chooses the parameter:

| y-pointer | parameter |
| --- | --- |
| 1 | set-point temperature |
| 2 | sweep-time to set-point |
| 3 | hold-time at set-point |

 *property *target_voltage*: Any*

Float property that reads the current heater target voltage, which is compared against actual heater voltage. Only valid if gas-flow in auto mode.

 *property *target_voltage_table*: Any*

Property for entries in the target heater voltage table. `ITC503.x_pointer` selects the table entry to set or read (1 to 64).

 *property *temperature_1*: Any*

Reads sensor 1 temperature in Kelvin.

 *property *temperature_2*: Any*

Reads sensor 2 temperature in Kelvin.

 *property *temperature_3*: Any*

Reads sensor 3 temperature in Kelvin.

 *property *temperature_error*: Any*

Reads the Kelvin difference between the set-point and measured temperature. The value is positive when the set-point is larger than measured.

 *property *temperature_setpoint*: Any*

Floating point property for the ITC temperature set-point in kelvin. (dynamic)

 *property *valve_scaling*: Any*

Reads the valve scaling parameter as a float. Only valid when gas-flow is in auto mode.

 *property *version*: Any*

String property that reports the IPS version.

 wait_for_temperature(*error=0.01*, *timeout=3600*, *check_interval=0.5*, *stability_interval=10*, *thermalize_interval=300*, *should_stop=<function ITC503.<lambda>>*)

Waits until the ITC reaches the set-point temperature.

Parameters:

-

**error** - Maximum Kelvin error below which the temperature is treated as being at set-point (default: `0.01`)

-

**timeout** - Maximum duration allowed for waiting. Exceeding timeout raises TimeoutError. If timeout is None, no timeout is applied. (default: `3600`)

-

**check_interval** - Time between temperature queries sent to the ITC. (default: `0.5`)

-

**stability_interval** - Time span during which temperature_error must remain below error for the temperature to count as stable. (default: `10`)

-

**thermalize_interval** - Waiting time after stabilization so the system can thermalize. (default: `300`)

-

**should_stop** - Optional bool-returning function that can stop the wait before it completes. (default: `<function ITC503.<lambda> at 0x7aa57f5e6fb0>`)

 wipe_sweep_table()

Clears the sweep table currently programmed.

 *property *x_pointer*: Any*

Integer property for pointing into tables while loading or inspecting table values. The meaning and valid range of the pointer depend on the property being read or set.

 *property *y_pointer*: Any*

Integer property for pointing into tables while loading or inspecting table values. The meaning and valid range of the pointer depend on the property being read or set.

## Oxford Instruments

### Oxford Instruments

This section documents the implemented Oxford Instruments instruments. For an instrument that is not present here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Oxford Instruments Base Instrument](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/base.html)
  - [`OxfordInstrumentsBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/base.html#pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase)
  - [`OxfordVISAError`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/base.html#pymeasure.instruments.oxfordinstruments.base.OxfordVISAError)

- [Oxford Instruments Intelligent Temperature Controller 503](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/ITC503.html)
  - [`ITC503`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/ITC503.html#pymeasure.instruments.oxfordinstruments.ITC503)

- [Oxford Instruments Intelligent Power Supply 120-10 for superconducting magnets](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/IPS120_10.html)
  - [`IPS120_10`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/IPS120_10.html#pymeasure.instruments.oxfordinstruments.IPS120_10)
  - [`MagnetError`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/IPS120_10.html#pymeasure.instruments.oxfordinstruments.ips120_10.MagnetError)
  - [`SwitchHeaterError`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/IPS120_10.html#pymeasure.instruments.oxfordinstruments.ips120_10.SwitchHeaterError)

- [Oxford Instruments Mercury Intelligent Temperature Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/MercuryiTC.html)
  - [`MercuryiTC`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/MercuryiTC.html#pymeasure.instruments.oxfordinstruments.MercuryiTC)
  - [`TemperatureSensor`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/MercuryiTC.html#pymeasure.instruments.oxfordinstruments.mercuryitc.TemperatureSensor)
  - [`Heater`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/MercuryiTC.html#pymeasure.instruments.oxfordinstruments.mercuryitc.Heater)

- [Oxford Instruments Power Supply 120-10 for superconducting magnets](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/PS120_10.html)
  - [`PS120_10`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/PS120_10.html#pymeasure.instruments.oxfordinstruments.PS120_10)

## Oxford Instruments Base Instrument

### Oxford Instruments Base Instrument

 *class *pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase(*adapter*, *name='OxfordInstruments Base'*, *max_attempts=5*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Base instrument class for Oxford Instruments devices.

Validates replies received from instruments.

Parameters:

-

**adapter** - A string, integer, or [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) subclass object

-

**name** (*string*) - Instrument name, often defaulting to the model designation.

-

**max_attempts** - Integer specifying how many tries may be made to obtain a valid query response (default: `5`)

-

****kwargs** - When `adapter` is a string or integer, additional arguments are passed to [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) (see that documentation for details). Otherwise, they are discarded.

 ask(*command*)

Sends the command to the instrument, checks that the response is valid, and returns the resulting ASCII response. If the response is invalid, another attempt is made until the maximum number of attempts has been reached.

Parameters:

**command** - ASCII command string sent to the instrument

Returns:

Instrument response as an ASCII string

Raises:

`OxfordVISAError` if the maximum number of attempts is exceeded before a valid response is obtained

 is_valid_response(*response*, *command*)

Checks whether the response returned after a command is valid and was understood by the instrument.

Parameters:

-

**response** - ASCII string response from the device

-

**command** - command from the original query

Returns:

True when the response is valid and indicates that the instrument recognised the command

 write(*command*)

Writes a command to the instrument and checks whether the reply says that the supplied command was not understood. Oxford Instruments devices answer with '?xxx' for a command 'xxx' when that command is unknown, and answer with 'x' when the command is understood. A command beginning with "$" receives no reply from the instrument, so no reply check is performed in that case.

Raises:

Raises `OxfordVISAError` when the supplied command is not recognised by the instrument or the instrument response cannot be understood

 *class *pymeasure.instruments.oxfordinstruments.base.OxfordVISAError

Bases: `Exception`

## Oxford Instruments Power Supply 120-10 for superconducting magnets

### Oxford Instruments Power Supply 120-10 for superconducting magnets

 *class *pymeasure.instruments.oxfordinstruments.PS120_10(*adapter*, *name='Oxford PS'*, ***kwargs*)

Bases: [`IPS120_10`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/IPS120_10.html#pymeasure.instruments.oxfordinstruments.IPS120_10)

Models the Oxford Superconducting Magnet Power Supply PS 120-10.

```python
ps = PS120_10("GPIB::25")   # Default channel for the IPS

ps.enable_control()         # Enables the power supply and remote control

ps.train_magnet([           # Train the magnet after it has been cooled-down
    (11.8, 1.0),
    (13.9, 0.4),
    (14.9, 0.2),
    (16.0, 0.1),
])

ps.set_field(12)            # Bring the magnet to 12 T. The switch heater will
                            # be turned off when the field is reached and the
                            # current is ramped back to 0 (i.e. persistent mode).

print(self.field)           # Print the current field (whether in persistent or
                            # non-persistent mode)

ps.set_field(0)             # Bring the magnet to 0 T. The persistent mode will be
                            # turned off first (i.e. current back to set-point and
                            # switch-heater on); afterwards the switch-heater will
                            # again be turned off.

ps.disable_control()        # Disables the control of the supply, turns off the
                            # switch-heater and clamps the output.

```

Parameters:

-

**clear_buffer** - Boolean property controlling whether the instrument buffer is cleared during initialisation.

-

**switch_heater_heating_delay** - Time in seconds (default is 20s) to wait after switch-heater turn-on before expecting the heater to be heated.

-

**switch_heater_cooling_delay** - Time in seconds (default is 20s) to wait after switch-heater turn-off before expecting the heater to be cooled down.

-

**field_range** - Numeric value or two-value tuple indicating the lowest and highest permitted magnetic fields. If a numeric value is supplied, the expected range is `-field_range` to `+field_range`.

 *class *pymeasure.instruments.oxfordinstruments.ips120_10.MagnetError

Bases: `ValueError`

Exception raised for problems involving the magnet state or power supply state.

 *class *pymeasure.instruments.oxfordinstruments.ips120_10.SwitchHeaterError

Bases: `ValueError`

Exception raised for problems involving the superconducting switch state.
