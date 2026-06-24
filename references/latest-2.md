# Introduction, Quick Start

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Introduction; Quick start.

## Introduction

### Introduction

PyMeasure communicates with scientific instruments through an object-oriented design. This gives users a clear interface while keeping low-level SCPI and GPIB commands out of everyday workflows. The emphasis stays on solving the measurement problems at hand rather than rebuilding instrument communication.

Instrument connections that use VISA (GPIB, Serial, etc) work via the [PyVISA package](https://pyvisa.readthedocs.io/en/latest/) behind the scenes. [Prologix GPIB](http://prologix.biz/) adapters work as well. Because the communication protocol is replaceable, instrument classes can operate interchangeably with every supported protocol.

Use [pint](https://pint.readthedocs.io) quantities when numbers and physical units (e.g. 5 meters) need to remain attached. This makes it straightforward to work across different orders of magnitude (meters and centimeters) or across different units (meters and feet).

Familiarity with [basic Python programming for the sciences](https://scipy-lectures.github.io/) and the concept of objects can be useful before working with PyMeasure.

### Instrument ready

PyMeasure ships with several [instrument definitions](https://pymeasure.readthedocs.io/en/latest/api/instruments/index.html) already available. They are grouped by the instrument manufacturer name. For example, the class for the [Keithley 2400 SourceMeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2400.html) is imported with:

```python
from pymeasure.instruments.keithley import Keithley2400

```

The [Tutorials](https://pymeasure.readthedocs.io/en/latest/tutorial/index.html) section provides more detail about [connecting to an instrument](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html). When the needed instrument is not available and you want to contribute, consult the documentation for [adding an instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

### Graphical displays

PyMeasure can generate graphical user interfaces (GUIs) to control measurement procedure execution. Those interfaces support live plotting for data and include a queue system for coordinating large numbers of experiments.

The [Using a graphical interface](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html) tutorial walks through these capabilities.

 (Figure: ManagedWindow Running Example)

The GUIs can work with more than the instruments bundled in this package. Any python instrument may be used. As an example, [this script](https://github.com/pymeasure/pymeasure/tree/master/examples/Basic/gui_foreign_instrument.py) shows use of an [InstrumentKit](https://instrumentkit.readthedocs.io) instrument.

## Quick start

### Quick start

This section gives the steps needed to start using PyMeasure quickly.

### Setting up Python

Using the [Anaconda distribution](https://www.anaconda.com/) is the simplest route for installing the Python environment PyMeasure needs; it includes 720 scientific packages. Compared with relying only on `pip`, this method has the benefit that Anaconda correctly installs the Qt libraries required by the GUI features.

Install the appropriate Python version of [Anaconda](https://www.anaconda.com/products/individual) for your operating system after downloading it.

### Installing PyMeasure

### Install with conda

With the [Anaconda distribution](https://www.anaconda.com/), the conda package manager can install PyMeasure along with every required dependency.

In a terminal, run the commands below; on Windows, open the Anaconda Prompt from the Start Menu.

```bash
conda config --add channels conda-forge
conda install pymeasure

```

The result is an installation of PyMeasure plus all required dependencies.

### Install with `pip`

`pip` is another supported way to install PyMeasure.

```bash
pip install pymeasure

```

To enable live-plotting and GUI support, install the `gui` extra together with a Qt binding:

```bash
pip install pymeasure[gui] PyQt5

```

Depending on your preference, `PyQt5` may be substituted with `PyQt6`, `PySide2`, or `PySide6`. A `conda` installation brings in Qt libraries automatically; a `pip` installation requires you to add one explicitly.

### Installing VISA

Instrument communication is usually handled through PyVISA, and PyVISA is installed automatically. Device communication still requires a VISA implementation. If that term is unfamiliar, install the pure-Python `pyvisa-py` package into the same installation used above. For additional detail, see [the PyVISA documentation](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html).

### Checking the version

After Python and PyMeasure are installed, open your python environment (e.g. a REPL or Jupyter notebook) and check the installed version. Run the following Python code.

```python
import pymeasure
pymeasure.__version__

```

The PyMeasure version should be printed. With PyMeasure installed, you can begin using it. Ready to [connect to an instrument](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html)?
