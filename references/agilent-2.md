# Agilentb298X, Agilent34410A

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Coverage: Agilent B2980 Series, Femto/Picoammeter Electrometer/High Resistance Meter; Agilent 34410A Multimeter.

## Agilent B2980 Series, Femto/Picoammeter Electrometer/High Resistance Meter

### Agilent B2980 Series, Femto/Picoammeter Electrometer/High Resistance Meter

 Class API: pymeasure.instruments.agilent.AgilentB2981; parameters: *adapter*, *name='Agilent/Keysight B2980A/B series'*, ***kwargs*.

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class wrapper for the Agilent/Keysight B2981A/B.

The B2981 model is a Femto/Picoammeter.

 abort()

Abort the all actions.

Return type:

`None`

 abort_acquisition()

Abort action ‘ACQuire’.

Return type:

`None`

 arm()

Issue an immediate arm trigger across every action.

After every action reaches initiated status, the arm trigger moves execution from the arm layer to the trigger layer.

Return type:

`None`

 arm_acquisition()

Issue an immediate arm trigger for action â€˜ACQuireâ€™.

Once action â€˜ACQuireâ€™ reaches initiated status, the arm trigger transfers execution from the arm layer to the trigger layer.

Return type:

`None`

 *property *arm_acquisition_bypass_once_enabled*: Any*

Enable or disable the event-detector bypass in the arm layer for action â€˜ACQuireâ€™ (bool).

 *property *arm_acquisition_count*: Any*

Configure the arm trigger count for action â€˜ACQuireâ€™.

Type:

-

int, strictly from `1` to `100000` or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `INF`

`INF` is equivalent to `2147483647`

 *property *arm_acquisition_delay*: Any*

Configure the arm trigger delay for action â€˜ACQuireâ€™, in seconds.

Type:

-

float; allowed range is `0` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *arm_acquisition_output_enabled*: Any*

Enable or disable arm trigger output for action â€˜ACQuireâ€™ (bool).

Applies to the transition between the idle state and the arm layer.

 *property *arm_acquisition_output_signal*: Any*

Select the arm trigger output signal for action â€˜ACQuireâ€™.

Type:

str; accepted values are exactly `INT1`, `INT2`, `LAN`, `TOUT`, `EXT1` to `EXT7`

-

`INT1` or `INT2` chooses internal bus 1 or 2.

-

`LAN` selects a LAN port.

-

`EXT1` to `EXT7` chooses GPIO pin n on the rear-panel Digital I/O D-sub connector as an output port. n = 1 to 7.

-

`TOUT` chooses the BNC Trigger Out.

Applies to the transition between the idle state and the arm layer.

 *property *arm_acquisition_source*: Any*

Select the arm trigger source for action â€˜ACQuireâ€™.

Type:

str; accepted values are exactly `AINT`, `BUS`, `TIM`, `INT1`, `INT2`, `LAN`, `TIN`, `EXT1` to `EXT7`

-

`AINT` lets internal algorithms choose the arm source best matched to the present operating mode.

-

`BUS` uses a remote-interface trigger command, including the group execute trigger (GET) and the TRG command.

-

`TIM` uses an internally produced signal at the interval configured by the arm_timer command.

-

`INT1` and `INT2` use a signal from internal bus 1 or 2.

-

`LAN` uses the LXI trigger identified by the arm_source_lan_id command.

-

`EXT1` to `EXT7` uses GPIO pin n on the rear-panel Digital I/O D-sub connector as an input port. n = 1 to 7.

-

`TIN` uses the BNC Trigger In.

 *property *arm_acquisition_source_lan_id*: Any*

Configure the LAN arm-trigger source for action â€˜ACQuireâ€™.

Type:

str; allowed range is `LAN0` through `LAN7`

 *property *arm_acquisition_timer*: Any*

Set the arm trigger source timer interval for action â€˜ACQuireâ€™, in seconds.

Type:

-

float; allowed range is `1E-5` through `1E5`

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *arm_all_bypass_once_enabled*: Any*

Configure the event-detector bypass in the arm layer for action â€˜ALLâ€™ (bool).

 *property *arm_all_count*: Any*

Configure the arm trigger counter for action â€˜ALLâ€™.

Type:

-

int, strictly from `1` to `100000` or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `INF`

`INF` is equivalent to `2147483647`.

 *property *arm_all_delay*: Any*

Configure the arm trigger delay for action â€˜ALLâ€™, in seconds.

Type:

-

float; allowed range is `0` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *arm_all_output_enabled*: Any*

Configure arm trigger output for action â€˜ALLâ€™ (bool).

Applies to the transition between the idle state and the arm layer.

 *property *arm_all_output_signal*: Any*

Select the arm trigger output signal for action â€˜ALLâ€™.

Type:

str; accepted values are exactly `INT1`, `INT2`, `LAN`, `TOUT`, `EXT1` to `EXT7`

-

`INT1` and `INT2` choose internal bus 1 or 2.

-

`LAN` selects a LAN port.

-

`EXT1` to `EXT7` chooses GPIO pin n on the rear-panel Digital I/O D-sub connector as an output port. n = 1 to 7.

-

`TOUT` chooses the BNC Trigger Out.

Applies to the transition between the idle state and the arm layer.

 *property *arm_all_source*: Any*

Select the arm trigger source for action â€˜ALLâ€™.

Type:

str; accepted values are exactly `AINT`, `BUS`, `TIM`, `INT1`, `INT2`, `LAN`, `TIN`, `EXT1` to `EXT7`

-

`AINT` lets internal algorithms choose the arm source best matched to the present operating mode.

-

`BUS` uses a remote-interface trigger command, including the group execute trigger (GET) and the TRG command.

-

`TIM` uses an internally generated signal at the interval set by attr:arm_all_timer.

-

`INT1` and `INT2` use a signal from internal bus 1 or 2.

-

`LAN` uses the LXI trigger identified by `arm_all_source_lan_id`.

-

`EXT1` to `EXT7` uses GPIO pin n on the rear-panel Digital I/O D-sub connector as an input port. n = 1 to 7.

-

`TIN` uses the BNC Trigger In.

 *property *arm_all_source_lan_id*: Any*

Configure the LAN arm-trigger source for action â€˜ALLâ€™.

Type:

str; allowed range is `LAN0` through `LAN7`

 *property *arm_all_timer*: Any*

Set the arm trigger source timer interval for action â€˜ALLâ€™, in seconds.

Type:

-

float; allowed range is `1E-5` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *current*: Any*

Take a spot current measurement in Amps.

Returns:

float

 *property *current_range*: Any*

Configure the current-measurement range in Amps.

Type:

-

float; allowed range is `2E-12` through `20E-3`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `UP`, `DOWN`

 *property *data_buffer_size*: Any*

Read the data buffer size (int).

 init()

Start a trigger for every action.

Return type:

`None`

 init_acquisition()

Start a trigger for action â€˜ACQuireâ€™.

Return type:

`None`

 *property *input_enabled*: Any*

Configure the instrument input relay (bool).

 *property *interlock_enabled*: Any*

Get the interlock status (bool).

 *property *measure*: Any*

Perform a spot measurement for the configured parameter(s).

Returns:

float or list of float

 *property *trigger_acquisition_bypass_once_enabled*: Any*

Enable or disable the event-detector bypass in the trigger layer for action â€˜ACQuireâ€™ (bool).

 *property *trigger_acquisition_count*: Any*

Configure the trigger count for action â€˜ACQuireâ€™.

Type:

-

int, strictly from `1` to `100000` or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `INF`

`INF` is equivalent to `2147483647`.

 *property *trigger_acquisition_delay*: Any*

Configure the trigger delay for action â€˜ACQuireâ€™, in seconds.

Type:

-

float; allowed range is `0` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *trigger_acquisition_is_idle*: Any*

Read whether action â€˜ACQuireâ€™ is idle (bool).

This command waits until the status becomes idle.

 *property *trigger_acquisition_output_enabled*: Any*

Enable or disable trigger output for action â€˜ACQuireâ€™ (bool).

Applies to the transition between the idle state and the trigger layer.

 *property *trigger_acquisition_output_signal*: Any*

Select the trigger signal output for action â€˜ACQuireâ€™.

Type:

str; accepted values are exactly `INT1`, `INT2`, `LAN`, `TOUT`, `EXT1` to `EXT7`

-

`INT1` and `INT2` choose internal bus 1 or 2.

-

`LAN` selects a LAN port.

-

`EXT1` to `EXT7` chooses GPIO pin n on the rear-panel Digital I/O D-sub connector as an output port. n = 1 to 7.

-

`TOUT`: chooses the BNC Trigger Out.

Applies to the transition between the idle state and the trigger layer.

 *property *trigger_acquisition_source*: Any*

Select the trigger source for action â€˜ACQuireâ€™.

Type:

str; accepted values are exactly `AINT`, `BUS`, `TIM`, `INT1`, `INT2`, `LAN`, `TIN`, `EXT1` to `EXT7`

-

`AINT` lets internal algorithms choose the trigger source best matched to the present operating mode.

-

`BUS` uses a remote-interface trigger command, including the group execute trigger (GET) and the TRG command.

-

`TIM` uses an internally generated signal at each interval set by the `trigger_acquisition_timer`.

-

`INT1` and `INT2` use a signal from internal bus 1 or 2.

-

`LAN` uses the LXI trigger identified by `trigger_acquisition_source_lan_id`.

-

`EXT1` to `EXT7` uses GPIO pin n on the rear-panel Digital I/O D-sub connector as an input port. n = 1 to 7.

-

`TIN` uses the BNC Trigger In.

 *property *trigger_acquisition_source_lan_id*: Any*

Configure the LAN trigger source for action â€˜ACQuireâ€™.

Type:

str; allowed range is `LAN0` through `LAN7`

 *property *trigger_acquisition_timer*: Any*

Set the trigger source timer interval for action â€˜ACQuireâ€™, in seconds.

Type:

-

float; allowed range is `1E-5` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *trigger_all_bypass_once_enabled*: Any*

Configure the event-detector bypass in the trigger layer for action â€˜ALLâ€™ (bool).

 *property *trigger_all_count*: Any*

Configure the trigger count for action â€˜ALLâ€™.

Type:

-

int, strictly from `1` to `100000` or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `INF`

`INF` is equivalent to `2147483647`.

 *property *trigger_all_delay*: Any*

Configure the trigger delay for action â€˜ALLâ€™, in seconds.

Type:

-

float; allowed range is `0` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *trigger_all_is_idle*: Any*

Read whether action â€˜ALLâ€™ has idle trigger status (bool).

This command waits until the status becomes idle.

 *property *trigger_all_output_enabled*: Any*

Configure trigger output for action â€˜ALLâ€™ (bool).

Applies to the transition between the idle state and the trigger layer.

 *property *trigger_all_output_signal*: Any*

Select the trigger signal output for action â€˜ALLâ€™.

Type:

str; accepted values are exactly `INT1`, `INT2`, `LAN`, `TOUT`, `EXT1` to `EXT7`

-

`INT1` and `INT2` choose internal bus 1 or 2.

-

`LAN` selects a LAN port.

-

`EXT1` to `EXT7` chooses GPIO pin n on the rear-panel Digital I/O D-sub connector as an output port. n = 1 to 7.

-

`TOUT` chooses the BNC Trigger Out.

Applies to the transition between the idle state and the trigger layer.

 *property *trigger_all_source*: Any*

Select the trigger source for action â€˜ALLâ€™.

Type:

str; accepted values are exactly `AINT`, `BUS`, `TIM`, `INT1`, `INT2`, `LAN`, `TIN`, `EXT1` to `EXT7`

-

`AINT` lets internal algorithms choose the trigger source best matched to the present operating mode.

-

`BUS` uses a remote-interface trigger command, including the group execute trigger (GET) and the TRG command.

-

`TIM` uses an internally generated signal at each interval set by `trigger_all_timer`.

-

`INT1` and `INT2` use a signal from internal bus 1 or 2.

-

`LAN` uses the LXI trigger identified by `trigger_all_source_lan_id`.

-

`EXT1` to `EXT7` uses GPIO pin n on the rear-panel Digital I/O D-sub connector as an input port. n = 1 to 7.

-

`TIN` uses the BNC Trigger In.

 *property *trigger_all_source_lan_id*: Any*

Configure the LAN trigger source for action â€˜ALLâ€™.

Type:

str; allowed range is `LAN0` through `LAN7`

 *property *trigger_all_timer*: Any*

Set the trigger source timer interval for action â€˜ALLâ€™, in seconds.

Type:

-

float; allowed range is `1E-5` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *zero_corrected*: Any*

Enable or disable zero correction (bool).

 Class API: pymeasure.instruments.agilent.AgilentB2983; parameters: *adapter*, *name='Agilent/Keysight B2980A/B series'*, ***kwargs*.

Bases: `AgilentB2981`, `BatteryMixin`

Class wrapper for the Agilent/Keysight B2983A/B.

The B2983 model is a battery-operated Femto/Picoammeter.

 Class API: pymeasure.instruments.agilent.AgilentB2985; parameters: *adapter*, *name='Agilent/Keysight B2980A/B series'*, ***kwargs*.

Bases: `AgilentB2981`

Class wrapper for the Agilent/Keysight B2985A/B.

The B2985 model combines Femto/Picoammeter and Electrometer/High Resistance Meter functions.

 abort_transient()

Abort action ‘TRANSient’.

Return type:

`None`

 arm_transient()

Issue an immediate arm trigger for action â€˜TRANSientâ€™.

When the specified action reaches initiated status, the arm trigger moves execution from the arm layer to the trigger layer.

Return type:

`None`

 *property *arm_transient_bypass_once_enabled*: Any*

Enable or disable the event-detector bypass in the arm layer for action â€˜TRANSientâ€™ (bool).

 *property *arm_transient_count*: Any*

Configure the arm trigger count for action â€˜TRANSientâ€™.

Type:

-

int, strictly from `1` to `100000` or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `INF`

`INF` is equivalent to `2147483647`.

 *property *arm_transient_delay*: Any*

Configure the arm trigger delay for action â€˜TRANSientâ€™, in seconds.

Type:

-

float; allowed range is `0` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *arm_transient_output_enabled*: Any*

Enable or disable arm trigger output for action â€˜TRANSientâ€™ (bool).

Applies to the transition between the idle state and the arm layer.

 *property *arm_transient_output_signal*: Any*

Select the arm trigger output signal for action â€˜TRANSientâ€™.

Type:

str; accepted values are exactly `INT1`, `INT2`, `LAN`, `TOUT`, `EXT1` to `EXT7`

-

`INT1` and `INT2` choose internal bus 1 or 2.

-

`LAN` selects a LAN port.

-

`EXT1` to `EXT7` chooses GPIO pin n on the rear-panel Digital I/O D-sub connector as an output port. n = 1 to 7.

-

`TOUT` chooses the BNC Trigger Out.

Applies to the transition between the idle state and the arm layer.

 *property *arm_transient_source*: Any*

Select the arm trigger source for action â€˜TRANSientâ€™.

Type:

str; accepted values are exactly `AINT`, `BUS`, `TIM`, `INT1`, `INT2`, `LAN`, `TIN`, `EXT1` to `EXT7`

-

`AINT` lets internal algorithms choose the arm source best matched to the present operating mode.

-

`BUS` uses a remote-interface trigger command, including the group execute trigger (GET) and the TRG command.

-

`TIM` uses an internally generated signal at each interval set by `arm_transient_timer`.

-

`INT1` and `INT2` use a signal from internal bus 1 or 2.

-

`LAN` uses the LXI trigger identified by `arm_transient_source_lan_id`.

-

`EXT1` to `EXT7` uses GPIO pin n on the rear-panel Digital I/O D-sub connector as an input port. n = 1 to 7.

-

`TIN` uses the BNC Trigger In.

 *property *arm_transient_source_lan_id*: Any*

Configure the LAN arm-trigger source for action â€˜TRANSientâ€™.

Type:

str; allowed range is `LAN0` through `LAN7`

 *property *arm_transient_timer*: Any*

Set the arm trigger source timer interval for action â€˜TRANSientâ€™, in seconds.

Type:

-

float; allowed range is `1E-5` through `1E5`

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *charge*: Any*

Take a spot charge measurement in Coulombs.

Returns:

float

 *property *charge_range*: Any*

Configure the charge-measurement range in Coulombs.

Type:

-

float; allowed range is `2E-9` through `2E-6`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `UP`, `DOWN`

 *property *function*: Any*

Control the measurement function.

Type:

str; accepted values are exactly `CURR`, `CHAR`, `VOLT`, `RES`

 *property *humidity*: Any*

Measure relative humidity in percent.

Returns:

float

 init_transient()

Start a trigger for action â€˜TRANSientâ€™.

Return type:

`None`

 *property *resistance*: Any*

Take a spot resistance measurement in Ohms.

Returns:

float

 *property *resistance_range*: Any*

Configure the resistance-measurement range.

Type:

-

float; allowed range is `1E6` through `1E15`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `UP`, `DOWN`

 *property *source_enabled*: Any*

Configure the voltage source output relay (bool).

 *property *source_low_state*: Any*

Configure the voltage source low terminal state.

Type:

str, strictly `FLO` or `COMM`

-

`FLO`: low terminal is floating.

-

`COMM`: low terminal connects to Common.

 *property *source_off_state*: Any*

Configure the voltage source off condition.

Type:

str; accepted values are exactly `ZERO`, `HIZ`, `NORM`

| `HIGH Z` | - Output relay: off (open) - The voltage source setting remains unchanged. - This status is available only with the 20 V range. |
| --- | --- |
| `NORMAL` | - Output voltage: 0 V - Output relay: off (open) |
| `ZERO` | - Output voltage: 0 V in the active voltage range |

 *property *source_voltage*: Any*

Configure the source voltage in Volts.

Type:

float, strictly from `-1050` to `1050`

For voltages > 20V, the interlock must be closed.

| Range | Resolution | Output voltage | Maximum current |
| --- | --- | --- | --- |
| 20 V | 700 µV | -21 V ≤ V ≤ 21 V | +/-20 mA |
| 1000 V | 35 mV | -1 V ≤ V ≤ 1000 V | +/-1.0 mA |
| -1000 V | 35 mV | -1000 V ≤ V ≤ 1 V | +/-1.0 mA |

 *property *source_voltage_range*: Any*

Control the source voltage range.

Type:

-

float, strictly from `-1000` to `1000` or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *temperature*: Any*

Measure the temperature.

Returns:

float

The `temperature_unit` setting determines the temperature unit:

 *property *temperature_sensor*: Any*

Control the tempertature sensor.

Type:

str, strictly in `TC`, `HSEN`

-

`TC` selects the thermocouple.

-

`HSEN` chooses the temperature sensor inside the humidity sensor.

 *property *temperature_unit*: Any*

Control the tempertature unit.

Type:

str; accepted values are exactly `C`, `CEL`, `F`, `FAR`, `K`

-

`C`, `CEL` selects degree Celsius.

-

`F`, `FAR` selects degree Fahrenheit.

-

`K` selects Kelvin.

 *property *trigger_transient_bypass_once_enabled*: Any*

Enable or disable the event-detector bypass in the trigger layer for action â€˜TRANSientâ€™ (bool).

 *property *trigger_transient_count*: Any*

Configure the trigger count for action â€˜TRANSientâ€™.

Type:

-

int, strictly from `1` to `100000` or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `INF`

`INF` is equivalent to `2147483647`.

 *property *trigger_transient_delay*: Any*

Configure the trigger delay for action â€˜TRANSientâ€™, in seconds.

Type:

-

float; allowed range is `0` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *trigger_transient_is_idle*: Any*

Read whether action â€˜TRANSientâ€™ is idle (bool).

This command waits until the status becomes idle.

 *property *trigger_transient_output_enabled*: Any*

Enable or disable trigger output for action â€˜TRANSientâ€™ (bool).

Applies to the transition between the idle state and the trigger layer.

 *property *trigger_transient_output_signal*: Any*

Select the trigger signal output for action â€˜TRANSientâ€™.

Type:

str; accepted values are exactly `INT1`, `INT2`, `LAN`, `TOUT`, `EXT1` to `EXT7`

-

`INT1`, `INT2` choose internal bus 1 or 2.

-

`LAN` selects a LAN port.

-

`EXT1` to `EXT7` chooses GPIO pin n on the rear-panel Digital I/O D-sub connector as an output port. n = 1 to 7.

-

`TOUT` chooses the BNC Trigger Out.

Applies to the transition between the idle state and the trigger layer.

 *property *trigger_transient_source*: Any*

Select the trigger source for action â€˜TRANSientâ€™.

Type:

str; accepted values are exactly `AINT`, `BUS`, `TIM`, `INT1`, `INT2`, `LAN`, `TIN`, `EXT1` to `EXT7`

-

`AINT` lets internal algorithms choose the trigger source best matched to the present operating mode.

-

`BUS` uses a remote-interface trigger command, including the group execute trigger (GET) and the TRG command.

-

`TIM` uses an internally generated signal at each interval set by `trigger_transient_timer`.

-

`INT1` and `INT2` use a signal from internal bus 1 or 2.

-

`LAN` uses the LXI trigger identified by `trigger_transient_source_lan_id`.

-

`EXT1` to `EXT7` uses GPIO pin n on the rear-panel Digital I/O D-sub connector as an input port. n = 1 to 7.

-

`TIN` uses the BNC Trigger In.

 *property *trigger_transient_source_lan_id*: Any*

Configure the LAN trigger source for action â€˜TRANSientâ€™.

Type:

str; allowed range is `LAN0` through `LAN7`

 *property *trigger_transient_timer*: Any*

Set the trigger source timer interval for action â€˜TRANSientâ€™.

Type:

-

float; allowed range is `1E-5` through `1E5`, or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`

 *property *voltage*: Any*

Take a spot (one-shot) voltage measurement in Volts.

Returns:

float

 *property *voltage_range*: Any*

Configure the voltage-measurement range in Volts.

Type:

-

float, strictly from `2` to `20` or

-

str; accepted values are exactly `MIN`, `MAX`, `DEF`, `UP`, `DOWN`

 Class API: pymeasure.instruments.agilent.AgilentB2987; parameters: *adapter*, *name='Agilent/Keysight B2980A/B series'*, ***kwargs*.

Bases: `AgilentB2985`, `BatteryMixin`

Class wrapper for the Agilent/Keysight B2987A/B.

The B2987 model combines Femto/Picoammeter and Electrometer/High Resistance Meter functions with battery operation.

 *class *pymeasure.instruments.agilent.agilentB298x.BatteryMixin

Bases: `object`

Class wrapper for B2983/7 battery features.

 *property *battery_cycles*: Any*

Read the battery cycle count (int).

 *property *battery_level*: Any*

Read remaining battery capacity as a percentage (int).

 *property *battery_selftest_passed*: Any*

Read the battery self-test result (bool).

## Agilent 34410A Multimeter

### Agilent 34410A Multimeter

 Class API: pymeasure.instruments.agilent.Agilent34410A; parameters: *adapter*, *name='HP/Agilent/Keysight 34410A Multimeter'*, ***kwargs*.

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class support for the HP/Agilent/Keysight 34410A and related multimeters.

Implemented measurements: voltage_dc, voltage_ac, current_dc, current_ac, resistance, resistance_4w

 *property *current_ac*: Any*

Get AC current, in Amps

 *property *current_dc*: Any*

Get DC current, in Amps

 *property *resistance*: Any*

Get Resistance, in Ohms

 *property *resistance_4w*: Any*

Read Four-wires (remote sensing) resistance in Ohms.

 *property *voltage_ac*: Any*

Get AC voltage, in Volts

 *property *voltage_dc*: Any*

Get DC voltage, in Volts
