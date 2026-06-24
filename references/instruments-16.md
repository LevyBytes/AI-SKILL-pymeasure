# Aja, Ametek, Fwbell, Toptica ...

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Scope includes AJA DCXS-750 or 1500 DC magnetron sputtering power supply; vendor AJA International; instrument Ametek 7270 DSP Lockin Amplifier; vendor Ametek; vendor F.W. Bell; instrument F.W. Bell 5080 Handheld Gaussmeter; device Toptica IBeam Smart Laser diode; vendor Toptica; controller ESP 300 Motion Controller; vendor Newport.

## AJA DCXS-750 or 1500 DC magnetron sputtering power supply

### AJA DCXS-750 or 1500 DC magnetron sputtering power supply

 *class *pymeasure.instruments.aja.DCXS(*adapter*, *name='AJA DCXS sputtering power supply'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Reference for AJA DCXS-750 / 1500 hardware. This DC magnetron sputtering power supply exposes multiple outputs.

Communicate with the device over an RS232 serial connection. Its fixed communication settings are 38400, one stopbit, no parity. Protocol traffic uses one-character commands and fixed length replies, with no terminator on either side.

Parameters:

-

**adapter** – pyvisa resource name for the instrument, or an adapter instance

-

**name** (*string*) – Instrument name.

-

**kwargs** – Any key-word argument accepted by Instrument

 *property *active_gun*: Any*

Control the active gun number.

 ask(*command*, *query_delay=None*, ***kwargs*)

Send a command to the instrument, then read and return its response.

Parameters:

-

**command** – Command string to send to the instrument.

-

**query_delay** – Seconds to wait between the write and the read. (default: `None`)

-

****kwargs** – Keyword arguments forwarded to the read method.

Returns:

Device response string with read_termination removed.

 *property *current*: Any*

Read the output current, reported in mA.

 *property *deposition_time_min*: Any*

Set or read the minutes component of deposition time. Only writable when ‘enabled’ is False.

 *property *deposition_time_sec*: Any*

Set or read the seconds component of deposition time. Only writable when ‘enabled’ is False.

 *property *enabled*: Any*

Set or read whether the power supply is on or off.

 *property *fault_code*: Any*

Read the power supply error code.

 *property *id*: Any*

Read the type identifier reported by the power supply.

 *property *material*: Any*

Set or read the material name for the sputter target.

 *property *power*: Any*

Read the actual output power, reported in W.

 *property *ramp_time*: Any*

Set or read the ramp time in seconds. Only writable when ‘enabled’ is False.

 read(*reply_length=-1*, ***kwargs*)

Read either through read_termination, excluding it, or return the complete read buffer.

 *property *regulation_mode*: Any*

Set or read the power supply regulation mode.

 Property entry: *property *remaining_deposition_time_min*: Any*

Read the minutes component of the remaining deposition time.

 Property entry: *property *remaining_deposition_time_sec*: Any*

Read the seconds component of the remaining deposition time.

 *property *setpoint*: Any*

Set or read the setpoint value. The regulation mode determines the units: power -> W, voltage -> V, current -> mA.

 *property *shutter_delay*: Any*

Set or read the shutter delay in seconds. Only writable when ‘enabled’ is False.

 *property *shutter_state*: Any*

Read gun shutter status: 0 means closed, and 1 means open.

 *property *software_version*: Any*

Read the software revision for the power supply firmware.

 *property *voltage*: Any*

Read the output voltage, reported in V.

## AJA International

### AJA International

Documentation here focuses on the implemented AJA International instruments. For hardware that is not covered, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- Reference: [AJA DCXS-750 or 1500 DC magnetron sputtering power supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/aja/DCXS.html)
  - [`DCXS`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aja/DCXS.html#pymeasure.instruments.aja.DCXS)

## Ametek 7270 DSP Lockin Amplifier

### Ametek 7270 DSP Lockin Amplifier

 *class *pymeasure.instruments.ametek.Ametek7270(*adapter*, *name='Ametek DSP 7270'*, *read_termination='\x00'*, *write_termination='\x00'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class representing the Ametek DSP 7270 lockin amplifier.

For this instrument, certain measurements are available only in particular Reference modes; see `set_reference_mode()`. Calling them in the wrong mode raises errors.

 *property *adc1*: Any*

Read ADC1 input in Volts (float).

 *property *adc2*: Any*

Read ADC2 input in Volts (float).

 *property *adc3*: Any*

Read ADC3 input in Volts (float).

 *property *adc4*: Any*

Read ADC4 input in Volts (float).

 ask(*command*, *query_delay=None*)

Send a command, read the response, and strip whitespace.

Most properties rely on the [`values()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.values) method, which performs stripping. A few methods instead cast the direct ask result into other types, so stripping must happen here too because every response ends with a newline character.

 *property *auto_gain

Set or read the automatic gain enable state (bool).

 check_set_errors()

Required for use by a property setter.

The Ametek protocol requires reading the default null character to verify that the property was set successfully. When the termination character is the Null character, the default read result becomes an empty string.

 *property *dac1*: Any*

Set or read DAC1 output in Volts (float truncated to values from -10 to 10).

 *property *dac2*: Any*

Set or read DAC2 output in Volts (float truncated to values from -10 to 10).

 *property *dac3*: Any*

Set or read DAC3 output in Volts (float truncated to values from -10 to 10).

 *property *dac4*: Any*

Set or read DAC4 output in Volts (float truncated to values from -10 to 10).

 *property *frequency*: Any*

Set or read frequency for the lock-in in Hz (float, truncated_range; allowed values from 0 to 2.5e5).

 *property *harmonic*: Any*

Set/read reference harmonic mode (integer truncated to values from 1 to 127).

 *property *id

Read the instrument ID and firmware version.

 *property *mag*: Any*

Get magnitude in Volts (float).

 *property *phase*: Any*

Set or read harmonic reference phase, in degrees (float, modular_range; allowed values from 0 to 360).

 *property *sensitivity*: Any*

Set or read sensitivity range in Volts (float truncated to the interval from 2 nV to 1 V).(dynamic)

 set_channel_A_mode()

Configure channel A mode, assuming the instrument is in voltage mode.

 set_current_mode(*low_noise=False*)

Configure current control mode, selecting either low noise or high bandwidth.

 set_differential_mode(*lineFiltering=True*)

Configure differential mode, assuming the instrument is in voltage mode.

 set_reference_mode(*mode=0*)

Configure Single, Dual, or harmonic mode on the instrument.

Parameters:

**mode** (`int`) ? Integer mode selector: 0 means Single, 1 means Dual harmonic, and 2 means Dual reference. (default: `0`)

 set_voltage_mode()

Configure voltage control mode on the instrument.

 shutdown()

Place the instrument in a safe state.

 *property *slope*: Any*

Set or read filter slope in dB/octave (integer; truncated choices are 6, 12, 18, 24).

 *property *theta*: Any*

Read signal phase in degrees (float).

 *property *time_constant*: Any*

Set or read the time constant, in seconds (float truncated to the range 10 microseconds through 100,000 seconds).

 *property *voltage*: Any*

Set or read the voltage in Volts (float, truncated_range, values from 0 to 5).

 *property *x*: Any*

Read X in Volts (float).

 *property *x1*: Any*

Read first harmonic X in Volts (float).

 *property *x2*: Any*

Read second harmonic X in Volts (float).

 *property *xy*: Any*

Read both X and Y in Volts (float, tuple).

 *property *y*: Any*

Read Y in Volts (float).

 *property *y1*: Any*

Read first harmonic Y in Volts (float).

 *property *y2*: Any*

Read second harmonic Y in Volts (float).

## Ametek

### Ametek

Documentation here focuses on the implemented Ametek instruments. For hardware that is not covered, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Ametek 7270 DSP Lockin Amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/ametek/ametek7270.html)
  - [`Ametek7270`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ametek/ametek7270.html#pymeasure.instruments.ametek.Ametek7270)

## F.W. Bell

### F.W. Bell

Documentation here focuses on the implemented F.W. Bell instruments. For hardware that is not covered, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [F.W. Bell 5080 Handheld Gaussmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/fwbell/fwbell5080.html)
  - [`FWBell5080`](https://pymeasure.readthedocs.io/en/latest/api/instruments/fwbell/fwbell5080.html#pymeasure.instruments.fwbell.FWBell5080)

## F.W. Bell 5080 Handheld Gaussmeter

### F.W. Bell 5080 Handheld Gaussmeter

 *class *pymeasure.instruments.fwbell.FWBell5080(*adapter*, *name='F.W. Bell 5080 Handheld Gaussmeter'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model for the F.W. Bell 5080 Handheld Gaussmeter, exposing a high-level interface to the instrument.

Parameters:

**port** – Serial port connected to the instrument

```python
meter = FWBell5080('/dev/ttyUSB0')  # Connects over serial port /dev/ttyUSB0 (Linux)

meter.units = 'gauss'               # Sets the measurement units to Gauss
meter.range = 1                     # Sets the range to 3 kG
print(meter.field)                  # Reads and prints a field measurement in G

fields = meter.fields(100)          # Samples 100 field measurements
print(fields.mean(), fields.std())  # Prints the mean and standard deviation of the samples

```

 auto_range()

Enables the auto range functionality.

 check_errors()

Read every pending instrument error.

Returns:

List of error entries.

 check_get_errors()

After getting a property, check for errors and log them.

Invoked for a property when `check_get_errors=True` is set.

Override this method if specific errors should raise an Exception.

Returns:

`list` – List of error entries.

 check_set_errors()

After setting a property, check for errors and log them.

Invoked for a property when `check_set_errors=True` is set.

Override this method if specific errors should raise an Exception.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. The Operation Complete query adds an ASCII character 1 to the device’s Output Queue after all pending selected device operations finish.

 *property *field*: Any*

Read the field using the active units (float).

 fields(*samples=1*)

Return a numpy array containing the requested number of field samples.

Parameters:

**samples** – Number of samples to perform (default: `1`)

 *property *id*: Any*

Read the instrument identification.

 *property *next_error*: Any*

Read the next queued error. To read and log every error, use `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *range*: Any*

Set or read the maximum field range in the active units (int). The current units mode controls the range unit (gauss, tesla, amp-meter). The value selects an equivalent range across units with increasing magnitude (1, 10, 100).

| Value | gauss | tesla | amp-meter |
| --- | --- | --- | --- |
| 0 | 300 G | 30 mT | 23.88 kAm |
| 1 | 3 kG | 300 mT | 238.8 kAm |
| 2 | 30 kG | 3 T | 2388 kAm |

 read()

Overrides [`Instrument.read`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.read) so semicolons are removed and spaces become colons.

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Bytes to read. A value of -1 means read the entire read buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Resets the instrument.

 shutdown()

Put the instrument into a safe, stable state.

Return type:

`None`

 *property *status*: Any*

Read the status byte together with the Master Summary Status bit.

 *property *units*: Any*

Read the field units (str). The value can be one of ?gauss?, ?gauss ac?, ?tesla?, ?tesla ac?, ?amp-meter?, or ?amp-meter ac?. AC variants configure AC measurement.

 wait_for(*query_delay=None*)

Pause for a period of time. ‘ask’ uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. None selects the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values to transmit.

-

****kwargs** (**args**,*) – Additional arguments passed to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send bytes content to the instrument.

Return type:

`None`

## Toptica IBeam Smart Laser diode

### Toptica IBeam Smart Laser diode

 *class *pymeasure.instruments.toptica.ibeamsmart.IBeamSmart(*adapter*, *name='Toptica IBeam Smart laser diode'*, *baud_rate=115200*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

IBeam Smart laser diode

Consult the manual for how the diode driver channels are used.

```python
laser = IBeamSmart("SomeResourceString")
laser.emission = True
laser.ch_2.power = 1000  # µW
laser.ch_2.enabled = True
laser.shutdown()

```

Parameters:

-

**adapter** – pyvisa resource name, or an adapter instance.

-

**baud_rate** – Baud rate configured in the instrument. (default: `115200`)

-

****kwargs** – Any key-word argument accepted by VISAAdapter.

 ch_1

Channel:

`DriverChannel`

 ch_2

Channel:

`DriverChannel`

 ch_3

Channel:

`DriverChannel`

 ch_4

Channel:

`DriverChannel`

 ch_5

Channel:

`DriverChannel`

 check_set_errors()

After getting a property, check for errors and log them.

Verify that the last reply is only ‘[OK]’. Otherwise, raise ValueError and flush the read buffer because communication may be out of sync.

 *property *current*: Any*

Read the laser diode current in mA.

 disable()

Shutdown all laser operation.

 *property *emission*: Any*

Set or read the laser diode driver emission status (bool).

 enable_continous()

Enable countinous emission mode. :rtype: `None`

Deprecated since version 0.17.0: prefer `enable_continuous()`.

 enable_continuous()

Enable countinous emission mode.

Return type:

`None`

 enable_pulsing()

Enable pulsing mode.

A digital input signal on a dedicated connector controls the optical output.

 *property *power*: Any*

Set or read actual output power in µW for the laser system. In pulse mode, the set value may differ from the readback value (float up to 200000).

 read()

Read an instrument reply and extract values when possible.

Read an instrument reply containing at least two lines. Earlier lines hold the command response, while the final line should be ‘[OK]’, acknowledging that the device is ready for more commands.

Note: ‘[OK]’ is still the last message for an invalid command; in that case, an error message appears before the ‘[OK]’.

Value extraction: take <value> from ‘name = <value> [unit]’. If <value> cannot be identified, return the original string.

Returns:

ASCII response string from the instrument, excluding ‘[OK]’.

 *property *serial*: Any*

Read the Serial number of the laser system.

 shutdown()

Put the instrument into a safe and stable state.

 *property *system_temp*: Any*

Read base plate (heatsink) temperature in degree centigrade.

 *property *temp*: Any*

Read the laser diode temperature in degree centigrade.

 *property *version*: Any*

Get Firmware version number.

 *class *pymeasure.instruments.toptica.ibeamsmart.DriverChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Driver channel for the IBeam Smart laser diode.

 *property *enabled*: Any*

Set or read whether the driver channel is enabled.

 *property *power*: Any*

Set output power in µW (float up to 200000).

## Toptica

### Toptica

Documentation here focuses on the implemented Toptica Photonics instruments. For hardware that is not covered, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Toptica IBeam Smart Laser diode](https://pymeasure.readthedocs.io/en/latest/api/instruments/toptica/ibeamsmart.html)
  - [`IBeamSmart`](https://pymeasure.readthedocs.io/en/latest/api/instruments/toptica/ibeamsmart.html#pymeasure.instruments.toptica.ibeamsmart.IBeamSmart)
  - [`DriverChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/toptica/ibeamsmart.html#pymeasure.instruments.toptica.ibeamsmart.DriverChannel)

## ESP 300 Motion Controller

### ESP 300 Motion Controller

 *class *pymeasure.instruments.newport.ESP300(*adapter*, *name='Newport ESP 300 Motion Controller'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model for the Newport ESP 300 Motion Controller, providing a high-level interface to the instrument.

By default, construction creates x, y, and phi attributes for axes 1, 2, and 3. Custom implementations may override this for the axes they expose. Axes are managed through an `Axis` class.

 *property *axes

Return the available `Axis` objects as a list.

 clear_errors()

Clear error messages by checking until code 0 is received.

 disable()

Disable every axis associated with this controller.

 enable()

Enable every axis associated with this controller.

 *property *error*: Any*

Read an error code from the motion controller.

 *property *errors

Return error Exceptions for later raising or diagnostic use.

 shutdown()

Shut down the controller by disabling every axis.

 *class *pymeasure.instruments.newport.esp300.Axis(*axis*, *controller*)

Bases: `object`

Model for one axis of the Newport ESP300 Motor Controller, with parameters independent from other axes.

 define_position(*position*)

Replace the current position value with the supplied value.

 disable()

Disables motion for the axis.

 enable()

Enables motion for the axis.

 *property *enabled*: Any*

Return True when motion is enabled for this axis; otherwise return False.

 home(*type=1*)

Move the axis to home position, which for some actuators may be the negative hardware limit (e.g. LTA-HS). type accepts integer values from 0 to 6.

 *property *left_limit*: Any*

Floating point property for the axis left software limit.

 *property *motion_done*: Any*

Return True when motion has finished; otherwise return False.

 *property *position*: Any*

Floating point property for the axis position. Units depend on the actuator. Use `wait_for_stop()` to confirm the position is stable.

 *property *right_limit*: Any*

Floating point property for the axis right software limit.

 *property *units*: Any*

String property for axis displacement units. Supported length units include encoder count, motor step, millimeter, micrometer, inches, milli-inches, and micro-inches; angular units include degree, gradient, radian, milliradian, and microradian.

 wait_for_stop(*delay=0*, *interval=0.05*)

Block program execution until motion completes. An additional delay can be given in seconds.

 zero()

Set the current axis position as zero.

 *class *pymeasure.instruments.newport.esp300.AxisError(*code*)

Bases: `Exception`

Exception raised when a specific axis triggers a Newport ESP300 error.

 *class *pymeasure.instruments.newport.esp300.GeneralError(*code*)

Bases: `Exception`

Exception raised for a general Newport ESP300 error.

## Newport

### Newport

Documentation here focuses on the implemented Newport instruments. For hardware that is not covered, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [ESP 300 Motion Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/newport/esp300.html)
  - [`ESP300`](https://pymeasure.readthedocs.io/en/latest/api/instruments/newport/esp300.html#pymeasure.instruments.newport.ESP300)
  - [`Axis`](https://pymeasure.readthedocs.io/en/latest/api/instruments/newport/esp300.html#pymeasure.instruments.newport.esp300.Axis)
  - [`AxisError`](https://pymeasure.readthedocs.io/en/latest/api/instruments/newport/esp300.html#pymeasure.instruments.newport.esp300.AxisError)
  - [`GeneralError`](https://pymeasure.readthedocs.io/en/latest/api/instruments/newport/esp300.html#pymeasure.instruments.newport.esp300.GeneralError)
