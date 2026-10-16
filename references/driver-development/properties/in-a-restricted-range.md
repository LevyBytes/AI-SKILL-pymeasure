# In a restricted range

For range-limited properties, use `strict_range` or `truncated_range`.

For example, when the Extreme 5000 only accepts voltages between -1 V and 1 V, the earlier property can be changed to use a strict validator for that interval.

```python
from pymeasure.instruments.validators import strict_range

from pymeasure.instruments.instrument import Instrument

Extreme5000.voltage = Instrument.control(
    ":VOLT?", ":VOLT %g",
    """Control the voltage in Volts (float strictly from -1 to 1).""",
    validator=strict_range,
    values=[-1, 1]
)

```

With that definition, assigning voltage outside the range raises ValueError.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 100
Traceback (most recent call last):
...
ValueError: Value of 100 is not in range [-1,1]

```

That behavior is useful when invalid input should be surfaced to the programmer. In some drivers, though, clipping the input to the permitted range is more convenient.

```python
from pymeasure.instruments.validators import truncated_range

from pymeasure.instruments.instrument import Instrument

Extreme5000.voltage = Instrument.control(
    ":VOLT?", ":VOLT %g",
    """Control the voltage in Volts (float from -1 to 1).

    Invalid voltages are truncated.
    """,
    validator=truncated_range,
    values=[-1, 1]
)

```

This version keeps assignments error-free and clips any out-of-bounds value to the nearest range boundary.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 100  # Executes ":VOLT 1"
>>> extreme.voltage
1.0

```
