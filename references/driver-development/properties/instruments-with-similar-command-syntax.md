# Instruments with similar command syntax

Dynamic properties can also preserve compatibility across instruments whose command syntax differs, as in this example.

```python
from pymeasure.instruments import Instrument

class MultimeterA(Instrument):
    voltage = Instrument.measurement(
        "VOLT?", "Measured voltage in volts.", dynamic=True
    )


class MultimeterB(MultimeterA):
    # Same as brand A multimeter, but the command to read voltage
    # is slightly different
    voltage_get_command = "VOLTAGE?"

```

In this example, `MultimeterA` and `MultimeterB` use different voltage-read commands while all other behavior stays the same. Define `MultimeterB` by subclassing `MultimeterA` and implementing only that difference.
