# Introduction

Covers: Introduction; Quick start.

## Introduction

### Introduction

PyMeasure communicates with scientific instruments through an object-oriented design. This gives users a clear interface while keeping low-level SCPI and GPIB commands out of everyday workflows. The emphasis stays on solving the measurement problems at hand rather than rebuilding instrument communication.

Instrument connections that use VISA (GPIB, Serial, etc) work via the [PyVISA package](https://pyvisa.readthedocs.io/en/latest/) behind the scenes. [Prologix GPIB](http://prologix.biz/) adapters work as well. Because the communication protocol is replaceable, instrument classes can operate interchangeably with every supported protocol.

Use [pint](https://pint.readthedocs.io) quantities when numbers and physical units (e.g. 5 meters) need to remain attached. This makes it straightforward to work across different orders of magnitude (meters and centimeters) or across different units (meters and feet).

Familiarity with [basic Python programming for the sciences](https://scipy-lectures.github.io/) and the concept of objects can be useful before working with PyMeasure.
