# Thyracont, Ilxlightwave, Racal

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Smartline V2 Transmitter Series; Thyracont; Smartline V1 Transmitter Series; ILX Lighwave LDP3811; ILX Lightwave; Racal-Dana 1992 Universal Counter; Racal-Dana.

## Smartline V2 Transmitter Series

### Smartline V2 Transmitter Series

 *class *pymeasure.instruments.thyracont.smartline_v2.SmartlineV2(*adapter*, *name='Thyracont SmartlineV2 Transmitter'*, *baud_rate=115200*, *address=1*, *timeout=250*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

A Smartline V2 series Thyracont transmitter for vacuum sensor measurements.

Subclass this Instrument and add the needed channels; the example below shows the pattern.

```pycon
from pymeasure.instruments import Instrument
from pymeasure.instruments.thyractont import SmartlineV2

PiezoAndPiraniInstrument(SmartlineV2):
    piezo = Instrument.ChannelCreator(Piezo)
    pirani = Instrument.ChannelCreator(Pirani)

```

Communication Protocol v2 via RS485:

-

Communication payloads use ASCII characters throughout.

-

Package (bytes and usage):

  -

0-2 address, 3 access code, 4-5 command, 6-7 data length.

  -

if data: 8-n contain payload data, n+1 checksum, n+2 carriage return

  -

if no data: 8 contains checksum, 9 carriage return

-

Access codes (request: master->transmitter, response: transmitter->master):

  -

read: 0, 1

  -

write: 2, 3

  -

factory default: 4,5

  -

error: -, 7

  -

binary 8, 9

-

Data length is the byte count of the data, left padded with zeroes

-

Checksum: Sum the preceding characters as decimal numbers, apply mod 64, add 64, and emit the ASCII character.

Parameters:

**adress** – Device address, valid from 1-16.

 *class *Sources(**values*)

Bases: `IntEnum`

 *property *analog_output_setting*: Any*

Get current analog output setting. See manual.

 ask(*command_message*, *query_delay=None*)

Request a value, then verify that the reply corresponds to the command originally sent.

Parameters:

**command_message** (*str*) – Access code, command, length, and content; the transmitted command is checked against the response command.

 ask_manually(*accessCode*, *command*, *data=''*, *query_delay=None*)

Transmit a message to the transmitter and return the reply.

Parameters:

-

**accessCode** – Access method for the device.

-

**command** – Command that will be sent to the device.

-

**data** – Command data. (default: `''`)

-

**query_delay** (*float*) – Seconds to pause after writing before reading.

Return str:

Device response after error checks have completed.

 *property *baud_rate*: Any*

Set the device baud rate.

 *property *bootloader_version*: Any*

Get the bootloader version.

 check_set_errors()

Run error checking after a property has been set.

 *property *device_address*: Any*

Set the device address.

 *property *device_serial*: Any*

Read the transmitter device serial number.

 *property *device_type*: Any*

Read the device type, for example ‘VSR205’.

 *property *device_version*: Any*

Get the device hardware version.

 *property *display_data*: Any*

Select the display data source (strict SOURCES).

 *property *display_orientation*: Any*

Set the display orientation relative to the pipe (‘top’, ‘bottom’).

 *property *display_unit*: Any*

Choose among ‘mbar’, ‘Torr’, and ‘hPa’ for the display unit.

 *property *firmware_version*: Any*

Get the firmware version.

 get_sensor_transition()

Read the active sensor transition between sensors.

return interpretation:

-

direct

switch at 1 mbar.

-

continuous

switch between 5 and 15 mbar.

-

F[float]T[float]

switch between the low value and the high value.

-

D[float]

switch at value.

 *property *operating_hours*: Any*

Measure the operating hours.

 *property *pressure*: Any*

Read the current pressure from the default sensor in mbar

 *property *product_name*: Any*

Read the product name (article number).

 *property *range*: Any*

Read the measurement range in mbar.

 read(*command=None*)

Read data from the device and perform error checking.

Parameters:

**command** (*str*) – Original command sent to the device for comparison with the response. None disables this check.

 *property *sensor_serial*: Any*

Read the sensor head serial number.

 set_continuous_sensor_transition(*low*, *high*)

Configure the sensor transition mode as “continuous” between low and high (floats).

 set_default_sensor_transition()

Configure the senstor transition mode to the device-dependent default value.

 set_direct_sensor_transition(*transition_point*)

Configure the sensor transition for “direct” mode.

Parameters:

**transition_point** (*float*) – Value where the sensor switch occurs.

 set_high(*high=''*)

Set the high pressure endpoint in mbar.

 set_low(*low=''*)

Set the low pressure endpoint in mbar.

 write(*command*)

Send a command to the device.

 write_composition(*accessCode*, *command*, *data=''*)

Send a command to the device using an accessCode plus optional data.

Parameters:

-

**accessCode** – Access method for the device.

-

**command** – Two char command string for the device.

-

**data** – Command data. (default: `''`)

 *class *pymeasure.instruments.thyracont.smartline_v2.VSH(*adapter*, *name='Thyracont SmartlineV2 Transmitter'*, *baud_rate=115200*, *address=1*, *timeout=250*, ***kwargs*)

Bases: `SmartlineV2`

VSH series vacuum transmitter combining a pirani sensor and a hot cathode sensor.

 hotcathode

Channel:

`HotCathode`

 pirani

Channel:

`Pirani`

 *class *pymeasure.instruments.thyracont.smartline_v2.VSM(*adapter*, *name='Thyracont SmartlineV2 Transmitter'*, *baud_rate=115200*, *address=1*, *timeout=250*, ***kwargs*)

Bases: `SmartlineV2`

VSM series vacuum transmitter with both piece and cold cathode sensor.

 coldcathode

Channel:

`ColdCathode`

 piezo

Channel:

`Piezo`

 *class *pymeasure.instruments.thyracont.smartline_v2.VSP(*adapter*, *name='Thyracont SmartlineV2 Transmitter'*, *baud_rate=115200*, *address=1*, *timeout=250*, ***kwargs*)

Bases: `SmartlineV2`

VSP/VCP series vacuum transmitter with a piezo sensor.

 piezo

Channel:

`Piezo`

 *class *pymeasure.instruments.thyracont.smartline_v2.VSR(*adapter*, *name='Thyracont SmartlineV2 Transmitter'*, *baud_rate=115200*, *address=1*, *timeout=250*, ***kwargs*)

Bases: `SmartlineV2`

VSR/VCR series vacuum transmitter combining a piezo sensor and a pirani sensor.

 piezo

Channel:

`Piezo`

 pirani

Channel:

`Pirani`

## Thyracont

### Thyracont

This section documents the implemented Thyracont instruments. For an instrument that is not covered here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Smartline V1 Transmitter Series](https://pymeasure.readthedocs.io/en/latest/api/instruments/thyracont/smartline_v1.html)
  - [`SmartlineV1`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thyracont/smartline_v1.html#pymeasure.instruments.thyracont.smartline_v1.SmartlineV1)

- [Smartline V2 Transmitter Series](https://pymeasure.readthedocs.io/en/latest/api/instruments/thyracont/smartline_v2.html)
  - [`SmartlineV2`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thyracont/smartline_v2.html#pymeasure.instruments.thyracont.smartline_v2.SmartlineV2)
  - [`VSH`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thyracont/smartline_v2.html#pymeasure.instruments.thyracont.smartline_v2.VSH)
  - [`VSM`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thyracont/smartline_v2.html#pymeasure.instruments.thyracont.smartline_v2.VSM)
  - [`VSP`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thyracont/smartline_v2.html#pymeasure.instruments.thyracont.smartline_v2.VSP)
  - [`VSR`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thyracont/smartline_v2.html#pymeasure.instruments.thyracont.smartline_v2.VSR)

## Smartline V1 Transmitter Series

### Smartline V1 Transmitter Series

 *class *pymeasure.instruments.thyracont.smartline_v1.SmartlineV1(*adapter*, *name='Thyracont Vacuum Gauge V1'*, *address=1*, *baud_rate=9600*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Thyracont Vacuum Instruments Smartline gauges that use Communication Protocol V1.

Protocol V1 applies to devices manufactured until 2017.

The device connection uses RS485 serial communication. By default it communicates at baudrate 9600 with 8 data bits, 1 stop bit, no parity, and no handshake.

A communication package is organized as follows:

Characters 0-2: Communication address Character 3: Command character; uppercase letters read and lowercase letters write Characters 4-n: Command data, possibly empty. Character n+1: Checksum; sum decimal values for bytes 0-n, then use mod 64 + 64 Character n+2: Carriage return

Parameters:

-

**adapter** – pyvisa resource name for the instrument, or an adapter instance

-

**name** (*string*) – Instrument name.

-

**address** (*int*) – RS485 adddress for the instrument, 1-15.

-

**baud_rate** (*int*) – baudrate used when communicating with the device.

-

**kwargs** – Any key-word argument accepted by Instrument

 *property *cathode_enabled*: Any*

Set or read the pressure gauge hot/cold cathode state.

 check_set_errors()

After setting a property, check for errors and log them.

Invoked when `check_set_errors=True` is configured for that property.

Override this method if selected errors should raise an Exception.

Returns:

List of error entries.

 *property *device_type*: Any*

Get the device type.

 *property *display_unit*: Any*

Set or read the display’s pressure unit.

 *property *pressure*: Any*

Return the pressure measurement in mbar.

 read()

Read one response message from the instrument.

The method verifies that the checksum is correct as well.

Returns:

the data fields

Return type:

string

Raises:

**ValueError** – raised when a checksum error is found

 write(*command*)

Send a command to the instrument.

The method attaches the required address and checksum.

Parameters:

**command** (*str*) – command sent to the instrument

## ILX Lighwave LDP3811

### ILX Lighwave LDP3811

 *class *pymeasure.instruments.ilxlightwave.LDP3811(*adapter*, *name='ILX Lightwave LDP 3811'*, *includeSCPI=False*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents the ILX Lightwave LDP3811 Pulsed Laser Diode Driver, exposing a high-level interface for instrument interaction.

 check_errors()

Read every instrument error and log the entries.

Returns:

`list`[`Union`[`float`, `str`]] – Error entries as a list.

 check_get_errors()

After getting a property, check for errors and log them.

Invoked when `check_get_errors=True` is configured for that property.

Override this method if selected errors should raise an Exception.

Returns:

`list` – List of error entries.

 check_set_errors()

After setting a property, check for errors and log them.

Invoked when `check_set_errors=True` is configured for that property.

Override this method if selected errors should raise an Exception.

Returns:

`list` – List of error entries.

 clear()

Clears the instrument status byte

Return type:

`None`

 *property *complete

Get the synchronization bit.

Use this property to synchronize a controller with a device. An Operation Complete query puts ASCII character 1 in the device’s Output Queue once all pending selected device operations are complete.

 *property *current*: Any*

Measure current in mA (float).

 *property *current_limit_200*: Any*

For the 200mA range, set or read the current limit in mA (float, strictly in range 0 to 200).

 *property *current_limit_500*: Any*

For the 500mA range, set or read the current limit in mA (float, strictly in range 0 to 500).

 *property *current_range_500_enabled*: Any*

Enable or disable the 500mA output current range (bool). When False, the 200mA output current range is used.

 *property *current_setpoint

For the current setpoint, set or read the value in mA (float); permitted span is 0 to (`current_limit_500` if `current_range_500_enabled` else `current_limit_200`).

 *property *duty_cycle*: Any*

Measure duty cycle (pulse width / pulse repetition interval), expressed as a percentage (float).

 *property *duty_cycle_setpoint

Set or read the duty cycle percentage for pulse width / pulse repetition interval (float, strictly in range (100 * `pulse_width` / 6500) to 100).

 *property *id

Read the instrument identification.

 *property *mode*: Any*

Set or read the mode as an `LDP3811Mode` enum.

 *property *next_error

Read the instrument’s next error (tuple of code and message).

 *property *options

Get the device options installed.

 *property *output_enabled*: Any*

Enable or disable current output (bool).

 *property *pulse_repetition_interval*: Any*

Measure pulse repetition interval, in us (float).

 *property *pulse_repetition_interval_setpoint

Set or read the pulse repetition interval in us; value is a float, strictly in range max(1, `pulse_width`) to 6500.

 *property *pulse_width*: Any*

Measure pulse width, in us (float).

 *property *pulse_width_setpoint

Set or read pulse width, in us (float strictly in range 0.1 to `pulse_repetition_interval`.

 read(***kwargs*)

Read until read_termination, excluding it, or return the entire read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Bytes to read. The value -1 means read the entire read buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Resets the instrument.

Return type:

`None`

 set_to_max_duty_cycle()

Use the present mode, pulse width, and pulse repetition interval to set the largest valid duty cycle, then return that duty cycle.

 set_to_min_duty_cycle()

Use the present mode, pulse width, and pulse repetition interval to set the smallest valid duty cycle, then return that duty cycle.

 shutdown()

Put the instrument into a safe, stable state

Return type:

`None`

 *property *status

Read the status byte and the Master Summary Status bit.

 wait_for(*query_delay=None*)

Pause briefly; ‘ask’ relies on this delay before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Delay between writing and reading, in seconds. None uses the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, appending write_termination.

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

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

-

****kwargs** (**args**,*) – Additional arguments to pass to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send the bytes content to the instrument.

Return type:

`None`

## ILX Lightwave

### ILX Lightwave

This section documents the implemented ILX Lightwave instruments. For an instrument that is not covered here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [ILX Lighwave LDP3811](https://pymeasure.readthedocs.io/en/latest/api/instruments/ilxlightwave/ldp3811.html)
  - [`LDP3811`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ilxlightwave/ldp3811.html#pymeasure.instruments.ilxlightwave.LDP3811)

## Racal-Dana 1992 Universal Counter

### Racal-Dana 1992 Universal Counter

 *class *pymeasure.instruments.racal.Racal1992(*adapter*, *name='Racal-Dana 1992'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents a Racal-Dana 1992 Universal counter

```python
from pymeasure.instruments.racal import Racal1992
counter = Racal1992("GPIB0::10")

```

This class should also support Racal-Dana 1991 because it uses the same product manual, provided you avoid features that need channel B.

 channel_settings(*channel_name*, ***settings*)

Set channel configuration parameters.

Parameters:

-

**channel_name** – ‘A’ or ‘B’

-

**settings** –

one or more of these entries:

Any of these may be supplied: ’coupling’ can be ‘AC’ or ‘DC’; ‘attenuation’ can be ‘X1’ or ‘X10’; ‘trigger’ can be ‘auto’ or ‘manual’; ‘impedance’ can be ‘50’ or ‘1M’; ‘slope’ can be ‘pos’ or ‘neg’; ‘filtering’ can be True or False (only allowed for channel A); ‘input_select’ can be ‘separate’ or ‘common’ (only allowed for channel B); ‘trigger_level’ uses <floating point number>

 *static *decode(*v*, *allowed_types=None*)

Decode received message.

Returned values all share one layout: a 2-letter type prefix followed by a floating point number, which may of course represent an integer. For example, math constant Z is reported as MZ+001.00000000E+00

 *property *delay_enable*: Any*

Control delay. True=enable, False=disable

 *property *delay_time*: Any*

Control delay time.

 *property *device_type*: Any*

Read the unit device type. A Racal-Dana 1992 should return 1992, and a Racal-Dana 1991 should return 1991.

 *property *gpib_software_version*: Any*

Get GPIB software version

 *property *math_mode*: Any*

Set math mode. True=enable, False=disable

 *property *math_x*: Any*

Control math constant X.

 *property *math_z*: Any*

Control math constant Z.

 *property *measured_value

Get measured value.

A Racal-Dana 1992 does not send measurement data in direct response to a measurement-data request. Instead, completed measurements are pushed into a FIFO; once that FIFO is full, the oldest measurement is discarded.

The FIFO buffer is emptied when the instrument receives a command needing an immediate reply, such as reading a setting. Clearing an operating mode also empties it.

If no measurement data is present, this property blocks until data arrives. It can also timeout after the interval configured through the standard pyvisa API.

To ensure measurement data exists first, call wait_for_measurement().

 *property *operating_mode*: Any*

Set operating mode.

Permitted modes are:

Valid modes: ‘self_check’; ‘frequency_a’; ‘period_a’; ‘phase_a_rel_b’; ‘ratio_a_to_b’; ‘ratio_c_to_b’; ‘interval_a_to_b’; ‘total_a_by_b’; ‘frequency_c’

 preset()

Configure instrument with default presets.

 read(***kwargs*)

Read until read_termination, excluding it, or return the entire read buffer.

 reset_measurement()

Reset ongoing measurement.

 *property *resolution*: Any*

Set or read counter resolution as an integer from 3 to 10, specifying the number of significant digits.

 *property *software_version*: Any*

Get instrument software version

 *property *special_function_enable*: Any*

Control special function. True=enable, False=disable

 *property *special_function_number*: Any*

Control special function.

 *property *total_so_far*: Any*

Read the total number of events so far.

 *property *trigger_level_a*: Any*

Set or read trigger level for channel A

 *property *trigger_level_b*: Any*

Set or read trigger level for channel B

 wait_for_measurement(*timeout=None*, *progressDots=False*)

Wait until a fresh measurement is ready.

Parameters:

-

**timeout** – seconds to wait before raising the timeout exception. (default: `None`)

-

**progressDots** – if true, print ‘.’ after every ready-check (default: `False`)

 write(*command*, ***kwargs*)

Prefix every command sent to the instrument with a space to work around an unusual model issue.

Almost every device should work without it, but using it is harmless; it also fixes a real issue seen on a few devices.

## Racal-Dana

### Racal-Dana

This section documents the implemented Raca-Dana instruments. For an instrument that is not covered here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Racal-Dana 1992 Universal Counter](https://pymeasure.readthedocs.io/en/latest/api/instruments/racal/racal1992.html)
  - [`Racal1992`](https://pymeasure.readthedocs.io/en/latest/api/instruments/racal/racal1992.html#pymeasure.instruments.racal.Racal1992)
