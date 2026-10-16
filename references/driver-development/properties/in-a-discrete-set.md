# In a discrete set

A control property often accepts only a small enumerated set. Use `strict_discrete_set` or `truncated_discrete_set` for that pattern. As with ranges, the strict form raises an error when the submitted value is absent from the set.

For example, suppose the Extreme 5000 provides `:RANG <float>` to choose a voltage range, with valid Volts values of 10 mV, 100 mV, and 1 V. A control property can be defined as follows.

```python
from pymeasure.instruments.validators import truncated_discrete_set

from pymeasure.instruments.instrument import Instrument

Extreme5000.voltage = Instrument.control(
    ":RANG?", ":RANG %g",
    """Control the voltage range in Volts (float in 10e-3, 100e-3, 1).""",
    validator=truncated_discrete_set,
    values=[10e-3, 100e-3, 1]
)

```

The voltage range can now be assigned, and unsuitable inputs are automatically truncated to a valid choice.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 0.08
>>> extreme.voltage
0.1

```
