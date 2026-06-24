# Agilente4980

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Agilent E4980 LCR Meter; Agilent.

## Agilent E4980 LCR Meter

### Agilent E4980 LCR Meter

Class entry for `pymeasure.instruments.agilent.AgilentE4980(adapter, name='Agilent E4980A/AL LCR meter', **kwargs)`.

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Python representation for the E4980A/AL LCR meter.

 *property *ac_current*: Any*

AC current level, in Amps

 *property *ac_voltage*: Any*

AC voltage level, in Volts

 aperture(*time=None*, *averages=1*)

Set and get aperture.

Parameters:

-

**time** - integration-time setting supplied as a string: SHORT, MED, or LONG; matching ignores case. Use `None` to read the current values (default: `None`).

-

**averages** - numeric count of readings to average together (default: `1`).

 freq_sweep(*freq_list*, *return_freq=False*)

Execute a frequency-list sweep with sequential triggering.

Parameters:

-

**freq_list** – list of frequencies

-

**return_freq** - when True, include the frequency values reported by the instrument in the return data (default: `False`).

Returned measurements follow the active `mode` configuration.

 *property *frequency*: Any*

AC frequency in Hertz; the available range depends on the model.

 *property *impedance*: Any*

Measurement channels A and B, interpreted using `mode`.

 *property *mode*: Any*

Select quantities to be measured:

>
-

CPD: Parallel capacitance [F] paired with dissipation factor [number].

-

CPQ: Parallel capacitance [F] paired with quality factor [number].

-

CPG: Parallel capacitance [F] paired with parallel conductance [S].

-

CPRP: Parallel capacitance [F] paired with parallel resistance [Ohm].

-

CSD: Series capacitance [F] paired with dissipation factor [number].

-

CSQ: Series capacitance [F] paired with quality factor [number].

-

CSRS: Series capacitance [F] paired with series resistance [Ohm].

-

LPD: Parallel inductance [H] paired with dissipation factor [number].

-

LPQ: Parallel inductance [H] paired with quality factor [number].

-

LPG: Parallel inductance [H] paired with parallel conductance [S].

-

LPRP: Parallel inductance [H] paired with parallel resistance [Ohm].

-

LSD: Series inductance [H] paired with dissipation factor [number].

-

LSQ: Seriesinductance [H] paired with quality factor [number].

-

LSRS: Series inductance [H] paired with series resistance [Ohm].

-

RX: Resistance [Ohm] paired with reactance [Ohm].

-

ZTD: Impedance magnitude [Ohm] paired with phase [deg].

-

ZTR: Impedance magnitude [Ohm] paired with phase [rad].

-

GB: Conductance [S] paired with susceptance [S].

-

YTD: Admittance magnitude [Ohm] paired with phase [deg].

-

YTR: Admittance magnitude [Ohm] paired with phase [rad].

 *property *trigger_source*: Any*

Choose the trigger source from the accepted values:

-

HOLD: manual

-

INT: internal

-

BUS: external bus (GPIB/LAN/USB)

-

EXT: external connector

## Agilent

### Agilent

This section documents the Agilent instruments that currently have PyMeasure implementations. For an unsupported instrument, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

When the needed instrument is absent from this Agilent list, also review [HP](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/index.html) for older hardware and [Keysight](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/index.html) for newer hardware.

- [Agilent 8257D Signal Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent8257D.html)
  - [`Agilent8257D`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent8257D.html#pymeasure.instruments.agilent.Agilent8257D)

- [Agilent 8722ES Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent8722ES.html)
  - [`Agilent8722ES`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent8722ES.html#pymeasure.instruments.agilent.Agilent8722ES)

- [Agilent E4408B Spectrum Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE4408B.html)
  - [`AgilentE4408B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE4408B.html#pymeasure.instruments.agilent.AgilentE4408B)

- [Agilent E4980 LCR Meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE4980.html)
  - [`AgilentE4980`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE4980.html#pymeasure.instruments.agilent.AgilentE4980)

- [Agilent E5062A Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5062A.html)
  - [`AgilentE5062A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5062A.html#pymeasure.instruments.agilent.AgilentE5062A)
  - [`VNAChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5062A.html#pymeasure.instruments.agilent.agilentE5062A.VNAChannel)
  - [`VNATrace`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5062A.html#pymeasure.instruments.agilent.agilentE5062A.VNATrace)

- [Agilent 34410A Multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent34410A.html)
  - [`Agilent34410A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent34410A.html#pymeasure.instruments.agilent.Agilent34410A)

- [HP/Agilent/Keysight 34450A Digital Multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent34450A.html)
  - [`Agilent34450A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent34450A.html#pymeasure.instruments.agilent.Agilent34450A)

- [Agilent 4155/4156 Semiconductor Parameter Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html)
  - [`Agilent4156`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.Agilent4156)
  - [`AgilentMeasurementChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.AgilentMeasurementChannel)
  - [`SMU`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.SMU)
  - [`VAR1`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.VAR1)
  - [`VAR2`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.VAR2)
  - [`VARD`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.VARD)
  - [`VARX`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.VARX)
  - [`VMU`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.VMU)
  - [`VSU`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html#pymeasure.instruments.agilent.agilent4156.VSU)

- [Agilent 4294A Precision Impedance Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4294A.html)
  - [`Agilent4294A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4294A.html#pymeasure.instruments.agilent.Agilent4294A)

- [Agilent 33220A Arbitrary Waveform Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33220A.html)
  - [`Agilent33220A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33220A.html#pymeasure.instruments.agilent.Agilent33220A)

- [Agilent 33500 Function/Arbitrary Waveform Generator Family](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33500.html)
  - [`Agilent33500`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33500.html#pymeasure.instruments.agilent.Agilent33500)

- [Agilent 33521A Function/Arbitrary Waveform Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33521A.html)
  - [`Agilent33521A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33521A.html#pymeasure.instruments.agilent.Agilent33521A)
  - [`Agilent33500Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33521A.html#pymeasure.instruments.agilent.agilent33500.Agilent33500Channel)

- [Agilent B1500 Semiconductor Parameter Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB1500.html)
  - [General Information](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB1500.html#general-information)
  - [Examples](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB1500.html#examples)
  - [Main Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB1500.html#main-classes)
  - [Supporting Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB1500.html#supporting-classes)

- [Agilent 4284A LCR Meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4284A.html)
  - [`Agilent4284A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4284A.html#pymeasure.instruments.agilent.Agilent4284A)
  - [`Agilent4284ACorrection`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4284A.html#pymeasure.instruments.agilent.agilent4284A.Agilent4284ACorrection)
  - [`Agilent4284ASpot`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4284A.html#pymeasure.instruments.agilent.agilent4284A.Agilent4284ASpot)

- [Agilent B2980 Series, Femto/Picoammeter Electrometer/High Resistance Meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB298x.html)
  - [`AgilentB2981`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB298x.html#pymeasure.instruments.agilent.AgilentB2981)
  - [`AgilentB2983`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB298x.html#pymeasure.instruments.agilent.AgilentB2983)
  - [`AgilentB2985`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB298x.html#pymeasure.instruments.agilent.AgilentB2985)
  - [`AgilentB2987`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB298x.html#pymeasure.instruments.agilent.AgilentB2987)
  - [`BatteryMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB298x.html#pymeasure.instruments.agilent.agilentB298x.BatteryMixin)

- [Agilent E5270B SMU mainframe](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5270B.html)
  - [`AgilentE5270B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5270B.html#pymeasure.instruments.agilent.AgilentE5270B)
  - [`Display`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5270B.html#pymeasure.instruments.agilent.agilentE5270B.Display)
  - [`SMUChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5270B.html#pymeasure.instruments.agilent.agilentE5270B.SMUChannel)

- [Agilent N8975A Noise Figure Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentN8975A.html)
  - [`AgilentN8975A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentN8975A.html#pymeasure.instruments.agilent.AgilentN8975A)
  - [`AgilentN8975AFrequency`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentN8975A.html#pymeasure.instruments.agilent.agilentN8975A.AgilentN8975AFrequency)
