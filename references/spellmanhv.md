# Spellmanxrv

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Spellman XRV High Voltage Power Supply; Spellman HV.

## Spellman XRV High Voltage Power Supply

### Spellman XRV High Voltage Power Supply

 *class *pymeasure.instruments.spellmanhv.SpellmanXRV(*adapter*, *name='Spellman XRV HV Power Supply'*, *query_delay=0.15*, *baud_rate=9600*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class wrapper for Spellman XRV series high voltage power supplies.

 filament

Channel:

`Filament`

 unscaled

Channel:

`UnscaledData`

 *property *analog_monitor*: Any*

Read the analog monitor feedback values.

Returns:

dict

Dict keys:

`voltage`, `current`, `filament`, `voltage_setpoint`, `current_setpoint`, `limit`, `preheat`, `anode_current`

(dynamic)

 *property *baudrate*: Any*

Configure the baud rate (int, exactly one of `9600`, `19200`, `38400`, `57600`, `115200`).

 check_set_errors()

After a command is sent, inspect the device for reported errors.

Raise:

ValueError if response is not `$`

Return type:

`list`[`str`]

 *static *checksum(*string_to_check*)

Calculate the checksum.

Parameters:

**string_to_check** (`str`) â€“ source string used when calculating the checksum

Return type:

`str`

Use this procedure to compute the checksum:

-

Before <CSUM>, sum every byte except <STX> into a 16 bit (or larger) word; treat each byte as an unsigned integer.

-

Take the two’s complement.

-

Keep only the eight least significant bits of the accumulated value.

-

On the resulting byte, force the most significant bit (bit 7) to 0 by applying bitwise AND with 0x7F.

-

Then force the next most significant bit (bit 6) to 1 using bitwise OR with 0x40.

With that algorithm, the checksum always falls from 0x40 through 0x7F. Because <STX> and <ETX> use ASCII values outside that range, the checksum cannot be mistaken for either control character.

 *property *configuration*: Any*

Get the power supply configuration.

Returns:

dict

Dict keys:

`reserved1`, `over_voltage_percentage`, `voltage_ramp_rate`, `current_ramp_rate`, `pre_warning_time`, `arc_count`, `reserved2`, `quench_time`, `max_kV`, `max_mA`, `watchdog_timer`

 *property *current_setpoint*: Any*

Set or read the current setpoint in Amps (float).(dynamic)

 *property *dsp*: Any*

Return the DSP part number and version (list).

 *property *errors*: Any*

Return the power supply errors (enum).

 *property *fpga*: Any*

Return the FPGA part number and version (list).

 *property *hv_on_timer*: Any*

Return accumulated HV On time in hours (float).

 *property *output_enabled*: Any*

Enable or disable the high voltage output (bool).

 *property *power_limits*: Any*

Set or read the power limits in Watts (list of int).

index = 0: large filament power limit index = 1: small filament power limit

Raise:

Raise ValueError when limit falls outside the allowed range

 read()

Read a response from the device, then validate it for errors.

Raise:

ConnectionError if the response lacks an initial <STX> or has a bad checksum. TCPIP connections skip checksum validation.

Return type:

`str`

 reset_errors()

Reset the error register.

Return type:

`None`

 reset_hv_on_timer()

Reset the counter for HV on hours.

Return type:

`None`

 *property *scaling*: Any*

Get scaling factors and polarity.

Returns:

dict

Dict keys:

`voltage`, `current`, `polarity`

For `voltage`, use V; for `current`, use A; `polarity` 0 means uni-polar and `polarity` 1 means bipolar

 set_scaling()

Set the scaling factors.

Set the scaling factor applied by `analog_monitor`, `current_setpoint`, `voltage`, `voltage_setpoint`, and `system_voltages`.

Return type:

`None`

 *property *status*: Any*

Return the power supply status (`StatusCode` enum).

 *property *system_voltages*: Any*

Read the system voltages in Volts.

Returns:

dict

Dict keys:

`temperature`, `reserved`, `anode`, `cathode`, `ac_line_cathode`, `dc_rail_cathode`, `ac_line_anode`, `dc_rail_anode`, `lvps_pos`, `lvps_neg`

(dynamic)

 *property *temperature*: Any*

Read the system temperature in Â°C (float).

 *property *voltage*: Any*

Read the output voltage in Volts (float).(dynamic)

 *property *voltage_setpoint*: Any*

Set or read the voltage setpoint in Volts (float).(dynamic)

 wait_for(*query_delay=0*)

Wait for some time.

Parameters:

**query_delay** (`float`) â€“ per-call override for the global query_delay. (default: `0`)

Return type:

`None`

 write(*command*)

Write to the instrument.

Before transmission, prefixes each command with <STX> (0x02) and appends checksum + <ETX> (0x03). TCPIP connections omit the checksum.

Return type:

`None`

 *class *pymeasure.instruments.spellmanhv.spellmanXRV.Filament(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class exposing filament functions for the x-ray tube.

 *property *enabled*: Any*

Set the filament status (bool).

 *property *large_size_enabled*: Any*

Configure whether the large filament is active (bool).

 *property *limit*: Any*

Set or read the filament limit setpoint (int, strictly from 0 to 4095).

 *property *preheat*: Any*

Set or read the filament preheat setpoint (int, strictly from 0 to 4095).

 *class *pymeasure.instruments.spellmanhv.spellmanXRV.UnscaledData(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for working with unscaled raw data from Spellman XRV power supplies.

 *property *analog_monitor*: Any*

Read the analog monitor feedback values.

Returns:

dict of int from `0` to `4095`

Dict keys:

`voltage`, `current`, `filament`, `voltage_setpoint`, `current_setpoint`, `limit`, `preheat`, `anode_current`

`voltage_setpoint`, `current_setpoint`, `limit`, and `preheat` apply only during local mode operation.

`anode_current` applies only to bipolar units.

 *property *current_setpoint*: Any*

Set or read the current setpoint (int, strictly from `0` to `4095`).

 *property *lvps_monitor*: Any*

Read the â€“15 V low voltage power supply (int from `0` to `4095`).

 *property *system_voltages*: Any*

Measure the system voltages.

Returns:

dict of int from `0` to `4095`

Dict keys:

`temperature`, `reserved`, `anode`, `cathode`, `ac_line_cathode`, `dc_rail_cathode`, `ac_line_anode`, `dc_rail_anode`, `lvps_pos`, `lvps_neg`

 *property *voltage*: Any*

Read the output voltage (int from `0` to `4095`).

 *property *voltage_setpoint*: Any*

Set or read the voltage setpoint (int, strictly from `0` to `4095`).

## Spellman HV

### Spellman HV

This section documents the implemented Spellman HV instruments. To cover an instrument that is absent, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Spellman XRV High Voltage Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/spellmanhv/spellmanXRV.html)
  - [`SpellmanXRV`](https://pymeasure.readthedocs.io/en/latest/api/instruments/spellmanhv/spellmanXRV.html#pymeasure.instruments.spellmanhv.SpellmanXRV)
  - [`Filament`](https://pymeasure.readthedocs.io/en/latest/api/instruments/spellmanhv/spellmanXRV.html#pymeasure.instruments.spellmanhv.spellmanXRV.Filament)
  - [`UnscaledData`](https://pymeasure.readthedocs.io/en/latest/api/instruments/spellmanhv/spellmanXRV.html#pymeasure.instruments.spellmanhv.spellmanXRV.UnscaledData)
