# Processing of return values

[`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) and [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement) likewise accept get_process. When provided, get_process must be a function that receives a value, processes it before value mapping, and returns the result. As with set_process, unit conversion is one use:

```python
from pymeasure.instruments.validators import strict_range

from pymeasure.instruments.instrument import Instrument

Extreme5000.current = Instrument.control(
    ":CURR?", ":CURR %g",
    """Control the measurement current in A (float strictly from 0 to 10).""",
    validator=strict_range,
    values=[0, 10],
    set_process=lambda v: 1e3*v,  # convert to mA
    get_process=lambda v: 1e-3*v,  # convert to A
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.current = 3.1
>>> extreme.current
3.1

```

set-process and get-process can also convert to or from a `pint.Quantity`. Adapting the previous example to set or return a quantity gives:

```python
from pymeasure.instruments.instrument import Instrument

from pymeasure.units import ureg

Extreme5000.current = Instrument.control(
    ":CURR?", ":CURR %g",
    """Control the measurement current (float).""",
    set_process=lambda v: v.m_as(ureg.mA),  # send the value as mA to the device
    get_process=lambda v: ureg.Quantity(v, ureg.mA),  # convert to quantity
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.current = 3.1 * ureg.A
>>> extreme.current.m_as(ureg.A)
3.1

```

Note

At present, this is the way quantities can be handled in pymeasure instruments. [Issue 666](https://github.com/pymeasure/pymeasure/issues/666) is tracking work on a more convenient quantity implementation for the property factories.

get_process is also suitable for text cleanup. For an instrument reply that includes a unit, such as `1.23 nF`, remove the unit before using the number; one implementation is:

```python
from pymeasure.instruments.instrument import Instrument

Extreme5000.capacity = Instrument.measurement(
    ":CAP?",
    """Measure the capacity in nF (float).""",
    get_process=lambda v: float(v.replace('nF', ''))
)

```

The preprocess_reply keyword argument to [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) or [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement) can perform the same job. This function is passed on to `Adapter.values` and executes immediately after the device reply arrives. Because the built-in casting behavior is then available, the code can be shortened:

```python
from pymeasure.instruments.instrument import Instrument

Extreme5000.capacity = Instrument.measurement(
    ":CAP?",
    """Measure the capacity in nF (float).""",
    preprocess_reply=lambda v: v.replace('nF', '')
    # notice how we don't need to cast to float anymore
)

```
