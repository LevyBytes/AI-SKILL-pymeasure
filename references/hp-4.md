# Hp8753E

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Hewlett Packard; HP 8753E Vector Network Analyzer.

## Hewlett Packard

### Hewlett Packard

Use this section for documentation on the implemented Hewlett Packard instruments. For an instrument that is missing here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

When the instrument you need is absent from this page, also look under [Agilent](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/index.html) or [Keysight](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/index.html) for newer instruments.

- [HP 33120A Arbitrary Waveform Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp33120A.html)
  - [`HP33120A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp33120A.html#pymeasure.instruments.hp.HP33120A)

- [HP 34401A Multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp34401A.html)
  - [`HP34401A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp34401A.html#pymeasure.instruments.hp.HP34401A)

- [HP 3437A System-Voltmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3437A.html)
  - [`HP3437A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3437A.html#pymeasure.instruments.hp.HP3437A)

- [HP 3478A Multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3478A.html)
  - [`HP3478A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3478A.html#pymeasure.instruments.hp.HP3478A)

- [HP 8116A 50 MHz Pulse/Function Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8116A.html)
  - [`HP8116A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8116A.html#pymeasure.instruments.hp.HP8116A)

- [HP 8560A / 8561B Spectrum Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html)
  - [Generic Specific Attributes & Methods](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html#generic-specific-attributes-methods)
  - [HP8560A Specific Attributes & Methods](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html#hp8560a-specific-attributes-methods)
  - [HP8561B Specific Attributes & Methods](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html#hp8561b-specific-attributes-methods)
  - [Enumerations](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html#enumerations)

- [HP Signal generator HP8657B](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8657B.html)
  - [`HP8657B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8657B.html#pymeasure.instruments.hp.HP8657B)

- [HP 8753E Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8753E.html)
  - [`HP8753E`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8753E.html#pymeasure.instruments.hp.HP8753E)

- [HP 11713A Attenuator/Switch Driver](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html)
  - [`HP11713A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.HP11713A)
  - [`SwitchDriverChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.SwitchDriverChannel)
  - [`Attenuator_11dB`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.Attenuator_11dB)
  - [`Attenuator_110dB`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.Attenuator_110dB)
  - [`Attenuator_70dB_3_Section`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.Attenuator_70dB_3_Section)
  - [`Attenuator_70dB_4_Section`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.Attenuator_70dB_4_Section)

- [HP 437B Power Meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp437B.html)
  - [`HP437B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp437B.html#pymeasure.instruments.hp.HP437B)

- [Support class for HP legacy devices](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html)
  - [`HPLegacyInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html#pymeasure.instruments.hp.HPLegacyInstrument)

- [HP System Power Supplies HP663XA](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html)
  - [`HP6632A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html#pymeasure.instruments.hp.HP6632A)
  - [`HP6633A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html#pymeasure.instruments.hp.HP6633A)
  - [`HP6634A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html#pymeasure.instruments.hp.HP6634A)

## HP 8753E Vector Network Analyzer

### HP 8753E Vector Network Analyzer

 *class *pymeasure.instruments.hp.HP8753E(*adapter=None*, *name=None*, *min_frequency=30000.0*, *max_frequency=6000000000.0*, *min_power=-70*, *max_power=10*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the HP8753E Vector Network Analyzer and exposes a high-level interface for sweeps over scattering or measurement parameters.

Parameters:

-

**name** - Optionally set the instrument name (str). (default: `None`)

-

**min_frequency** - Optional minimum validator applied during initialization for HP8753E.start_frequency, HP8753E.stop_frequency, HP8753E.span_frequency, HP8753E.center_frequency (float in Hz). (default: `30000.0`)

-

**max_frequency** - Optional maximum validator applied during initialization for HP8753E.start_frequency, HP8753E.stop_frequency, HP8753E.span_frequency, HP8753E.center_frequency (float in Hz). (default: `6000000000.0`)

-

**min_power** - Optional minimum validator applied to HP8753E.power during initialization (float in dBm). (default: `-70`)

-

**max_power** - Optional maximum validator applied to HP8753E.power during initialization (float in dBm). (default: `10`)

 *property *IFBW*: Any*

For a scan sweep, set the instrument IF Bandwidth. (int allowed in [10, 30, 100, 300, 1000, 3000, 3700, 6000]).

 *property *averages*: Any*

Set the average count for a scan sweep. (int truncated from 1 to 999).

 *property *averaging_enabled*: Any*

Enable or disable averaging. (boolean)

 averaging_restart()

Restart sweep averaging.

 *property *center_frequency*: Any*

Set the center frequency in Hz (float).(dynamic)

 *property *correction_enabled*: Any*

Enable or disable correction. (boolean)

 *property *data_complex

Read the complex s-parameter measurements from the most recent scan. The call blocks until completion.

Parameters:

**timeout** - Optional wait value in seconds before timing out. (default: `10`)

Raises:

**TimeoutError** - Raised when the VNA does not complete the sweep before timeout occurs.

Returns:

Returns an array of s-parameters for the measurement_parameter.

Return type:

numpy.ndarray

 emit_beep()

Make the VNA beep

 *property *frequencies

Return the frequency list from the last scan.

Returns:

Return an array of frequencies sized by number of points in sweep)

Return type:

numpy.ndarray

 *property *fw

Return the instrument firmware.

 *property *id*: Any*

Return the instrument identification (list of strings)

 *property *manu

Return the instrument manufacturer.

 *property *measuring_parameter

Read which Scattering or Measuring Parameter is currently selected. (str from ['S11', 'S21', 'S12', 'S22', 'A', 'B', 'R'])

 *property *model

Return the instrument model.

 *property *options*: Any*

Return the options installed on the instrument

 *property *output_enabled*: Any*

Control RF Output State (boolean)

 *property *power*: Any*

Set the output RF power for the instrument's active port. (float).(dynamic)

 reset()

Reset the instrument. RF Output power may become enabled!

 scan(*timeout=10*)

Start a scan using the specified number of averages and block until completion.

Parameters:

**timeout** - Optional seconds added to the sweep time before timing out. (default: `10`)

Raises:

**TimeoutError** - Raised when the VNA does not complete the sweep before timeout occurs.

Returns:

None.

 *property *scan_points*: Any*

Choose the scan sweep point count. Allowed set [3, 11, 21, 26, 51, 101, 201, 401, 801, 1601]

 scan_single()

Start a single scan or N averaged scans based on averaging. This function is not blocking.

 set_fixed_frequency(*frequency*)

Configure the sweep as a fixed frequency in Hz.

 set_sweep_time_fastest()

Set the instrument scan sweep time to the fastest possible selection.

 shutdown()

Shutdown - Disables RF Output.

 *property *sn*: Any*

Return the serial number for the instrument

 *property *span_frequency*: Any*

Set the sweep frequency span in Hz (float).(dynamic)

 *property *start_frequency*: Any*

Set the start frequency in Hz. (float).(dynamic)

 *property *stop_frequency*: Any*

Set the stop frequency in Hz. (float).(dynamic)

 *property *sweep_time*: Any*

Set the sweep time in seconds. (float truncated from 0.0 to 36_400.0)

 *property *trigger_continuous*: Any*

Control Sweep Scan Trigger State (boolean)

 *property *trigger_hold*: Any*

Control Sweep Scan Trigger State (boolean)
