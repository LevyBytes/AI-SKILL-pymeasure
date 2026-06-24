# Velleman, Aculight, Novanta, Hcp ...

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Coverage in this packet includes Velleman and the Velleman K8090 8-channel relay board; Aculight with the Aculight Argos 2400 OPO system; Novanta FPU60 laser power supply unit and Novanta Photonics; HCP TC038 crystal oven, HCP TC038D crystal oven, and HC Photonics; Inficon SQM-160 multi-film rate/thickness monitor and Inficon; plus Razorbill and the Razorbill RP100 custrom power supply for Razorbill Instrums stress & strain cells.

## Velleman

### Velleman

Implemented Velleman instruments are documented in this section. To use a device that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Velleman K8090 8-channel relay board](https://pymeasure.readthedocs.io/en/latest/api/instruments/velleman/k8090.html)
  - [`VellemanK8090`](https://pymeasure.readthedocs.io/en/latest/api/instruments/velleman/k8090.html#pymeasure.instruments.velleman.VellemanK8090)
  - [`VellemanK8090Switches`](https://pymeasure.readthedocs.io/en/latest/api/instruments/velleman/k8090.html#pymeasure.instruments.velleman.VellemanK8090Switches)

## Velleman K8090 8-channel relay board

### Velleman K8090 8-channel relay board

 *class *pymeasure.instruments.velleman.VellemanK8090(*adapter*, *name='Velleman K8090'*, *timeout=100*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Use this for the Velleman K8090 relay board.

Consult the "K8090/VM8090 PROTOCOL MANUAL" for serial command details.

Communication uses serial USB, with fixed IO settings:

| Baud rate | 19200 |
| --- | --- |
| Data bits | 8 |
| Parity | None |
| Stop bits | 1 |
| Flow control | None |

Prefer a short timeout because the device does not reliably emit status messages, and serial timeouts can happen during normal use.

Use the class like:

```python
from pymeasure.instruments.velleman import VellemanK8090, VellemanK8090Switches as Switches

instrument = VellemanK8090("ASRL1::INSTR")

# Get status update from device
last_on, curr_on, time_on = instrument.status

# Toggle a selection of channels on
instrument.switch_on = Switches.CH3 | Switches.CH4 | Switches.CH5

```

 check_set_errors()

After setting a property, check for errors and log any found.

Used when `check_set_errors=True` is configured on that property.

After a switch command, the K8090 returns status only when at least one switch actually changed. This code tries to drain the buffer so it is empty. It does not perform real error checking here.

Returns:

List of error entries.

 read(***kwargs*)

Read command tailored to the K8090 protocol.

Overrides the corresponding method from the `instrument` class.

Refer to `write()`; device replies follow the same format.

Reading returns CMD, MASK, PARAM1, and PARAM2 as a list.

 *property *status*: Any*

Return the present relay status; the response command byte differs from the request.

Returns three `VellemanK8090Switches` flag values:

-

Previous state: every relay's state before this event

-

Current state: every relay's present state

-

Timer state: every relay timer's state

 *property *switch_off*: Any*

Switch channels to the off state. See `switch_on` for details.

 *property *switch_on*: Any*

Switch channels to the on state without affecting other channels. Provide a list or set of channel numbers, beginning at 1, or provide a bitmask.

Once switching is requested, this waits for the device reply. The reply is sent only when a relay toggles, so otherwise the call can block for the communication timeout. Avoid unnecessary switch_ calls when speed matters.

 *property *version*: Any*

Return the firmware version as (year - 2000, week), for example `(10, 1)`.

 write(*command*, ***kwargs*)

Write command tailored to the K8090 protocol.

Overrides the corresponding method from the `Instrument` class.

Every packet sent to the device contains 7 bytes:

STX (0x04) - CMD - MASK - PARAM1 - PARAM2 - CHK - ETX (0x0F)

CHK is the package checksum.

Parameters:

**command** (*str*) - String such as "CMD[, MASK, PARAM1, PARAM2]"; only CMD is required.

 *class *pymeasure.instruments.velleman.VellemanK8090Switches(**values*)

Bases: `IntFlag`

Use to identify switch channels.

## Aculight

### Aculight

Implemented (Lockheed Martin) Aculight instruments are documented in this section. To use a device that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Aculight Argos 2400 OPO system](https://pymeasure.readthedocs.io/en/latest/api/instruments/aculight/argos.html)
  - [`Argos`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aculight/argos.html#pymeasure.instruments.aculight.argos.Argos)

## Aculight Argos 2400 OPO system

### Aculight Argos 2400 OPO system

 *class *pymeasure.instruments.aculight.argos.Argos(*adapter*, *name='Argos 2400 OPO system'*, *query_delay=0.01*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Communication model for the Aculight Argos 2400 OPO system.

The device returns only the full value set at once, which takes around 100 ms. When more than one value is needed, read the `state` property rather than separate properties. Any property read reads all properties, then returns the matching value.

Also note that block temperature cannot be set remotely; use the front panel.

Cable type: RS232 null modem female DB9 connectors. Pins 2 and 3 must cross between the two sides. Pin2 is RX, Pin3 is Tx, and Pin 5 is ground.

Parameters:

-

**adapter** – resource name

-

**query_delay** - Delay in seconds between write and read. (default: `0.01`)

 check_set_errors()

Read after setting.

 *property *etalon*: Any*

Set or read the etalon angle in degrees.

 *property *seed_voltage*: Any*

Set or read the seed source tuning voltage.

 *property *state*: State*

Return the system's present state as a namped tuple

Return named tuple:

containing 'crystal_temperature', 'crystal_temperature_setpoint', 'etalon_angle', and 'seed_voltage'.

 *property *temperature*: Any*

Return the present crystal temperature in Â°C.

 *property *temperature_setpoint*: Any*

Set or read the crystal temperature setpoint in Â°C.

 *property *version*: Any*

Get the firmware version.

 wait_for(*query_delay=None*)

Wait for a duration; `ask` uses this before reading.

Parameters:

**query_delay** - Seconds to wait between writing and reading. None means the default delay. (default: `None`)

## Novanta FPU60 laser power supply unit

### Novanta FPU60 laser power supply unit

 *class *pymeasure.instruments.novanta.Fpu60(*adapter*, *name='Laserquantum fpu60 power supply unit'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents an fpu60 power supply unit for the finesse laser series from Laserquantum, a Novanta company.

The instrument sends a response for each command.

 check_set_errors()

After setting a property, check for errors and log any found.

Used when `check_set_errors=True` is configured on that property.

Returns:

List of error entries.

 *property *current*: Any*

Measure diode current as a percent value (float).

 disable_emission()

Turn off emission, then unlock the button.

Emission can be enabled again only by pressing the physical button.

 *property *emission_enabled*: Any*

Measure the emission status (bool).

 get_operation_times()

Return operation times in minutes as a dictionary.

 *property *head_temperature*: Any*

Measure laser head temperature in Â°C (float).

 *property *interlock_enabled*: Any*

Return interlock enabled status (bool).

 *property *power*: Any*

Measure present output power in Watts (float).

 *property *power_setpoint*: Any*

Set or read the output power setpoint in Watts (float).

 *property *psu_temperature*: Any*

Measure power supply unit temperature in Â°C (float).

 *property *serial_number*: Any*

Get the serial number (str).

 *property *shutter_open*: Any*

Set or read whether the shutter is open (bool).

 *property *software_version*: Any*

Get the software version (str).

## Novanta Photonics

### Novanta Photonics

Implemented Novanta photonics instruments are documented in this section. Novanta also includes lasers developed by Laserquantum. To use a device that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Novanta FPU60 laser power supply unit](https://pymeasure.readthedocs.io/en/latest/api/instruments/novanta/fpu60.html)
  - [`Fpu60`](https://pymeasure.readthedocs.io/en/latest/api/instruments/novanta/fpu60.html#pymeasure.instruments.novanta.Fpu60)

## HCP TC038 crystal oven

### HCP TC038 crystal oven

 *class *pymeasure.instruments.hcp.TC038(*adapter*, *name='TC038'*, *address=1*, *timeout=1000*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Communication support for the HCP TC038 oven.

This older version uses an AC power supply and AC heater.

Parity or framing errors occur from time to time, so the application must handle them.

For every valid request or command, the oven responds with "OK".

Parameters:

-

**adapter** (`Union`[[`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter), `int`, `str`]) - COM-Port name.

-

**name** (`str`) - Instrument name. (default: `'TC038'`)

-

**address** (`int`) - Device address; should be between 1 and 99. (default: `1`)

-

**timeout** (`int`) - Timeout in ms. (default: `1000`)

-

**kwargs** - Extra arguments passed to the Instrument base class.

 check_set_errors()

After setting a property, check for errors.

Used when `check_set_errors=True` is configured on that property.

Return type:

`list`[`str`]

 *property *information*: Any*

Return information about the device and its capabilities.

 *property *monitored_value*: Any*

Measure the value currently being monitored. By default, this is the current temperature in Â°C.

 read(***kwargs*)

Do error checking on reading.

Return type:

`str`

 set_monitored_quantity(*quantity='temperature'*)

Set which quantity the oven should monitor.

quantity can be any registers key. The default is current temperature in Â°C.

Return type:

`None`

 *property *setpoint*: Any*

Set or read the temperature controller setpoint in Â°C.

 *property *temperature*: Any*

Measure the present temperature in Â°C.

 write(*command*, ***kwargs*)

Send a command using the device's own protocol.

Return type:

`None`

## HCP TC038D crystal oven

### HCP TC038D crystal oven

 *class *pymeasure.instruments.hcp.TC038D(*adapter*, *name='TC038D'*, *address=1*, *timeout=1000*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Communication support for the HCP TC038D oven.

This newer version uses DC heating.

The oven expects raw bytes to be written, not ascii code, and it also sends raw bytes. Variables can use two or four-byte modes. The driver uses the four-byte mode addresses, where element count must be double the variables read.

 check_set_errors()

After setting a property, check for errors.

Used when `check_set_errors=True` is configured on that property.

 ping(*test_data=0*)

Test the connection by sending an integer up to 65535, then checking the response.

 read()

Read the response, interpret the number, and return it as a string.

 *property *setpoint*: Any*

Set or read the oven setpoint in Â°C.

 *property *temperature*: Any*

Measure the oven's present temperature in Â°C.

 write(*command*)

Send a command to the device.

Parameters:

**command** (*str*) - Comma separated string containing the function, read ('R'), write ('W'), or 'echo'; the address to write, for example '0x106' or '262'; the comma separated values to write; or the number of elements to read, defaulting to 1.

## HC Photonics

### HC Photonics

Implemented HC Photonics instruments are documented in this section. To use a device that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [HCP TC038 crystal oven](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038.html)
  - [`TC038`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038.html#pymeasure.instruments.hcp.TC038)

- [HCP TC038D crystal oven](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038d.html)
  - [`TC038D`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038d.html#pymeasure.instruments.hcp.TC038D)

## Inficon SQM-160 multi-film rate/thickness monitor

### Inficon SQM-160 multi-film rate/thickness monitor

 *class *pymeasure.instruments.inficon.sqm160.SQM160(*adapter*, *name='Inficon SQM-160 thickness monitor'*, *baud_rate=19200*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Inficon SQM-160 multi-film rate/thickness monitor.

Uses a quartz crystal sensor to measure rate and thickness during thin film deposition. Device connection is typically through serial (RS232), with USB or Ethernet as optional alternatives.

Each command packet always contains:

-

1 Byte: Sync character; '!' occurs only at message start.

-

1 Byte: length character derived from message length without CRC.

34 is added to prevent any '!' from appearing.

-

Command message with variable length.

-

2 Byte: Cyclic Redundancy Check (CRC) checksum.

Each response packet always contains:

-

1 Byte: Sync character; '!' occurs only at message start.

-

1 Byte: length character derived from message length without CRC.

A value of 35 is added.

-

1 Byte: response status character that reports command status.

-

Response message with variable length.

-

2 Byte: Cyclic Redundancy Check (CRC) checksum.

Parameters:

-

**adapter** - pyvisa resource name for the instrument, or an adapter instance

-

**name** (*string*) - Instrument name.

-

**baud_rate** (*string*) - Serial connection baud rate.

-

**kwargs** - Any valid key-word argument for Instrument

 sensor_1

Channel:

`SensorChannel`

 sensor_2

Channel:

`SensorChannel`

 sensor_3

Channel:

`SensorChannel`

 sensor_4

Channel:

`SensorChannel`

 sensor_5

Channel:

`SensorChannel`

 sensor_6

Channel:

`SensorChannel`

 *property *all_values*: Any*

Return each sensor's current rate (Angstrom/s), Thickness (Angstrom), and frequency (Hz)

 *property *average_rate*: Any*

Return current average rate in Angstrom per second

 *property *average_thickness*: Any*

Return current average thickness in Angstrom

 check_set_errors()

After setting a property, check for errors.

 *property *firmware_version*: Any*

Get the firmware version.

 *property *number_of_channels*: Any*

Return how many channels are installed

 read()

Read a response message from the instrument.

This method also validates the checksum.

Returns:

the response packet

Return type:

string

Raises:

**ConnectionError** - raised when a checksum error or incorrect response status is detected.

 *property *reset_flag*: Any*

Return the power-up reset flag. It is True only on the first read after a power cycle.

 reset_system_parameters()

Reset all system and film parameters.

 reset_thickness_rate()

Reset average rate and average thickness.

This also zeroes all active Sensor Rates and Thicknesses

 reset_time()

Reset monitor time to zero.

 write(*command*)

Send a command to the device.

 *class *pymeasure.instruments.inficon.sqm160.SensorChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Sensor channel used for individual rate measurements.

 *property *crystal_life*: Any*

Return crystal life as a percent value

 *property *frequency*: Any*

Return the current frequency for one sensor in Hz

 *property *rate*: Any*

Return the current rate for one sensor in Angstrom per second

 *property *thickness*: Any*

Return the current thickness for one sensor in Angstrom

## Inficon

### Inficon

Implemented Inficon instruments are documented in this section. To use a device that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Inficon SQM-160 multi-film rate/thickness monitor](https://pymeasure.readthedocs.io/en/latest/api/instruments/inficon/sqm160.html)
  - [`SQM160`](https://pymeasure.readthedocs.io/en/latest/api/instruments/inficon/sqm160.html#pymeasure.instruments.inficon.sqm160.SQM160)
  - [`SensorChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/inficon/sqm160.html#pymeasure.instruments.inficon.sqm160.SensorChannel)

## Razorbill

### Razorbill

Implemented Razorbill instruments are documented in this section. To use a device that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Razorbill RP100 custrom power supply for Razorbill Instrums stress & strain cells](https://pymeasure.readthedocs.io/en/latest/api/instruments/razorbill/razorbillRP100.html)
  - [`razorbillRP100`](https://pymeasure.readthedocs.io/en/latest/api/instruments/razorbill/razorbillRP100.html#pymeasure.instruments.razorbill.razorbillRP100)

## Razorbill RP100 custrom power supply for Razorbill Instrums stress & strain cells

### Razorbill RP100 custrom power supply for Razorbill Instrums stress & strain cells

 *class *pymeasure.instruments.razorbill.razorbillRP100(*adapter*, *name='Razorbill RP100 Piezo Stack Powersupply'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents Razorbill RP100 strain cell controller

```python
scontrol = razorbillRP100("ASRL/dev/ttyACM0::INSTR")

scontrol.output_1 = True      # turns output on
scontrol.slew_rate_1 = 1      # sets slew rate to 1V/s
scontrol.voltage_1 = 10       # sets voltage on output 1 to 10V

```

 *property *contact_current_1*: Any*

Return the amps currently present at the channel 1 front panel output

 *property *contact_current_2*: Any*

Return the amps currently present at the channel 2 front panel output

 *property *contact_voltage_1*: Any*

Return the volts currently present at the channel 1 front panel output

 *property *contact_voltage_2*: Any*

Return the volts currently present at the channel 2 front panel output

 *property *instant_voltage_1*: Any*

Return the instantaneous voltage output from source one

 *property *instant_voltage_2*: Any*

Return the instantaneous voltage output from source two

 *property *output_1*: Any*

Turn channel 1 output on or off

 *property *output_2*: Any*

Turn channel 2 output on or off

 *property *slew_rate_1*: Any*

Set or read channel 1 source slew rate in volts/sec

 *property *slew_rate_2*: Any*

Set or read channel 2 source slew rate in volts/sec

 *property *voltage_1*: Any*

Set or read channel 1 output voltage

 *property *voltage_2*: Any*

Set or read channel 2 output voltage
