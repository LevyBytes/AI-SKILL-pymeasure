# Instrument, Solutions

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Scope covered: File structure; Solutions for implementation challenges.

## File structure

### File structure

Your new instrument belongs under the directory for its manufacturer. For example, when adding an "Extreme 5000" instrument and treating "Extreme" as the manufacturer, add the files shown below. Keep every filename lowercase so package names remain visually distinct from CamelCase Python classes.

```none
pymeasure/pymeasure/instruments/extreme/
    |--> __init__.py
    |--> extreme5000.py

```

### Updating the init file

Inside the manufacturer's `__init__.py`, import every instrument for that manufacturer so those instrument files can be imported conveniently.

### Add test files

For each instrument, pytest test files are strongly recommended because they verify behavior and make later changes safer. Writing tests for new code as Test Driven Development supports faster, cleaner programming by exposing errors early.

```none
pymeasure/tests/instruments/extreme/
    |--> test_extreme5000.py

```

### Adding documentation

Each instrument must have documentation, both as a requirement and to explain the implemented features to other users. Create a new reStructuredText file in the documentation.

```none
pymeasure/docs/api/instruments/extreme/
    |--> index.rst
    |--> extreme5000.rst

```

Start from an existing instrument documentation file; that copied pattern will auto-generate the instrument docs. In `index.rst`, link to the `extreme5000` file. When the manufacturer is new, also add that manufacturer in `pymeasure/docs/api/instruments/index.rst`.

### Instrument file

Every standard instrument should subclass [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument). That base supplies the core behavior for using [`Adapters`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter), which handle the real communication.

For the "Extreme 5000" example, the simplest instrument begins this way:

```python

# This file is part of the PyMeasure package.

# Copyright (c) 2013-2026 PyMeasure Developers

# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:

# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.

from pymeasure.instruments import Instrument

```

A minimal instrument definition is:

```python
class Extreme5000(Instrument):
    """Control the imaginary Extreme 5000 instrument."""

    def __init__(self, adapter, name="Extreme 5000", **kwargs):
        super().__init__(
            adapter,
            name,
            **kwargs
        )

```

Add the PyMeasure license to every file, and list yourself as an author in `AUTHORS.txt`.

Instrument classes are easier to read when their elements follow this order:

-

Place the initializer, the `__init__()` method, first so it is quick to locate while reading the source code.

-

After that, add class attributes/variables when you need them.

-

Next come properties, either pymeasure-specific or ordinary Python versions; this section usually contains most of the implementation.

-

Finally, any methods.

### Your instrument’s user interface

An instrument exposes properties and methods to users; those members should be visible through the documentation and an editor's autocomplete.

Aside from standard SCPI properties such as `id`, you generally decide how to shape this interface. A few conventions have proven worth following:

-

Names matter. Choose clear, expressive, and unambiguous names for the elements on your instrument.

-

When pymeasure already has comparable instruments in the same "family" (for example, a power supply), follow those patterns where they apply. Prefer all power supplies using `current_limit` over a mixture such as `current_max`, `Ilim`, `max_curr`, etc.

-

When another instrument already uses a similar command set, consider inheriting from it and changing only the few differences. That greatly cuts duplicate code and maintenance load. The [Instruments with similar features](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#instruments-with-similar-features) section explains the approach.

-

Most of an instrument interface will likely consist of properties for quantities that are set, read, or both. PyMeasure's custom properties (see [Writing properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#properties) ff. below) provide convenience behavior and are preferred, while plain Python properties remain acceptable.

-

"Actions", commands, or verbs normally belong as methods rather than properties: `recall()`, `trigger_scan()`, `prepare_resistance_measurement()`, etc.

-

Keeping properties separate from methods also supports the ["command-query separation" principle](https://en.wikipedia.org/wiki/Command%E2%80%93query_separation).

-

For instruments with multiple identical channels, consult [Instruments with channels](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#channels).

You may define whatever methods are needed to interact with the instrument. In those methods, send commands through `self.ask(command)`, `self.write(command)`, and `self.read()` rather than directly invoking the adapter. If communication requires modified sent or received commands, override these methods in the instrument; see [Advanced communication protocols](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#advanced-communication-protocols) for more information.

The project has accumulated best practices that make instruments simpler to author and maintain. The following sections describe them, and following them is strongly encouraged.

### Common instrument types

Many instruments fall into common categories. In the future, pymeasure is expected to add a category-based abstraction layer; see [this issue](https://github.com/pymeasure/pymeasure/issues/416). Until then, use these guidelines for a more uniform API. Some current instruments do not follow them yet, but they are expected to be harmonized later.

### Generic types mixins

The [generic_types](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html) module provides mixin classes for shared instrument types. For instance, an instrument that follows SCPI standards can include [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin):

```python
from pymeasure.instruments.generic_types import SCPIMixin

class SomeSCPIInstrument(SCPIMixin, Instrument):
    """This instrument has properties and methods defined for all SCPI instruments"""

```

This mixin supplies default SCPI properties such as [`id`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.id) and [`status`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.status), plus default methods such as [`clear()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.clear) and [`reset()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.reset), to `SomeSCPIInstrument`.

To verify whether your instrument can safely inherit from [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), run `pytest -k scpi_mixin --device-address "<instrument-address>"`.

### Frequent properties

When an instrument provides an **output** that can be turned on and off, implement it as a [boolean property](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#boolean-properties) named `output_enabled`.

### Power supplies

For PSUs, the *actual* current and voltage are usually measurable, while voltage level and current limit are configurable settings. To keep names clear and avoid ambiguity, use `current`, `voltage`, `voltage_setpoint`, and `current_limit`, respectively.

### Managing status codes or other indicator values

Instruments often expose one or more sets of specific values that indicate status, mode, or allowed configuration choices. These are usually stored as some kind of mapping, because the user should see clear values while the raw data is hidden; think `ACQUISITION_MODE` rather than `0x04`. Keep the mappings at module level, not inside the instrument class, so property factories can access them. This is a minor downside of Python class attributes.

A plain `dict` is the simplest mapping approach. Often, though, Python `enum.Enum` is better. As the [Python documentation](https://docs.python.org/3.11/howto/enum.html) puts it,

>

An Enum contains symbolic names assigned to unique values. Compared with global variables, it provides a better `repr()`, grouping, type-safety, and additional features.

Because these signal values are frequently integers, `IntEnum` and `IntFlag` are the most suitable enum types.

`IntEnum` behaves like `Enum`, except its members are integers too and work anywhere an integer works, making command composition transparent while keeping surrounding logic/code easier to read. Starting with Python version 3.11, printing `IntEnum` and `IntFlag` returns the numeric value; to get the symbolic name, print its `repr`, use the `.name` property, or return the value in a REPL.

```pycon
>>> from enum import IntEnum
>>> class InstrMode(IntEnum):
...     WAITING = 0x00
...     HEATING = 0x01
...     COOLING = 0x05
...
>>> received_from_device = 0x01
>>> current_mode = InstrMode(received_from_device)
>>> if current_mode == InstrMode.WAITING:
...     print('Idle')
... else:
...     current_mode
...     print(repr(current_mode))
...     print(f'Mode value: {current_mode}')
...
<InstrMode.HEATING: 1>
<InstrMode.HEATING: 1>
Mode value: 1

```

`IntFlag` additionally supports bitwise operators and combinations, which makes it suitable for status bitmasks or error codes that can hold multiple values:

```pycon
>>> from enum import IntFlag
>>> class ErrorCode(IntFlag):
...     TEMP_OUT_OF_RANGE = 8
...     TEMPSENSOR_FAILURE = 4
...     COOLER_FAILURE = 2
...     HEATER_FAILURE = 1
...     OK = 0
...
>>> received_from_device = 7
>>> ErrorCode(received_from_device)
<ErrorCode.TEMPSENSOR_FAILURE|COOLER_FAILURE|HEATER_FAILURE: 7>

```

Many instruments use `IntFlags` for exactly that purpose.

A status property might be written like this:

```python
status = Instrument.measurement(
    "STB?",
    """Measure the status of the device as enum.""",
    get_process=lambda v: ErrorCode(v),
)

```

### Defining default connection settings

Instrument implementations sometimes need default connection settings. Reasons include a connection that needs *specific non-default settings* or an instrument that supports *multiple interfaces*.

[`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) supports handling connection settings flexibly inside the instrument initializer.

### Single interface

The simplest form, useful when default settings are needed, forwards all keyword arguments to the `Instrument` initializer, which passes them through to [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) when `adapter` is a string or integer.

```python
def __init__(self, adapter, name="Extreme 5000", **kwargs):
    super().__init__(
        adapter,
        name,
        **kwargs
    )

```

Put defaults in the signature when they should be obvious to users and may be overridden. This fits instruments with a single interface type, or defaults that are valid across every interface type; see [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) documentation for details.

```python
def __init__(self, adapter, name="Extreme 5000", baud_rate=2400, **kwargs):
    super().__init__(
        adapter,
        name,
        baud_rate=baud_rate,
        **kwargs
    )

```

When defaults are needed but do not need prominent exposure for replacement, use this pattern; it sets the value only if `kwargs` does not already contain an entry.

```python
def __init__(self, adapter, name="Extreme 5000", **kwargs):
    kwargs.setdefault('timeout', 1500)
    super().__init__(
        adapter,
        name,
        **kwargs
    )

```

### Multiple interfaces

With instruments that have multiple interfaces (e.g. serial, TCPI/IP, USB), the setup becomes more complex. Some settings may apply to every interface, such as `timeout`, while others are valid for only one interface type.

The useful pattern is to add keyword arguments named for interface types, such as `asrl` or `gpib` below; the full list is [here](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType). Each keyword then holds a *dictionary* of settings for that specific interface:

```python
def __init__(self, adapter, name="Extreme 5000", baud_rate=2400, **kwargs):
    kwargs.setdefault('timeout', 1500)
    super().__init__(
        adapter,
        name,
        gpib=dict(enable_repeat_addressing=False,
                  read_termination='\r'),
        asrl={'baud_rate': baud_rate,
              'read_termination': '\r\n'},
        **kwargs
    )

```

On instrument creation, settings for the interface actually in use are merged with `**kwargs` before being sent to PyVISA; settings for other interfaces are discarded. This keeps the forwarded argument set valid. Entries already present in `**kwargs**` take precedence, so users can *still* override any defaults from the instrument definition when necessary.

For many instruments, the first simple approach is sufficient. When the connection arrangement is more complex, check whether [Advanced communication protocols](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#advanced-communication-protocols) covers it. If an unusual connection type cannot be represented with PyVISA, you can implement your own Adapter.

## Solutions for implementation challenges

### Solutions for implementation challenges

The following list pairs less common implementation challenges with solutions and example instruments.

### General issues

-

With `%f`, small numbers (<1e-5) display as 0. If the instrument accepts exponential notation, use `%g`; it chooses floating point or exponential format based on the exponent.

### Communication protocol issues

-

When an instrument replies to every message, including setting commands, set the setting's `check_set_errors = True` parameter and redefine `check_set_errors()` so it reads the reply; see [`hcp.TC038D`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038d.html#pymeasure.instruments.hcp.TC038D)

-

Binary, frame-based communication, see [`hcp.TC038D`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038d.html#pymeasure.instruments.hcp.TC038D)

-

For replies that all share the same length, see [`aja.DCXS`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aja/DCXS.html#pymeasure.instruments.aja.DCXS)

-

For startup garbage messages that pollute the buffer, see [`aja.DCXS`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aja/DCXS.html#pymeasure.instruments.aja.DCXS)

-

When both an instrument and its channel must override values while still using the correct ask method, see [`tcpowerconversion.CXN`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tcpowerconversion/tccxn.html#pymeasure.instruments.tcpowerconversion.CXN)

### Channels

-

For channels that do not all provide identical features, see [`MKS937B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks937b.html#pymeasure.instruments.mksinst.mks937b.MKS937B)

-

When communication channel names (1, 2, 3) do not match the front panel labels (A, B, C), see [`AdvantestR624X`](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR624X.html#pymeasure.instruments.advantest.advantestR624X.AdvantestR624X)

-

For an instrument family where a channel property varies between family members, see [`AnritsuMS464xB`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.AnritsuMS464xB)

-

To document the type of an instrument's channels with a clickable link, review the source for the [Aim-TTI PL Series Power Supplies](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html#aimtti-landing-page) page.
