# Lakeshore425, Lakeshore211, Lakeshore224, Lakeshore3Xx

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Lake Shore 425 Gaussmeter; Lake Shore 211 Temperature Monitor; Lake Shore 224 Temperature Monitor; Lake Shore Cryogenics; Lake Shore 3xx Temperature Controller.

## Lake Shore 425 Gaussmeter

### Lake Shore 425 Gaussmeter

 *class *pymeasure.instruments.lakeshore.LakeShore425(*adapter*, *name='LakeShore 425 Gaussmeter'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the LakeShore 425 Gaussmeter, exposing a high-level interface for instrument interaction.

For Linux user access to the LakeShore 425 Gaussmeter, add `/etc/udev/rules.d/52-lakeshore425.rules` containing:

```none
SUBSYSTEMS=="usb",ATTRS{idVendor}=="1fb9",ATTRS{idProduct}=="0401",MODE="0666",SYMLINK+="lakeshore425"

```

Afterwards, reload the udev rules using:

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger

```

Access the device at `/dev/lakeshore425`.

 ac_mode(*wideband=True*)

Configures measurement for an oscillating (AC) field.

 auto_range()

Enables automatic adjustment of the field range.

 dc_mode(*wideband=True*)

Configures a steady-state (DC) field measurement.

 *property *field*: Any*

Read the field using the current units.

 measure(*points*, *has_aborted=<function LakeShore425.<lambda>>*, *delay=0.001*)

Blocks while collecting a supplied number of points, then returns the mean and standard deviation.

 *property *mode

Configure mode, filter, and bandwidth settings.

 *property *range*: Any*

Set the field range in units of Gauss; valid values are 35, 350, 3500, and 35,000 G. (float)

 *property *unit*: Any*

Set instrument units; allowed values are G, T, Oe, or A/m. (str)

 zero_probe()

Starts the zero field sequence used to calibrate the probe.

## Lake Shore 211 Temperature Monitor

### Lake Shore 211 Temperature Monitor

 *class *pymeasure.instruments.lakeshore.LakeShore211(*adapter*, *name='Lake Shore 211 Temperature Monitor'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Lake Shore 211 Temperature Monitor, exposing a high-level interface for instrument interaction.

Docstrings identify any properties and methods that remain untested.

```python
controller = LakeShore211("GPIB::1")

print(controller.temperature_celsius)     # Print the sensor temperature in celsius

```

 *class *AnalogMode(**values*)

Bases: `IntEnum`

 *class *AnalogRange(**values*)

Bases: `IntEnum`

 *class *RelayMode(**values*)

Bases: `IntEnum`

 *class *RelayNumber(**values*)

Bases: `IntEnum`

 *property *analog_configuration*: Any*

Set both analog range and analog mode. Provide values as (analog mode, analog range); Analog mode can be 0 or 1

| setting | mode |
| --- | --- |
| 0 | voltage |
| 1 | current |

Analog range can be 0 through 5

| setting | range |
| --- | --- |
| 0 | 0 – 20 K |
| 1 | 0 – 100 K |
| 2 | 0 – 200 K |
| 3 | 0 – 325 K |
| 4 | 0 – 475 K |
| 5 | 0 – 1000 K |

 *property *analog_out*: Any*

Measure the analog output percentage.

 configure_alarm(*on=True*, *high_value=270.0*, *low_value=0.0*, *deadband=0*, *latch=False*)

Set the alarm parameters for the input.

Parameters:

-

**on** - Boolean alarm setting, default True (default: `True`)

-

**high_value** - High value used as the temperature check for alarm activation (default: `270.0`)

-

**low_value** - Low value used as the temperature check for alarm activation (default: `0.0`)

-

**deadband** - Value by which the temperature must change outside an alarm condition (default: `0`)

-

**latch** - Determines whether the alarm latches (default: `False`)

 configure_relay(*relay*, *mode*)

Set the relay mode for a relay.

Property is UNTESTED

Parameters:

-

**relay** (*RelayNumber*) - Choose the relay to configure

-

**mode** (*RelayMode*) - Choose the mode to assign

 *property *display_units*: Any*

Set which input data is shown. Valid entries:

| setting | units |
| --- | --- |
| ‘kelvin’ | Kelvin |
| ‘celsius’ | Celsius |
| ‘sensor’ | Sensor Units |
| ‘fahrenheit’ | Fahrenheit |

 get_alarm_status()

Query the current alarm status

Returns:

Current status dictionary [on, high_value, low_value, deadband, latch]

 get_relay_mode(*relay*)

Retrieve a relay's status.

Property is UNTESTED

Parameters:

**relay** (*RelayNumber*) - Choose the relay to query

Returns:

Current RelayMode of queried relay

 reset_alarm()

Reset the Lakeshore 211 alarm.

 *property *temperature_celsius*: Any*

Measure sensor temperature in celsius.

 *property *temperature_fahrenheit*: Any*

Measure sensor temperature in fahrenheit.

 *property *temperature_kelvin*: Any*

Measure sensor temperature in kelvin.

 *property *temperature_sensor*: Any*

Measure sensor temperature in sensor units.

## Lake Shore 224 Temperature Monitor

### Lake Shore 224 Temperature Monitor

 *class *pymeasure.instruments.lakeshore.LakeShore224(*adapter*, *name='Lakeshore Model 224 Temperature Controller'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Lakeshore 224 Temperature monitor with a high-level interface to the instrument. The 224 includes 12 temperature input channels (A, B, C1-5, D1-5). This driver uses the [LakeShore Channel Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#lakeshorechannels)

```python
monitor = LakeShore224('GPIB::1')

print(monitor.input_A.kelvin)           # Print the temperature in kelvin on sensor A
monitor.input_A.wait_for_temperature()  # Wait for the temperature on sensor A to stabilize.

```

 input_0

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_A

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_B

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C1

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C2

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C3

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C4

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C5

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D1

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D2

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D3

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D4

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D5

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

## Lake Shore Cryogenics

### Lake Shore Cryogenics

This section documents the implemented Lake Shore Cryogenics instruments. For an instrument that is not included, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html). lakeshore3xx is the general class for Lake Shore temperature controllers in the 3xx series (like 325, 331, 334, 336, 340, 350).

- [Lake Shore 211 Temperature Monitor](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore211.html)
  - [`LakeShore211`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore211.html#pymeasure.instruments.lakeshore.LakeShore211)

- [Lake Shore 224 Temperature Monitor](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore224.html)
  - [`LakeShore224`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore224.html#pymeasure.instruments.lakeshore.LakeShore224)

- [Lake Shore 331 Temperature Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore331.html)
  - [`LakeShore331`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore331.html#pymeasure.instruments.lakeshore.LakeShore331)

- [Lake Shore 3xx Temperature Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore3xx.html)
  - [`LakeShore3xx`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore3xx.html#pymeasure.instruments.lakeshore.LakeShore3xx)

- [Lake Shore 421 Gaussmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore421.html)
  - [`LakeShore421`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore421.html#pymeasure.instruments.lakeshore.LakeShore421)

- [Lake Shore 425 Gaussmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore425.html)
  - [`LakeShore425`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore425.html#pymeasure.instruments.lakeshore.LakeShore425)

### LakeShore Channel Classes

Several Lakeshore instruments are built around channels and rely on the [Channel Interface](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#channels). Temperature monitoring and controller instruments use these common [`Channel Classes`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel):

 *class *pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Temperature input channel on a lakeshore temperature monitor. It reads temperature in kelvin, celsius, or sensor units, and includes a method that blocks until a specified stable temperature is reached.

 *property *celcius

Expose the celsius attribute through the celcius (sic) property.

Deprecated since version 0.14.0: Use celsius instead.

 *property *celsius*: Any*

Read a channel temperature in celsius.

 *property *kelvin*: Any*

Read a channel temperature in kelvin.

 *property *sensor*: Any*

Read a channel temperature in sensor units.

 Method call: wait_for_temperature with *target*, *unit='kelvin'*, *accuracy=0.1*, *interval=1*, *timeout=360*, and *should_stop=<function LakeShoreTemperatureChannel.<lambda>>*.

Blocks execution until the temperature reaches the target within accuracy (%), checking at each interval in seconds.

Parameters:

-

**target** - Target temperature expressed in kelvin, celsius, or sensor units.

-

**unit** - Unit used when querying temperature values: 'kelvin', 'celsius', or 'sensor'. (default: `'kelvin'`)

-

**accuracy** - Acceptable percentage deviation between target and temperature. (default: `0.1`)

-

**interval** - Time interval in seconds between queries. (default: `1`)

-

**timeout** - Seconds to wait before raising an exception (default: `360`)

-

**should_stop** - Function consulted to stop waiting when it returns True; by default it always returns False (default: `<function LakeShoreTemperatureChannel.<lambda> at 0x7aa5808f6f00>`)

 *class *pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreHeaterChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

A lakeshore temperature controller heater output channel. It offers properties for querying output power in percent of the max, setting manual output power, setting heater range, and setting the PID temperature setpoint.

 *property *mout*: Any*

Set manual heater output as a percent.

 *property *output*: Any*

Read heater output as percent of the max.

 *property *range*: Any*

Set heater range; allowed values are off, low, medium, and high.

 *property *setpoint*: Any*

Set the setpoint temperature using the preferred units of the control loop sensor.

## Lake Shore 3xx Temperature Controller

### Lake Shore 3xx Temperature Controller

 *class *pymeasure.instruments.lakeshore.LakeShore3xx(*adapter*, *name='Lakeshore Model 3xx Temperature Controller'*, *read_termination='\r\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models a Lake Shore Temperature Controller of the 3xx-Series with a high-level interface to the instrument. Multiple input-and output options are implemented. Not every channel exists in every device version. Some devices can use input option cards for additional input channels.

LS 331 and 335 provide two input channels (A and B) plus two output channels (1 and 2). LS 336 provides four input channels (A, B, C and D) plus four output channels (1, 2, 3 and 4).

LS 340 provides two input channels (A and B) and one output channel (1). Supported extension cards: * 3465 Single Capacitance Input Option Card: one added channel (C). * 3462 Dual Standard Input Option Card: two added channels (C and D). * 3464 Dual Thermocouple Input Option Card: two added channels (C and D). * 3468 Eight Channel Input Option Card: eight added channels (C1-C4, D1-D4).

LS 350 has input channels A, B, C and D (four total) and output channels 1, 2, 3 and 4 (four total). Supported extension card: * 3062 4-Channel Scanner option: D2, D3, D4, and D5 as 4 additional channels.

This driver uses the [LakeShore Channel Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#lakeshorechannels).

```python
controller = LakeShore3xx("GPIB::1")

print(controller.output_1.setpoint)         # Print the current setpoint for loop 1
controller.output_1.setpoint = 50           # Change the loop 1 setpoint to 50 K
controller.output_1.heater_range = 'low'    # Change the heater range to low.
controller.input_A.wait_for_temperature()   # Wait for the temperature to stabilize.
print(controller.input_A.kelvin)            # Print the temperature at sensor A.

```

 input_A

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_B

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C1

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C2

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C3

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_C4

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D1

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D2

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D3

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D4

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 input_D5

Channel:

[`LakeShoreTemperatureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreTemperatureChannel)

 output_1

Channel:

[`LakeShoreHeaterChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreHeaterChannel)

 output_2

Channel:

[`LakeShoreHeaterChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreHeaterChannel)

 output_3

Channel:

[`LakeShoreHeaterChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreHeaterChannel)

 output_4

Channel:

[`LakeShoreHeaterChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#pymeasure.instruments.lakeshore.lakeshore_base.LakeShoreHeaterChannel)
