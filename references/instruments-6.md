# Anaheimautomation, Eurotest

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Anaheim Automation; DP-Series Step Motor Controller; EURO TEST; Euro Test HPP120256 High Voltage Power Supply.

## Anaheim Automation

### Anaheim Automation

This section documents the implemented Anaheim Automation instruments. For an instrument that is not listed here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [DP-Series Step Motor Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/anaheimautomation/dpseriesstepmotorcontroller.html)
  - [`DPSeriesMotorController`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anaheimautomation/dpseriesstepmotorcontroller.html#pymeasure.instruments.anaheimautomation.DPSeriesMotorController)

## DP-Series Step Motor Controller

### DP-Series Step Motor Controller

DPSeriesMotorController provides the base driver class for Anaheim-Automation DP Series stepper motor controllers. The series includes many controller models, and they share the same core command set. Certain controllers, including DPY50601, have extra capabilities outside this driver. Implement those capabilities in a subclass if you need them.

 *class *pymeasure.instruments.anaheimautomation.DPSeriesMotorController(*adapter*, *name='Anaheim Automation Stepper Motor Controller'*, *address=0*, *encoder_enabled=False*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Base class for communicating with Anaheim Automation DP series stepper motor controllers.

DPY50601 and DPE25601 motor controllers are the tested hardware for this driver.

 *property *absolute_position

Float property for the motor position value in absolute units. In DP series motor controller instrument manuals, 'absolute position' names the `step_position` property, not this property. This property also depends on subclass implementations of `steps_to_absolute()` and `absolute_to_steps()`. That lets the user choose how a motor step position maps into any desired absolute unit. For example, absolute units may be a linear stage position in meters, a gimbal mount angle, etc. This property is settable.

 absolute_to_steps(*pos*)

Convert an absolute position into a step count for the move. Subclasses must implement this.

Parameters:

**pos** - Absolute position, using the units selected by the subclassed `absolute_to_steps()` method.

 *property *address*: Any*

Integer property for the address used by the motor controller during serial communications.

 *property *basespeed*: Any*

Integer property for the motor controller's starting/homing speed. This property can be set.

 *property *busy*: Any*

Query whether the controller is moving a motor right now.

 check_errors()

Read the error codes register and write a log entry when an error is found.

Return error_code:

one byte containing the contents of the error codes register

 *property *direction*: Any*

String property for the direction the stepper motor uses on later step commands. This property can be set. 'CW' means clockwise rotation, and 'CCW' means counter-clockwise rotation.

 *property *encoder_autocorrect*: Any*

Boolean property that turns the encoder auto correct function on or off. This property can be set.

 *property *encoder_delay*: Any*

Integer property for the wait time in ms. after a move completes and before encoder reading for a possible encoder auto-correct action. This property can be set.

 *property *encoder_enabled

Boolean property indicating that `step_position` should come from a connected external encoder.

 *property *encoder_motor_ratio*: Any*

Integer property for the ratio: number of encoder pulses per motor step. This property can be set.

 *property *encoder_retries*: Any*

Integer property for how many encoder auto correct attempts the motor controller makes before it sets an error flag. This property can be set.

 *property *encoder_window*: Any*

Integer property setting the allowed encoder-pulse error relative to the target position before encoder auto-correct runs. This property can be set.

 *property *error_reg*: Any*

Read the current error codes register value.

 home(*home_mode*)

Send the motor controller the command that homes the motor.

Parameters:

**home_mode** –

`0` or `1`, choosing the homing mode to run.

Mode 0 runs homing by moving the motor until it reaches a soft limit; the controller then ramps down to base speed and keeps moving until it reaches a home limit.

In mode 1, the controller moves the motor until it reaches a limit, then ramps down to base speed, reverses direction, and runs until that limit is released.

 *property *maxspeed*: Any*

Integer property for the motor controller's maximum (running) speed. This property can be set.

 move(*direction*)

Move the stepper motor nonstop in the supplied direction until either a stop command is sent or a limit switch is reached. In the DP series instrument manuals, this is the 'slew' command.

Parameters:

**direction** - value assigned to the direction property before motor motion starts.

 reset_position()

Reset to 0 the position counted by both the motor controller and an externally connected encoder.

 *property *step_position

Integer property for motor position in steps. Steps are counted by the motor controller, or by an externally connected encoder when `encoder_enabled` is set. In DP series motor controller instrument manuals, this property is called the 'absolute position'; this driver instead converts between steps and absolute units through the `absolute_position` property. This property can be set.

 steps_to_absolute(*steps*)

Convert a step-measured position into an absolute position.

Parameters:

**steps** - Step position to convert into an absolute position.

 stop()

Stop all motion on the motor controller.

 wait_for_completion(*interval=0.5*)

Block while the controller remains "busy"; in other words, wait until the motor stops moving.

Parameters:

**interval** - (float) seconds to wait between queries of the "busy" flag. (default: `0.5`)

Returns:

None

 write(*command*)

Override the instrument base write method so the motor controller's address is added to the command string.

Parameters:

**command** - command string sent to the motor controller.

## EURO TEST

### EURO TEST

This section documents the implemented EURO TEST instruments. For an instrument not listed here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Euro Test HPP120256 High Voltage Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/eurotest/eurotestHPP120256.html)
  - [`EurotestHPP120256`](https://pymeasure.readthedocs.io/en/latest/api/instruments/eurotest/eurotestHPP120256.html#pymeasure.instruments.eurotest.EurotestHPP120256)

## Euro Test HPP120256 High Voltage Power Supply

### Euro Test HPP120256 High Voltage Power Supply

 *class *pymeasure.instruments.eurotest.EurotestHPP120256(*adapter*, *name='Euro Test High Voltage DC Source model HPP-120-256'*, *query_delay=0.1*, *write_delay=0.4*, *timeout=5000*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for the Euro Test High Voltage DC Source model HPP-120-256 using the Euro Test command set rather than the SCPI command set.

```python
hpp120256 = EurotestHPP120256("GPIB0::20::INSTR")

print(hpp120256.id)
print(hpp120256.lam_status)
print(hpp120256.status)

hpp120256.ramp_to_zero(100.0)

hpp120256.voltage_ramp = 50.0  # V/s
hpp120256.current_limit = 2.0  # mA
inst.kill_enabled = True  # Enable over-current protection
time.sleep(1.0)  # Give time to enable kill
inst.output_enabled = True
time.sleep(1.0)  # Give time to output on

abs_output_voltage_error = 0.02 # kV

hpp120256.wait_for_output_voltage_reached(abs_output_voltage_error, 1.0, 40.0)

# Here voltage HV output should be at 0.0 kV

print("Setting the output voltage to 1.0kV...")
hpp120256.voltage_setpoint = 1.0  # kV

# Now HV output should be rising to reach the 1.0kV at 50.0 V/s

hpp120256.wait_for_output_voltage_reached(abs_output_voltage_error, 1.0, 40.0)

# Here voltage HV output should be at 1.0 kV

hpp120256.shutdown()

hpp120256.wait_for_output_voltage_reached(abs_output_voltage_error, 1.0, 60.0)

# Here voltage HV output should be at 0.0 kV

inst.output_enabled = False

# Now the HV voltage source is in safe state

```

 *class *EurotestHPP120256Status(**values*)

Bases: `IntFlag`

Auxiliary class created to translate the instrument 16bits_status_string into an Enum_IntFlag, helping the user interpret that status.

 ask(*command*)

Override the Instrument ask method to include query_delay time in the parent call. :type command: :param command: Command string sent to the instrument. :returns: Device response string without read_termination.

 *property *current*: Any*

Measure actual output current in mAmps as a float.

 *property *current_limit*: Any*

Control the current limit in mAmps, with a float strictly from 0 to 25.

 *property *current_range*: Any*

Measure the actual output current range in mAmps as a float.

 emergency_off()

Switch the HV source output OFF permanently and set the voltage and current setting values to zero.

 *property *id*: Any*

Return the instrument identification (string).

 *property *kill_enabled*: Any*

Control the instrument kill enable state (boolean).

 *property *lam_status*: Any*

Return the instrument lam status (string).

 *property *output_enabled*: Any*

Control the instrument output enable state (boolean).

 ramp_to_zero(*voltage_rate=200.0*)

Set the voltage output setting to zero, and set the ramp setting from the voltage_rate parameter. In short, the method ramps the voltage output to zero at the specified voltage changing rate (ramp in V/s). :type voltage_rate: :param voltage_rate: changing rate (ramp in V/s) for the ramp setting (default: `200.0`)

 shutdown(*voltage_rate=200.0*)

Change the output voltage setting (V) to zero, and change the output-voltage ramp speed, voltage_rate (V/s). After shutdown is called, if the HV voltage output > 0, it should fall to zero at the rate given by the voltage_rate parameter. :type voltage_rate: :param voltage_rate: changing rate (V/s) for the voltage output (default: `200.0`)

 *property *status*: Any*

Return the instrument status (EurotestHPP120256Status).

 *property *voltage*: Any*

Measure actual output voltage in kVolts as a float.

 *property *voltage_ramp*: Any*

Control the voltage ramp in Volts/second, using an int strictly from 10 to 3000.

 *property *voltage_range*: Any*

Measure the actual output voltage range in kVolts as a float.

 *property *voltage_setpoint*: Any*

Control the voltage set-point in kVolts, with a float strictly from 0 to 12.

 wait_for_output_voltage_reached(*voltage_setpoint*, *abs_output_voltage_error=0.03*, *check_period=1.0*, *timeout=60.0*)

Wait until the HV voltage output reaches the voltage setpoint.

At each check_period-second interval, measure the voltage output; raise an exception if the voltage output does not reach the voltage setting before timeout expires. :type voltage_setpoint: :param voltage_setpoint: voltage in kVolts set in the HV power supply that should appear at the output after some time, depending on the ramp setting. :type abs_output_voltage_error: :param abs_output_voltage_error: absolute error in kVolts for considering the output voltage reached (default: `0.03`). :type check_period: :param check_period: period, in seconds, between voltage output measurements. (default: `1.0`) :type timeout: :param timeout: allowed duration, in seconds, for reaching the voltage setting at the output. (default: `60.0`) :return: None :raises: Exception when timeout finishes (seconds) before the voltage output reaches the voltage setting.

 write(*command*, ***kwargs*)

Override the Instrument write method so write_delay time is applied after the parent call.

Parameters:

**command** - command string sent to the instrument
