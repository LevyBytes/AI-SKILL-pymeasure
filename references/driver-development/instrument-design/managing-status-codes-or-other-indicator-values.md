# Managing status codes or other indicator values

Instruments often expose one or more sets of specific values that indicate status, mode, or allowed configuration choices. These are usually stored as some kind of mapping, because the user should see clear values while the raw data is hidden; think `ACQUISITION_MODE` rather than `0x04`. Keep the mappings at module level, not inside the instrument class, so property factories can access them. This is a minor downside of Python class attributes.

A plain `dict` is the simplest mapping approach. Often, though, Python `enum.Enum` is better. As the [Python documentation](https://docs.python.org/3.11/howto/enum.html) puts it,
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
from pymeasure.instruments.instrument import Instrument

status = Instrument.measurement(
    "STB?",
    """Measure the status of the device as enum.""",
    get_process=lambda v: ErrorCode(v),
)

```
