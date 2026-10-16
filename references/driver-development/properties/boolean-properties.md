# Boolean properties

Maps also work well for boolean-style properties, letting the public interface use Pythonic `True` and `False` values:

```python
from pymeasure.instruments.validators import strict_discrete_set

from pymeasure.instruments.instrument import Instrument

Extreme5000.output_enabled = Instrument.control(
    "OUTP?", "OUTP %d",
    """Control the instrument output is enabled (boolean).""",
    validator=strict_discrete_set,
    map_values=True,
    values={True: 1, False: 0},  # the dict values could also be "on" and "off", etc. depending on the device
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.output_enabled = True
>>> extreme.read()
'1'
>>> extreme.output_enabled = False
>>> extreme.output_enabled
False
>>> # Invalid input raises an exception
>>> extreme.output_enabled = 34
Traceback (most recent call last):
...
ValueError: Value of 34 is not in the discrete set {True: 1, False: 0}

```

For boolean property names, choose wording that could answer a yes/no question, such as Is the output enabled? -> `output_enabled`, `display_active`, etc.
