# The property factories

PyMeasure provides three main convenience factories for class properties: [`CommonBase.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), [`CommonBase.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement), and [`CommonBase.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting). They are also available through the shorter `Instrument.control`, `Instrument.measurement`, and `Instrument.setting` names.

[`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement) creates a read-only property for retrieving data from an instrument. Suppose our Extreme 5000 implements `:TEMP?`; the property below can be placed after `def __init__` in the earlier class example, or attached to the class later as shown here:

```python
from pymeasure.instruments.instrument import Instrument

Extreme5000.cell_temp = Instrument.measurement(
   ":TEMP?",
   """Measure the temperature of the reaction cell.""",
)

```

A documentation string must be supplied; see [Docstrings](https://pymeasure.readthedocs.io/en/latest/dev/coding_standards.html#docstrings) for the relevant convention.

Using this property returns the temperature of the reaction cell.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.cell_temp  # Sends ":TEMP?" to the device
127.2

```

[`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) builds on that pattern by producing a property that supports both reads and writes. If our Extreme 5000 exposes `:VOLT?` plus `:VOLT <float>` commands expressed in Volts, the property can be written this way.

```python
from pymeasure.instruments.instrument import Instrument

Extreme5000.voltage = Instrument.control(
    ":VOLT?", ":VOLT %g",
    """Control the voltage in Volts (float)."""
)

```

Here `%g` is the [Python string format](https://docs.python.org/3/library/string.html#format-specification-mini-language) specifier used to pass values through as floating-point text.

With this property, assigning 100 mV sends the correct voltage command; reading it afterwards asks the instrument for the present voltage:

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 0.1        # Sends ":VOLT 0.1" to set the voltage to 100 mV
>>> extreme.voltage              # Sends ":VOLT?" to query for the current value
0.1

```

The remaining factory, [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting), creates write-only properties.

Together, [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement), and [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting) let instrument classes expose many routine measurement and control points as properties.

The following sections cover other property-factory capabilities: limiting accepted ranges, translating between physical values and command values, and applying heavier processing to data returned by a device.
