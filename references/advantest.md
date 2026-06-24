# Advantestr3767Cg

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Advantest; Advantest R3767CG Vector Network Analyzer.

## Advantest

### Advantest

This section documents the implemented Advantest instruments. For an instrument that is not yet listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Advantest R3767CG Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR3767CG.html)
  - [`AdvantestR3767CG`](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR3767CG.html#pymeasure.instruments.advantest.advantestR3767CG.AdvantestR3767CG)

- [Advantest R6245/R6246 DC Voltage/Current Sources/Monitors](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR624X.html)
  - [Main Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR624X.html#main-classes)
  - [General Information](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR624X.html#general-information)
  - [Examples](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR624X.html#examples)

## Advantest R3767CG Vector Network Analyzer

### Advantest R3767CG Vector Network Analyzer

 *class *pymeasure.instruments.advantest.advantestR3767CG.AdvantestR3767CG(*adapter*, *name='Advantest R3767CG'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Advantest R3767CG VNA and provides controls for adjusting the analysis range and reading trace data.

 *property *center_frequency*: Any*

Control the center frequency, using Hz.

 *property *id*: Any*

Get the instrument identification.

 *property *span_frequency*: Any*

Control the span of the frequency range in Hz.

 *property *start_frequency*: Any*

Control the start value for frequency in Hz.

 *property *stop_frequency*: Any*

Control the stop value for frequency in Hz.

 *property *trace_1*: Any*

Return the formatted data array from trace 1.
