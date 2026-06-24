# Cnt91

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Pendulum; Pendulum CNT91 frequency counter.

## Pendulum

### Pendulum

This section documents the implemented Pendulum instruments. For an instrument that is not present here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Pendulum CNT91 frequency counter](https://pymeasure.readthedocs.io/en/latest/api/instruments/pendulum/cnt91.html)
  - [`CNT91`](https://pymeasure.readthedocs.io/en/latest/api/instruments/pendulum/cnt91.html#pymeasure.instruments.pendulum.cnt91.CNT91)

## Pendulum CNT91 frequency counter

### Pendulum CNT91 frequency counter

 *class *pymeasure.instruments.pendulum.cnt91.CNT91(*adapter*, *name='Pendulum CNT-91'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models a Pendulum CNT-91 frequency counter.

 *property *batch_size

Return the largest count of buffer entries transmittable in one operation.

 buffer_frequency_time_series(*channel*, *n_samples*, *sample_rate=None*, *gate_time=None*, *trigger_source=None*, *back_to_back=True*)

Capture a time series into the buffer, then read it once the operation completes.

Parameters:

-

**channel** â€“ Channel to use

-

**n_samples** â€“ Count of samples

-

**gate_time** â€“ Measurement gate duration in s (default: `None`)

-

**trigger_source** â€“ Optional trigger source used to start the measurement (default: `None`)

-

**back_to_back** â€“ When True, run the buffer measurement back-to-back. (default: `True`)

-

**sample_rate** –

Sample rate in Hz

Deprecated since version 0.14: Use gate_time as the replacement parameter. (default: `None`)

 configure_frequency_array_measurement(*n_samples*, *channel*, *back_to_back=True*)

Set up the counter to make a measurement array.

Parameters:

-

**n_samples** â€“ Count of samples

-

**channel** â€“ Channel for measurement (A, B, C, E, INTREF)

-

**back_to_back** â€“ When True, run the buffer measurement back-to-back. (default: `True`)

 *property *continuous*: Any*

Set whether measurements run continuously.

 *property *external_arming_start_slope*: Any*

Set the start arming condition slope (str â€˜POSâ€™ or â€˜NEGâ€™).

 *property *external_start_arming_source*: Any*

Set the external arming source (â€˜Aâ€™, â€˜Bâ€™, â€˜Eâ€™ (rear) or â€˜IMMâ€™ for immediately arming).

 *property *format*: Any*

Select the response format (â€˜ASCIIâ€™ or â€˜REALâ€™).

 *property *gate_time*: Any*

Set one measurement's gate time in s (float strictly from 2e-8 to 1000).

 *property *interpolator_autocalibrated*: Any*

Set whether interpolators calibrate automatically (bool).

 *property *measurement_time

Set one measurement's gate time in s (float strictly from 2e-8 to 1000).

Deprecated since version 0.14: Use gate_time as the replacement.

 read_buffer(*n=10000*)

Read n samples from the buffer.

Parameters:

**n** â€“ Count of samples to read from the buffer. By default, the maximum number of 10000 samples is read out. (default: `10000`)

Returns:

Frequency values from the buffer.
