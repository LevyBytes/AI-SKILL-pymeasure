# Aimtti, Mksinst, Danfysik, Resources

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Aim-TTi Electronic Loads; Aim-TTI; Aim-TTI PL Series Power Supplies; MKS Instruments Abstract Instrument; MKS Instruments 937B Vacuum Gauge Controller; MKS Instruments; MKS Instruments 974B Vacuum Pressure Transducer; Danfysik; Danfysik 8500 Power Supply; Resource Manager.

## Aim-TTi Electronic Loads

### Aim-TTi Electronic Loads

 *class *pymeasure.instruments.aimtti.ld400p.LD400P(*adapter*, *name='LD400'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Aim-TTi LD400P electronic DC load interface.

Note: digital communication is available on the LD400P only; the LD400 edition has no digital interface.

The LD400[P] [manual](https://resources.aimtti.com/manuals/LD400+LD400P_Instruction_Manual_EN_48511-1730_8.pdf) documents this interface.

Although `SCPIMixin` is inherited, this device does not handle the command options, `next_error`, or `check_errors` features.

 check_errors()

Not available.

 *property *current*: Any*

Return the measured load current (float).

 *property *input_enabled*: Any*

Set or read the digital load input state: `True` enables it and `False` disables it.

 *property *level_a*: Any*

Set or read Level A for current control mode (float).

 *property *level_b*: Any*

Set or read Level B for current control mode (float).

 *property *level_select*: Any*

Set which digital-load level is active. Accepted values are `("A", "B", "T", "V", "E")`; in order they select Level A, Level B, Transient, Ext Voltage and Ext TTL (string).

 *property *mode*: Any*

Set or read the digital load mode. Accepted values are `("C", "P", "R", "G", "V")`; in order they mean constant current, power, resistance, conductance, or voltage (string).

 *property *next_error

Get next error - Not available.

 *property *options

Get options - Not available.

 *classmethod *remove_unit_suffix(*msg*)

Strip recognized unit suffixes from a msg.

Because reply units vary with the device mode, this removes every known unit string.

Return type:

`str`

 *property *voltage*: Any*

Return the measured source input voltage (float).

## Aim-TTI

### Aim-TTI

This section documents the implemented Aim-TTI instruments. For a missing model, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Aim-TTI PL Series Power Supplies](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html)
  - [`PLBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#pymeasure.instruments.aimtti.aimttiPL.PLBase)
  - [`PLChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#pymeasure.instruments.aimtti.aimttiPL.PLChannel)
  - [`PL068P`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#pymeasure.instruments.aimtti.aimttiPL.PL068P)
  - [`PL155P`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#pymeasure.instruments.aimtti.aimttiPL.PL155P)
  - [`PL303P`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#pymeasure.instruments.aimtti.aimttiPL.PL303P)
  - [`PL601P`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#pymeasure.instruments.aimtti.aimttiPL.PL601P)
  - [`PL303QMDP`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#pymeasure.instruments.aimtti.aimttiPL.PL303QMDP)
  - [`PL303QMTP`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#pymeasure.instruments.aimtti.aimttiPL.PL303QMTP)

- [Aim-TTi Electronic Loads](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/ld400p.html)
  - [`LD400P`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/ld400p.html#pymeasure.instruments.aimtti.ld400p.LD400P)

## Aim-TTI PL Series Power Supplies

### Aim-TTI PL Series Power Supplies

 *class *pymeasure.instruments.aimtti.aimttiPL.PLBase(*adapter*, *name='AimTTI PL'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Control AimTTI PL series power supplies. Models whose number ends in -P or P(G) implement this remote interface.

Documentation:

[https://resources.aimtti.com/manuals/New_PL+PL-P_Series_Instruction_Manual-Iss18.pdf](https://resources.aimtti.com/manuals/New_PL+PL-P_Series_Instruction_Manual-Iss18.pdf)

PL-series devices:

[https://www.aimtti.com/product-category/dc-power-supplies/aim-plseries](https://www.aimtti.com/product-category/dc-power-supplies/aim-plseries)

The timeout argument defaults to 5000ms.

```python
psu = PL303QMDP("ASRL7::INSTR")
psu.reset()
psu.ch_2.voltage = 1.2
psu.ch_2.output_enabled = True
...
psu.ch_2.output_enabled = False
psu.local()

```

 *property *all_outputs_enabled*: Any*

Set whether every source is enabled at the same time; accepts True or False.

 local()

Switch to local mode. Disable every output before doing so.

 *class *pymeasure.instruments.aimtti.aimttiPL.PLChannel(*parent*, *id*, *voltage_range=None*, *current_range=None*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Single channel for AimTTI PL series power supplies.

Power-supply channels. Channel numbering begins at 1 and runs from right-to-left.

 *property *current*: Any*

Read the output readback current for this output channel in Amps.

 *property *current_limit*: Any*

Set or read the current limit in Amps.(dynamic)

 *property *current_range*: Any*

Choose the channel current range: Low (500/800mA) range or High range. Turn the output off before changing it.

 *property *output_enabled*: Any*

Set whether the source is enabled; accepts True or False.

 *property *voltage*: Any*

Read the output readback voltage for this output channel in Volts.

 *property *voltage_setpoint*: Any*

Set or read this channel's output voltage. With verify: completion means the adjusted parameter has reached the requested value within ±5% or ±10 counts.(dynamic)

 *class *pymeasure.instruments.aimtti.aimttiPL.PL068P(*adapter*, *name='AimTTI PL068-P'*, ***kwargs*)

Bases: `PLBase`

 ch_1

Channel:

`PLChannel`

 *class *pymeasure.instruments.aimtti.aimttiPL.PL155P(*adapter*, *name='AimTTI PL155-P'*, ***kwargs*)

Bases: `PLBase`

 ch_1

Channel:

`PLChannel`

 *class *pymeasure.instruments.aimtti.aimttiPL.PL303P(*adapter*, *name='AimTTI PL303-P'*, ***kwargs*)

Bases: `PLBase`

 ch_1

Channel:

`PLChannel`

 *class *pymeasure.instruments.aimtti.aimttiPL.PL601P(*adapter*, *name='AimTTI PL601-P'*, ***kwargs*)

Bases: `PLBase`

 ch_1

Channel:

`PLChannel`

 *class *pymeasure.instruments.aimtti.aimttiPL.PL303QMDP(*adapter*, *name='AimTTI PL303QMD-P'*, ***kwargs*)

Bases: `PLBase`

 ch_1

Channel:

`PLChannel`

 ch_2

Channel:

`PLChannel`

 *class *pymeasure.instruments.aimtti.aimttiPL.PL303QMTP(*adapter*, *name='AimTTI PL303QMT-P'*, ***kwargs*)

Bases: `PLBase`

 ch_1

Channel:

`PLChannel`

 ch_2

Channel:

`PLChannel`

 ch_3

Channel:

`PLChannel`

## MKS Instruments Abstract Instrument

### MKS Instruments Abstract Instrument

 *class *pymeasure.instruments.mksinst.mksinst.MKSInstrument(*adapter*, *name='MKS Instrument'*, *address=253*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Abstract MKS Instrument

The device connection uses an RS232/RS485 serial link. These devices follow this communication protocol:

For a query, send ‘@<aaa><Command>?;FF’ and expect ‘@<aaa>ACK<Response>;FF’. For a set command, send ‘@<aaa><Command>!<parameter>;FF’ and expect ‘@<aaa>ACK<Response>;FF’. The <aaa> field is an address from 001 to 254 supplied during initialization. Because pyvisa cannot use ‘;FF’ as the terminator, this class replaces the normal communication methods.

Parameters:

-

**adapter** – pyvisa resource name for the instrument, or an adapter instance

-

**name** (*string*) – Instrument name.

-

**address** – address inserted into each device message (default=253) (default: `253`)

-

**kwargs** – Any key-word argument accepted by Instrument

 check_set_errors()

Validate that a reply string contains the acknowledgement string.

 read()

Read from the instrument, including the required termination characters.

 write(*command*)

Send a write to the instrument, adding the device address.

Parameters:

**command** – command string sent to the instrument

 *class *pymeasure.instruments.mksinst.mksinst.RelayChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Configuration for the optional setpoint relay.

Depending on `direction`, the relay energizes either below or above the setpoint. Crossing the reset value in the opposite direction de-energizes it.

By default, the device applies auto hysteresis equal to 10% of the setpoint value; any change to the setpoint value or direction overwrites the current reset value. To use a hysteresis other than 10%, configure the setpoint value and direction first, then set the reset value.

 *property *direction*: Any*

Control the switching direction

 *property *resetpoint*: Any*

Set or read the value where the relay switches off

 *property *setpoint*: Any*

Control the relay switch setpoint

 *property *status*: Any*

Get the setpoint relay status

## MKS Instruments 937B Vacuum Gauge Controller

### MKS Instruments 937B Vacuum Gauge Controller

 *class *pymeasure.instruments.mksinst.mks937b.MKS937B(*adapter*, *name='MKS 937B vacuum gauge controller'*, *address=253*, ***kwargs*)

Bases: [`MKSInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html#pymeasure.instruments.mksinst.mksinst.MKSInstrument)

MKS 937B vacuum gauge controller

The device connection uses an RS232/RS485 serial link.

The 937B gauge controller accepts as many as 6 pressure measurement channels for different gauge types, including ionization gauges, Pirani and piezo gauges. Its twelve setpoint relays can energize at configured pressure readings. Relay-to-channel mapping is fixed: each pressure channel owns two relays.

Parameters:

-

**adapter** – pyvisa resource name for the instrument, or an adapter instance

-

**name** (*string*) – Instrument name.

-

**address** – address inserted into each device message (default=253) (default: `253`)

-

**kwargs** – Any key-word argument accepted by Instrument

 ch_1

Channel:

`IonGaugeAndPressureChannel`

 ch_2

Channel:

`PressureChannel`

 ch_3

Channel:

`IonGaugeAndPressureChannel`

 ch_4

Channel:

`PressureChannel`

 ch_5

Channel:

`IonGaugeAndPressureChannel`

 ch_6

Channel:

`PressureChannel`

 relay_1

Channel:

`Relay`

 relay_10

Channel:

`Relay`

 relay_11

Channel:

`Relay`

 relay_12

Channel:

`Relay`

 relay_2

Channel:

`Relay`

 relay_3

Channel:

`Relay`

 relay_4

Channel:

`Relay`

 relay_5

Channel:

`Relay`

 relay_6

Channel:

`Relay`

 relay_7

Channel:

`Relay`

 relay_8

Channel:

`Relay`

 relay_9

Channel:

`Relay`

 *property *all_pressures*: Any*

Return pressures for all channels using the selected units

 *property *combined_pressure1*: Any*

Return pressure for channel 1 together with its combination sensor

 *property *combined_pressure2*: Any*

Return pressure for channel 2 together with its combination sensor

 *property *serial*: Any*

Return the instrument serial number

 *property *unit*: Any*

Set or read the pressure unit used for every pressure reading from the instrument.

Permitted units: Unit.Torr, Unit.mbar, Unit.Pa, Unit.uHg.

 *class *pymeasure.instruments.mksinst.mks937b.IonGaugeAndPressureChannel(*parent*, *id*, ***kwargs*)

Bases: `PressureChannel`

Channel that includes both pressure and ion gauge sensors

 *property *ion_gauge_status*: Any*

Return the channel ion gauge status.

 *class *pymeasure.instruments.mksinst.mks937b.PressureChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

 *property *power_enabled*: Any*

Set or read the channel power status. (bool)

 *property *pressure*: Any*

Return the channel pressure in the units selected on the device

 *class *pymeasure.instruments.mksinst.mks937b.Relay(*parent*, *id*, ***kwargs*)

Bases: [`RelayChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html#pymeasure.instruments.mksinst.mksinst.RelayChannel)

 *property *enabled*: Any*

Set the relay function, or turn the setpoint relay off.

Use True/False to enable or disable pressure based relay activation; use ‘SET’ to energize the relay continuously.

## MKS Instruments

### MKS Instruments

This section documents the implemented MKS Instruments devices. For a missing model, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [MKS Instruments Abstract Instrument](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html)
  - [`MKSInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html#pymeasure.instruments.mksinst.mksinst.MKSInstrument)
  - [`RelayChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html#pymeasure.instruments.mksinst.mksinst.RelayChannel)

- [MKS Instruments 937B Vacuum Gauge Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks937b.html)
  - [`MKS937B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks937b.html#pymeasure.instruments.mksinst.mks937b.MKS937B)
  - [`IonGaugeAndPressureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks937b.html#pymeasure.instruments.mksinst.mks937b.IonGaugeAndPressureChannel)
  - [`PressureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks937b.html#pymeasure.instruments.mksinst.mks937b.PressureChannel)
  - [`Relay`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks937b.html#pymeasure.instruments.mksinst.mks937b.Relay)

- [MKS Instruments 974B Vacuum Pressure Transducer](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks974b.html)
  - [`MKS974B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks974b.html#pymeasure.instruments.mksinst.mks974b.MKS974B)
  - [`Relay`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks974b.html#pymeasure.instruments.mksinst.mks974b.Relay)

## MKS Instruments 974B Vacuum Pressure Transducer

### MKS Instruments 974B Vacuum Pressure Transducer

 *class *pymeasure.instruments.mksinst.mks974b.MKS974B(*adapter*, *name='MKS 974B vacuum pressure transducer'*, *address=253*, ***kwargs*)

Bases: [`MKSInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html#pymeasure.instruments.mksinst.mksinst.MKSInstrument)

MKS 974B vacuum pressure transducer

The device connection uses an RS232/RS485 serial link.

The 974B pressure transducer combines cold cathode ionization current measurement, a Pirani sensor, and a Piezo sensor, allowing one pressure gauge to span a wide pressure range. Optional hardware may include up to three mechanical relays that energize from the measured pressure value.

Parameters:

-

**adapter** – pyvisa resource name for the instrument, or an adapter instance

-

**name** (*string*) – Instrument name.

-

**address** – address inserted into each device message (default=253) (default: `253`)

-

**kwargs** – Any key-word argument accepted by `Instrument`

 relay_1

Channel:

`Relay`

 relay_2

Channel:

`Relay`

 relay_3

Channel:

`Relay`

 *property *coldcathode_pressure*: Any*

Get Cold Cathode sensor pressure

 *property *device_type*: Any*

Get the device type

 *property *firmware_version*: Any*

Return the instrument firmware version

 *property *hardware_version*: Any*

Return the instrument hardware version

 id()

Return the instrument identification.

 *property *manufacturer*: Any*

Get the manufacturer name

 *property *model*: Any*

Get the transducer model number

 *property *operation_hours*: Any*

Return the instrument operation hours

 *property *part_number*: Any*

Get the transducer part number

 *property *piezo_pressure*: Any*

Get Piezo differential sensor pressure

 *property *pirani_pressure*: Any*

Get MicroPirani sensor pressure

 *property *pressure*: Any*

Get combined pressure reading

 *property *serial_number*: Any*

Return the instrument serial number

 *property *status*: Any*

Get transducer status

 *property *switch_enabled*: Any*

Set or read the user switch that guards against accidental adjustment execution

 *property *temperature*: Any*

Get the MicroPirani sensor temperature

 *property *unit*: Any*

Set or read the pressure unit used for every pressure reading from the instrument.

Permitted units: Unit.Torr, Unit.mbar, Unit.Pa.

 *property *user_tag*: Any*

Control the user programmable tag

 *class *pymeasure.instruments.mksinst.mks974b.Relay(*parent*, *id*, ***kwargs*)

Bases: [`RelayChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html#pymeasure.instruments.mksinst.mksinst.RelayChannel)

 *property *enabled*: Any*

Set the assigned input channel, or disable the setpoint relay.

## Danfysik

### Danfysik

This section documents the implemented Danfysik instruments. For a missing model, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Danfysik 8500 Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/danfysik/danfysik8500.html)
  - [`Danfysik8500`](https://pymeasure.readthedocs.io/en/latest/api/instruments/danfysik/danfysik8500.html#pymeasure.instruments.danfysik.Danfysik8500)

## Danfysik 8500 Power Supply

### Danfysik 8500 Power Supply

 *class *pymeasure.instruments.danfysik.Danfysik8500(*adapter*, *name='Danfysik 8500 Current Supply'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

High-level interface representing the Danfysik 8500 Electromanget Current Supply for instrument interaction.

On Linux, allow user access to the Prolific Technology PL2303 Serial port adapter by creating `/etc/udev/rules.d/50-danfysik.rules` with these contents:

```none
SUBSYSTEMS=="usb",ATTRS{idVendor}=="067b",ATTRS{idProduct}=="2303",MODE="0666",SYMLINK+="danfysik"

```

After that, reload the udev rules with:

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger

```

The port `/dev/danfysik` will provide access to the device.

 add_ramp_step(*current*)

Append a current step to the ramp set.

Parameters:

**current** – A current in Amps

 clear_ramp_set()

Clears the ramp set.

 clear_sequence(*stack*)

Clear the sequence for the specified stack number.

Parameters:

**stack** (`int`) – Stack number in the range 0-15

Return type:

`None`

 *property *current

Set or read the actual current in Amps. You can assign this property through `current_ppm`.

 *property *current_ppm

Set or read current, expressed in parts per million..

 *property *current_setpoint

Return the current setpoint, which may differ from actual current (`current`) while the supply is still applying the value.

 disable()

Disables the flow of current.

 enable()

Enables the flow of current.

 *property *id*: Any*

Get the idenfitication information.

 is_current_stable()

Return True when the current is within 0.02 A of the setpoint value.

 is_enabled()

Return True when the current supply is enabled.

 is_ready()

Return True when the instrument reports the ready state.

 is_sequence_running(*stack*)

Return True when a sequence is running for the given stack number

Parameters:

**stack** – A stack number between 0-15

 local()

Put the instrument into local mode so the front panel can be used.

 *property *polarity

Set or read current-supply polarity, either -1 or 1. Assign one of those values to set this property.

 ramp_to_current(*current*, *points*, *delay_time=1*)

Run `set_ramp_to_current()` and then start the ramp.

 read()

Read from the device and raise exceptions for errors reported by the instrument.

Returns:

ASCII string response returned by the instrument

Raises:

An `Exception` raised if the Danfysik reports an error

 remote()

Put the instrument into remote mode, disabling the front panel.

 reset_interlocks()

Resets the instrument interlocks.

 set_ramp_delay(*time*)

Set the ramp delay time in seconds.

Parameters:

**time** – Delay time in seconds

 set_ramp_to_current(*current*, *points*, *delay_time=1*)

Configure a linear ramp from the initial current to another current, using a point count and delay time.

Parameters:

-

**current** – Final current in Amps

-

**points** – Number of linear points to traverse

-

**delay_time** – Delay time in seconds (default: `1`)

 set_sequence(*stack*, *currents*, *times*, *multiplier=999999*)

Configure an arbitrary ramp profile on the selected stack number (0-15), using a list of currents (Amps) and a list of interval times (seconds).

Return type:

`None`

 *property *slew_rate

Return the current sweep slew rate.

 start_ramp()

Starts the current ramp.

 start_sequence(*stack*)

Start a sequence for the specified stack number.

Parameters:

**stack** (`int`) – Stack number in the range 0-15

Return type:

`None`

 *property *status

Return human-readable status strings derived from `status_hex`.

 *property *status_hex

Return the hexadecimal status. `status` parses this value into a human-readable list.

 stop_ramp()

Stops the current ramp.

 stop_sequence()

Stops the currently running sequence.

Return type:

`None`

 sync_sequence(*stack*, *delay=0*)

Arm the ramp sequence for triggering by hardware input to pin P33 1&2 (10 to 24 V) or by a TS command. When delay is supplied, the sequence begins after that delay.

Parameters:

-

**stack** (`int`) – Stack number in the range 0-15

-

**delay** – Delay time in seconds (default: `0`)

Return type:

`None`

 wait_for_current(*has_aborted=<function Danfysik8500.<lambda>>*, *delay=0.01*)

Wait until the current stabilizes. If supplied, `has_aborted` is called after each delay interval (in seconds) along with the stability check, allowing abort behavior to be integrated.

Parameters:

-

**has_aborted** – Function returning True when waiting should stop (default: `<function Danfysik8500.<lambda> at 0x7aa5879e8510>`)

-

**delay** – Seconds between stability checks (default: `0.01`)

 wait_for_ready(*has_aborted=<function Danfysik8500.<lambda>>*, *delay=0.01*)

Wait until the instrument is ready. If supplied, `has_aborted` is called after each delay interval (in seconds) along with the readiness check, allowing abort behavior to be integrated.

Parameters:

-

**has_aborted** – Function returning True when waiting should stop (default: `<function Danfysik8500.<lambda> at 0x7aa5879e87d0>`)

-

**delay** – Seconds between readiness checks (default: `0.01`)

## Resource Manager

### Resource Manager

The `list_resources` function lets a user interactively inspect connected instruments.

 pymeasure.instruments.list_resources()

Print the available resources and return a list of VISA resource names

```python
resources = list_resources()
#prints (e.g.)
    #0 : GPIB0::22::INSTR : Agilent Technologies,34410A,******
    #1 : GPIB0::26::INSTR : Keithley Instruments Inc., Model 2612, *****
dmm = Agilent34410(resources[0])

```
