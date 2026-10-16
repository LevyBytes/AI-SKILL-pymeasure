# Processing of set values

[`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) and [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting) accept the keyword argument set_process. It must be a function that receives the value after validation, transforms it before value mapping, and returns the transformed value. Unit conversion is a typical use, as this example shows:

```python
from pymeasure.instruments.validators import strict_range

from pymeasure.instruments.instrument import Instrument

Extreme5000.current = Instrument.setting(
    ":CURR %g",
    """Set the measurement current in A (float strictly from 0 to 10).""",
    validator=strict_range,
    values=[0, 10],
    set_process=lambda v: 1e3*v,  # convert current to mA
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.current = 1  # set current to 1000 mA

```
