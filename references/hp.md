# Hp8657B, Hpsystempsu

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: HP Signal generator HP8657B; HP System Power Supplies HP663XA.

## HP Signal generator HP8657B

### HP Signal generator HP8657B

*Note:*

-

Because the instrument is a listen-only GPIB device, it cannot read values back.

-

The dynamic ranges feature could support implementations for other instruments in this family.

-

Support is not yet present for the optional pulse modulation feature.

Glossary:

| Abbreviation | Explanation |
| --- | --- |
| AM | Amplitude Modulation |
| FM | Frequency Modulation |
| dBm | power level, expressed in dB referenced to 1mW |

 *class *pymeasure.instruments.hp.HP8657B(*adapter*, *name='Hewlett-Packard HP8657B'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Hewlett Packard 8657B signal generator and exposes a high-level interface for interacting with the instrument.

 *class *Modulation(**values*)

Bases: `IntEnum`

IntEnum covering the available modulation sources.

 *property *am_depth*: Any*

Sets AM modulation depth; usable range is 0-99.9%.

 *property *am_source*: Any*

Selects the AM function source using the `Modulation` enumeration.

| Value | Meaning |
| --- | --- |
| OFF | no modulation active |
| INT_400HZ | internal 400 Hz modulation source |
| INT_1000HZ | internal 1000 Hz modulation source |
| EXTERNAL | External source, AC coupling |

*Note:*

-

AM & FM may both be active at the same time.

-

Only a single internal source can be active at one time.

-

use “OFF” to deactivate AM

usage example:

```python
sig_gen = HP8657B("GPIB::7")
...
sig_gen.am_source = sig_gen.Modulation.INT_400HZ    #  Enable int. 400 Hz source for AM
sig_gen.am_depth = 50                               #  Set AM modulation depth to 50%
...
sig_gen.am_source = sig_gen.Modulation.OFF          #  Turn AM off

```

 check_errors()

Reads the error status register; since the 8657B cannot read out values, it returns 0 and logs a warning.

 clear()

Restores the instrument to its power-on default settings.

 *property *fm_deviation*: Any*

Sets FM peak deviation in kHz; useable range is 0.1 - 400 kHz.

*NOTE*:

The maximum usable deviation depends on output frequency; consult the instrument documentation for further detail.

 *property *fm_source*: Any*

Selects the FM function source using the `Modulation` enumeration.

| Value | Meaning |
| --- | --- |
| OFF | no modulation active |
| INT_400HZ | internal 400 Hz modulation source |
| INT_1000HZ | internal 1000 Hz modulation source |
| EXTERNAL | External source, AC coupling |
| DC_FM | External source with DC coupling (FM only) |

*Note:*

-

AM & FM may both be active at the same time.

-

Only a single internal source can be active at one time.

-

use “OFF” to deactivate FM

-

Refer to the documentation for details on use of DC FM mode.

usage example:

```python
sig_gen = HP8657B("GPIB::7")
...
sig_gen.fm_source = sig_gen.Modulation.EXTERNAL     #  Enable external source for FM
sig_gen.fm_deviation = 15                           #  Set FM peak deviation to 15 kHz
...
sig_gen.fm_source = sig_gen.Modulation.OFF          #  Turn FM off

```

 *property *frequency*: Any*

Sets the instrument output frequency in Hz.

For the 8567B, valid values span 100 kHz to 2060 MHz.

 id* = 'HP,8657B,N/A,N/A'*

Manual ID entry

 *property *level*: Any*

Sets the output level in dBm.

For the 8657B, the allowed range is -143.5 to +17 dBm/

 *property *level_offset*: Any*

Sets output offset in dB; usable range is -199 to +199 dB.

 *property *output_enabled*: Any*

Controls whether output is enabled.

 reset()

Resets the instrument.

 shutdown()

Places the instrument in a safe and stable state.

## HP System Power Supplies HP663XA

### HP System Power Supplies HP663XA

Currently supported models are:

| Model | Voltage | Current | Power |
| --- | --- | --- | --- |
| 6632A | 0..20 V | 0..5.0 A | 100 W |
| 6633A | 0..50 V | 0..2.5 A | 100 W |
| 6634A | 0..100 V | 0..1.0 A | 100 W |

*Note:*

-

Some command syntax is shared by HP 6621A, 6622A, 6623A, 6624A, 6625A, 6626A, 6627A & 6628A multi-channel system power supplies; this implementation could probably incorporate them.

-

The B-version models (6632B, 6633B & 6634B) are SPCI-compliant, so a similar implementation approach could cover them.

 *class *pymeasure.instruments.hp.HP6632A(*adapter*, *name='Hewlett-Packard HP6632A'*, ***kwargs*)

Bases: [`HPLegacyInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html#pymeasure.instruments.hp.HPLegacyInstrument)

Models the Hewlett Packard 6632A system power supply and exposes a high-level interface for interacting with the instrument.

 *class *ERRORS(**values*)

Bases: `Enum`

Enum class for error messages

 *property *OCP_enabled*: Any*

A bool property controlling whether OCP (OverCurrent Protection) is enabled.

 *property *SRQ_enabled*: Any*

A bool property controlling whether SRQ (ServiceReQuest) is enabled.

 *class *ST_ERRORS(**values*)

Bases: `Enum`

Enum class for selftest errors

 check_errors()

Reads the error status register.

Return error_status:

One byte containing the error status register content.

Rtype error_status:

int

 check_selftest_errors()

Reads the error status register.

Return error_status:

One byte containing the error status register content.

Rtype error_status:

int

 clear()

Restores the instrument to power-on default settings.

 *property *current*: Any*

A floating point property controlling the device output current.

(dynamic)

 *property *delay*: Any*

A float property for the reprogamming delay; defaults are 8 ms when FAST mode is used and 80 ms when NORM mode is used.

The instrument rounds values to the next 4 ms.

 *property *display_active*: Any*

A boot property controlling whether the display is enabled.

 *property *id*: Any*

Reads the instrument ID and currently returns this value.

 *property *output_enabled

A bool property controlling whether output is enabled.

 *property *over_voltage_limit*: Any*

A floationg point property for setting the OVP threshold.

(dynamic)

 reset_OVP_OCP()

Resets Overvoltage and Overcurrent protections

 *property *rom_version*: Any*

Reads the instrument ROM id (software version) and currently returns this value.

 *property *status

Returns an object that represents the unit's current status.

 status_desc

alias of `Status`

 *property *voltage*: Any*

A floating point proptery controlling the device output voltage.

(dynamic)

 *class *pymeasure.instruments.hp.HP6633A(*adapter*, *name='Hewlett Packard HP6633A'*, ***kwargs*)

Bases: `HP6632A`

Models the Hewlett Packard 6633A system power supply and exposes a high-level interface for interacting with the instrument.

 *class *pymeasure.instruments.hp.HP6634A(*adapter*, *name='Hewlett Packard HP6634A'*, ***kwargs*)

Bases: `HP6632A`

Models the Hewlett Packard 6634A system power supply and exposes a high-level interface for interacting with the instrument.
