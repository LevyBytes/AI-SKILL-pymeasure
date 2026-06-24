# Parker, Ami, Bkprecision, Proterial ...

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Parker GV6 Servo Motor Controller; Parker; AMI; AMI 430 Power Supply; BK Precision; BK Precision 9130B DC Power Supply; Proterial; ROD-4 MFC Controller; Attocube; Attocube ANC300 Motion Controller; Generic Instrument Types Mixins.

## Parker GV6 Servo Motor Controller

### Parker GV6 Servo Motor Controller

 *class *pymeasure.instruments.parker.ParkerGV6(*adapter*, *name='Parker GV6 Motor Controller'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for the Parker Gemini GV6 Servo Motor Controller instrument.

 *property *acceleration

Configure the acceleration setpoint, expressed in revolutions per second squared.

 *property *angle

Set the angle target in degrees, using the current position mode and the relative or absolute positioning setting.

 *property *angle_error

Report the angular error in degrees from the position error; return None if the query fails.

 *property *average_acceleration

Configure the average acceleration setpoint, expressed in revolutions per second squared.

 disable()

Disables the motor from moving

 *property *echo

Enable or disable command echoing for every command sent to the instrument (bool).

 enable()

Enables the motor to move

 is_moving()

Return True when the motor is in motion.

 kill()

Stop the motor

 move()

Start motor motion toward the configured setpoint.

 *property *position

Control angular position as counts, with 4000 counts per revolution (int).

 *property *position_error

Return the position error as counts, using 4000 counts for 1 revolution.

 read()

Override Instrument.read so reads use the required device behavior.

 reset()

Reset the motor controller in a blocking operation; CAUTION: this also resets the motor absolute position value.

 set_defaults()

Initialize the motor defaults during construction.

 set_hardware_limits(*positive=True*, *negative=True*)

Turn the motor hardware limits on (True) or off (False).

 set_software_limits(*positive*, *negative*)

Configure software motion limits in count units, where 4000 counts equal 1 revolution.

 *property *status

Return the motor status values as a readable list.

 stop()

Stop the motor during movement

 use_absolute_position()

Configure the motor so setpoints are interpreted from an absolute zero position.

 use_relative_position()

Configure the motor so setpoints are interpreted relative to the previous position.

 *property *velocity

Configure the velocity setpoint, expressed in revolutions per second.

## Parker

### Parker

Documentation for implemented Parker instruments is collected in this section. For a missing instrument, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Parker GV6 Servo Motor Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/parker/parkerGV6.html)
  - [`ParkerGV6`](https://pymeasure.readthedocs.io/en/latest/api/instruments/parker/parkerGV6.html#pymeasure.instruments.parker.ParkerGV6)

## AMI

### AMI

Documentation for implemented AMI instruments is collected in this section. For a missing instrument, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [AMI 430 Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/ami/ami430.html)
  - [`AMI430`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ami/ami430.html#pymeasure.instruments.ami.AMI430)

## AMI 430 Power Supply

### AMI 430 Power Supply

 *class *pymeasure.instruments.ami.AMI430(*adapter*, *name='AMI superconducting magnet power supply.'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for interacting with the AMI 430 Power supply.

```python
magnet = AMI430("TCPIP::web.address.com::7180::SOCKET")

magnet.coilconst = 1.182                 # kGauss/A
magnet.voltage_limit = 2.2               # Sets the voltage limit in V

magnet.target_current = 10               # Sets the target current to 10 A
magnet.target_field = 1                  # Sets target field to 1 kGauss

magnet.ramp_rate_current = 0.0357       # Sets the ramp rate in A/s
magnet.ramp_rate_field = 0.0422         # Sets the ramp rate in kGauss/s
magnet.ramp                             # Initiates the ramping
magnet.pause                            # Pauses the ramping
magnet.status                           # Returns the status of the magnet

magnet.ramp_to_current(5)             # Ramps the current to 5 A

magnet.shutdown()                     # Ramps the current to zero and disables output

```

 *property *coilconst*: Any*

Control the coil constant, in kGauss/A. (float)

 disable_persistent_switch()

Disables the persistent switch.

 enable_persistent_switch()

Enables the persistent switch.

 *property *field*: Any*

Read the magnet field in kGauss.

 has_persistent_switch_enabled()

Return a boolean indicating whether the persistent switch is enabled.

 *property *magnet_current*: Any*

Read the magnet current in Amps.

 *property *magnet_status

Get the magnet status.

 pause()

Pause magnetic-field ramping.

 ramp()

Begin ramping the magnetic field toward the configured current/field by using the previously set ramping rate.

 *property *ramp_rate_current*: Any*

Set the current ramping rate in A/s. (float)

 *property *ramp_rate_field*: Any*

Set the field ramping rate in kGauss/s. (float)

 ramp_to_current(*current*, *rate*)

Heat the persistent switch, then ramp the current at the configured ramp rate.

 ramp_to_field(*field*, *rate*)

Warm the persistent switch and ramp current using the configured ramp rate.

 shutdown(*ramp_rate=0.0357*)

Enable the persistent switch, ramp current down to zero, then disable the persistent switch.

 *property *state*: Any*

Read the magnet field in kGauss.

 *property *supply_current*: Any*

Read the power-supply current in Amps.

 *property *target_current*: Any*

Set the magnet target current in A. (float)

 *property *target_field*: Any*

Set the magnet target field in kGauss. (float)

 *property *voltage_limit*: Any*

Configure the voltage limit used while charging/discharging the magnet. (float)

 wait_for_holding(*should_stop=<function AMI430.<lambda>>*, *timeout=800*, *interval=0.1*)

 zero()

Begin ramping the magnetic field down to zero current/field, using the previously set ramping rate.

## BK Precision

### BK Precision

Documentation for implemented BK Precision instruments is collected in this section. For a missing instrument, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [BK Precision 9130B DC Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/bkprecision/bkprecision9130b.html)
  - [`BKPrecision9130B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/bkprecision/bkprecision9130b.html#pymeasure.instruments.bkprecision.BKPrecision9130B)

## BK Precision 9130B DC Power Supply

### BK Precision 9130B DC Power Supply

 *class *pymeasure.instruments.bkprecision.BKPrecision9130B(*adapter*, *name='BK Precision 9130B Source'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents the BK Precision 9130B DC Power Supply interface for controlling the instrument.

 *property *channel*: Any*

Select the active channel. Accepted values are [1, 2, 3]. (int)

 *property *current*: Any*

Set the selected channel current. (float)

 *property *source_enabled*: Any*

Enable or disable the source. (bool)

 *property *voltage

Set the selected channel voltage. (float)

## Proterial

### Proterial

Documentation for implemented Proterial (formerly Hitachi Metals) instruments is collected in this section. For a missing instrument, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [ROD-4 MFC Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/proterial/rod4.html)
  - [`ROD4`](https://pymeasure.readthedocs.io/en/latest/api/instruments/proterial/rod4.html#pymeasure.instruments.proterial.ROD4)
  - [`ROD4Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/proterial/rod4.html#pymeasure.instruments.proterial.rod4.ROD4Channel)

## ROD-4 MFC Controller

### ROD-4 MFC Controller

 *class *pymeasure.instruments.proterial.ROD4(*adapter*, *name='ROD-4 MFC Controller'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for the Proterial ROD-4(A) operator for mass flow controllers. The user must choose the channel to control (1-4).

```python
rod4 = ROD4("ASRL1::INSTR")

print(rod4.version)             # Print version and series number
rod4.ch_1.mfc_range = 500       # Sets Channel 1 MFC range to 500 sccm
rod4.ch_2.valve_mode = 'flow'   # Sets Channel 2 MFC to flow control
rod4.ch_3.setpoint = 50         # Sets Channel 3 MFC to flow at 50% of full range
print(rod4.ch_4.actual_flow)    # Prints Channel 4 actual MFC flow in %

```

 ch_1

Channel:

`ROD4Channel`

 ch_2

Channel:

`ROD4Channel`

 ch_3

Channel:

`ROD4Channel`

 ch_4

Channel:

`ROD4Channel`

 check_errors()

Read every instrument error and write each one to the log.

Returns:

`list` – List of error entries.

 check_get_errors()

After reading a property, check for errors and log any findings.

This is called when `check_get_errors=True` is configured on that property.

Override this method if some errors should raise an Exception.

Returns:

`list` – List of error entries.

 check_set_errors()

Read `OK` from ROD-4 after a setting operation.

 clear()

Clears the instrument status byte

Return type:

`None`

 *property *complete

Get the synchronization bit.

Use this property to synchronize a controller with a device. Once all selected pending operations finish, the Operation Complete query queues ASCII character 1 in the device Output Queue.

 *property *id

Read the instrument identification.

 *property *keyboard_locked*: Any*

Configure the front keyboard lock state.

 *property *next_error

Read the next instrument error as a tuple containing code and message.

 *property *options

Get the device options installed.

 read(***kwargs*)

Read until just before read_termination, or consume the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) - Number of bytes to read. Use -1 to consume the complete read buffer.

-

**kwargs** - Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Resets the instrument.

Return type:

`None`

 shutdown()

Put the instrument into a stable safe state.

Return type:

`None`

 *property *status

Read the status byte along with the Master Summary Status bit.

 *property *version*: Any*

Read the version and series number. Response format is x.xx<TAB>S/N

 wait_for(*query_delay=None*)

Pause briefly; `ask` uses this delay before it reads.

Parameters:

**query_delay** (`Optional`[`float`]) - Delay between write and read operations in seconds. None selects the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, appending write_termination.

Parameters:

-

**command** (`str`) - command string sent to the instrument

-

**kwargs** - Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) - Values to transmit.

-

****kwargs** (**args**,*) - Additional arguments passed through to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send the bytes content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.proterial.rod4.ROD4Channel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Implements one ROD-4 MFC channel.

 *property *actual_flow*: Any*

Measure the actual flow in %.

 *property *flow_unit_display*: Any*

Set flow units for the front display. Valid options are %, sccm, or slm. When absolute units are shown, sccm is used for control range < 10 slm.

 *property *mfc_range*: Any*

Configure the MFC range in sccm. The upper limit is 200 slm.

 *property *ramp_time*: Any*

Configure MFC setpoint ramping time in seconds.

 *property *setpoint*: Any*

Set the setpoint as % of MFC range.

 *property *valve_mode*: Any*

Set the MFC valve mode. Valid options are flow, close, and open.

## Attocube

### Attocube

Documentation for implemented Attocube instruments is collected in this section. For a missing instrument, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Attocube ANC300 Motion Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/attocube/anc300.html)
  - [`ANC300Controller`](https://pymeasure.readthedocs.io/en/latest/api/instruments/attocube/anc300.html#pymeasure.instruments.attocube.anc300.ANC300Controller)
  - [`Axis`](https://pymeasure.readthedocs.io/en/latest/api/instruments/attocube/anc300.html#pymeasure.instruments.attocube.anc300.Axis)

## Attocube ANC300 Motion Controller

### Attocube ANC300 Motion Controller

 *class *pymeasure.instruments.attocube.anc300.ANC300Controller(*adapter=None*, *name='attocube ANC300 Piezo Controller'*, *axisnames=''*, *passwd=''*, *query_delay=0.05*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Attocube ANC300 Piezo stage controller supporting multiple axes

Parameters:

-

**adapter** - VISA resource name for the controller, such as `TCPIP::<address>::<port>::SOCKET`, or an existing Adapter. The instruments default communication port is 7230. (default: `None`)

-

**axisnames** - list of axis names used to create properties with matching names (default: `''`)

-

**passwd** - password for the attocube standard console (default: `''`)

-

**query_delay** - default delay in s between sending and reading (default 0.05) (default: `0.05`)

-

**host** –

Instrument host address, for example 169.254.0.1

Deprecated since version 0.11.2: The `host` argument is deprecated; use the `adapter` argument instead.

-

**kwargs** - Any valid VISAAdapter key-word argument.

 check_set_errors()

After setting a property, check for errors and log any findings.

This is called when `check_set_errors=True` is configured on that property.

Returns:

List of error entries.

 *property *controllerBoardVersion*: Any*

Read the controller board serial number.

 ground_all()

Ground every controller axis.

 handle_deprecated_host_arg(*adapter*, *kwargs*)

Normalizes user input for __init__ so it matches the current __init__ signature. It exists to keep outdated (deprecated) code working and is isolated so future removal is simpler. Removal note: delete this function and make the adapter argument in __init__ non-optional.

Parameters:

**kwargs** (*dict*) - keyword arguments passed into __init__, including the deprecated host argument.

Return str:

resource string for the VISAAdapter

 read()

Read after setting a value.

 stop_all()

Stop movement on all axes.

 *property *version*: Any*

Read the version number and instrument identification.

 wait_for(*query_delay=None*)

Pause briefly; `ask` uses this delay before it reads.

Parameters:

**query_delay** - Delay between writing and reading in seconds. None uses `query_delay`. (default: `None`)

 *class *pymeasure.instruments.attocube.anc300.Axis(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Models a single open loop axis of the Attocube ANC350.

Parameters:

-

**axis** - axis identifier; integer from 1 to 7

-

**controller** - ANC300Controller instance used for communication

 *property *capacity*: Any*

Measure the axis saved capacity value in nF.

 *property *frequency*: Any*

Set stepping-motion frequency in Hertz from 1 to 10000 Hz.

 insert_id(*command*)

Insert the channel id into a command by replacing the placeholder.

Place the axis id into a command string after the initial command and before any value.

 measure_capacity()

Take a fresh capacity measurement. After measurement, the axis mode returns to `gnd`.

Returns capacity:

Freshly measured capacity, in nF.

 *property *mode*: Any*

Set axis mode. Valid values include `gnd`, `inp`, `cap`, `stp`, `off`, `stp+`, and `stp-`; the actual axis model determines which modes are available.

 move(*steps*, *gnd=True*)

Move `steps` steps in the direction indicated by the argument sign. The method automatically changes axis mode and, when `gnd` is True, grounds the axis at the end. It blocks until motion is complete.

Parameters:

-

**steps** - finite integer number of steps to perform. Positive values mean upward steps; negative values mean downward steps.

-

**gnd** - bool flag selecting whether the axis is grounded after movement completes (default: `True`)

 move_raw(*steps*)

Move `steps` steps according to the argument sign. This non-blocking method assumes the axis mode is already `stp` and returns immediately after sending the command.

Parameters:

**steps** - integer number of steps to perform. Positive values mean upward steps; negative values mean downward steps. +/-inf starts continuous movement, and stop can halt the axis.

 *property *offset_voltage*: Any*

Set offset voltage in Volts from 0 to 150 V.

 *property *output_voltage*: Any*

Measure output voltage in volts.

 *property *pattern_down*: Any*

Set the piezo drive step down pattern. It consists of 256 values from 0 to 255 that define the output-voltage sequence within one piezo-drive step; the set value must be an array of 256 integer values.

 *property *pattern_up*: Any*

Set the piezo drive step up pattern. It consists of 256 values from 0 to 255 that define the output-voltage sequence within one piezo-drive step; the set value must be an array of 256 integer values.

 *property *serial_nr*: Any*

Read the axis serial number.

 *property *stepd*: Any*

Command N downward steps. Use mode `stp`; N must be positive. A value of 0 starts continuous movement and continues until stop is called.

Deprecated since version 0.13.0: Use meth:move_raw in new code.

 *property *stepu*: Any*

Command N upward steps. Use mode `stp`; N must be positive. A value of 0 starts continuous movement and continues until stop is called.

Deprecated since version 0.13.0: Use meth:move_raw in new code.

 stop()

Stop any axis motion.

 *property *voltage*: Any*

Set stepping-voltage amplitude in volts from 0 to 150 V.

## Generic Instrument Types Mixins

### Generic Instrument Types Mixins

Use these Mixins as additional parent classes on an instrument. For details, see [Common instrument types](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#common-instrument-types).

 *class *pymeasure.instruments.generic_types.SCPIMixin(**args*, ***kwargs*)

Mixin class that supplies default base SCPI command implementations for SCPI instruments.

 check_errors()

Read every error from the instrument.

Returns:

List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to synchronize a controller with a device. Once all selected pending operations finish, the Operation Complete query queues ASCII character 1 in the device Output Queue.

 *property *id*: Any*

Read the instrument identification.

 *property *next_error*: Any*

Read the next queued error. To read and log all errors, use `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 reset()

Reset the instrument.

 *property *status*: Any*

Read the status byte along with the Master Summary Status bit.
