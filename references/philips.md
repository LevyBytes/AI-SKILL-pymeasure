# Pm6669

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Philips; Philips PM 6669 Universal Frequency Counter.

## Philips

### Philips

This part documents the Philips instruments currently implemented. For an instrument that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).`.

- [Philips PM 6669 Universal Frequency Counter](https://pymeasure.readthedocs.io/en/latest/api/instruments/philips/PM6669.html)
  - [`PM6669`](https://pymeasure.readthedocs.io/en/latest/api/instruments/philips/PM6669.html#pymeasure.instruments.philips.PM6669)

## Philips PM 6669 Universal Frequency Counter

### Philips PM 6669 Universal Frequency Counter

 *class *pymeasure.instruments.philips.PM6669(*adapter*, *name='Philips PM 6669'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents the Philips PM 6669 instrument.

 *property *SRQMask*: Any*

Control the SRQ mask

 *property *freerun_enabled*: Any*

Control the freerun settings

 *property *gate_enabled*: Any*

Control the gate

For the totalize function, choose True to open the gate and False to close it. After that, retrieve the count with read_measurement(). Freerun mode is the usual choice for most uses.

 *property *id*: Any*

Get the instrument identification

 *property *measurement_settings*: Any*

Retrieve the device's measurement settings.

 *property *measurement_time*: Any*

Set the measurement time, in seconds.

 *property *measurement_timeout*: Any*

Control the measurement timeout

This timeout matters only when freerun is off.

 *property *measuring_function*: Any*

Set the device measuring function (str).

 read()

Read function that includes the instrument bug work around.

When the device receives a request with a measurement ready, it returns both the reply and the measurement. The measurement gets removed from that response and stored in a backlog Queue.

 read_measurement(*wait_for_srq=False*)

Wait until the device sends an SRQ, then read the result.

With wait_for_srq set, MSR needs to be MSRFlag.MEASUREMENT_READY.

 reset_to_defaults()

Return the instruments to their default settings.

 spoll()

Retrieve the device status.

 trigger()

Send a trigger to the device outside freerun mode.
