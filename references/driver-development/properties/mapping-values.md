# Mapping values

After the validators are clear, maps provide another way to satisfy instruments that expect non-physical command values. Enable that behavior with the `map_values` argument of [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control).

When the allowed values are supplied as a list, the command uses the matching list index. For example, if the Extreme 5000 instead expects `:RANG <integer>`, where 0, 1, and 2 mean 10 mV, 100 mV, and 1 V, this control works:

```python
from pymeasure.instruments.validators import truncated_discrete_set

from pymeasure.instruments.instrument import Instrument

Extreme5000.voltage = Instrument.control(
    ":RANG?", ":RANG %d",
    """Control the voltage range in Volts (float in 10 mV, 100 mV and 1 V).
    """,
    validator=truncated_discrete_set,
    values=[10e-3, 100e-3, 1],
    map_values=True
)

```

In that case, setting 100 mV produces the actual GPIB/SCIP command `:RANG 1`, because 100 mV is at index 1 in the values list.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 100e-3
>>> extreme.read()
'1'
>>> extreme.voltage = 1
>>> extreme.voltage
1

```

Dictionaries make the real-value to instrument-value mapping less constrained. If `:RANG <integer>` instead uses 1, 2, and 3 for 10 mV, 100 mV, and 1 V, replace the previous control with this version.

```python
from pymeasure.instruments.validators import truncated_discrete_set

from pymeasure.instruments.instrument import Instrument

Extreme5000.voltage = Instrument.control(
    ":RANG?", ":RANG %d",
    """Control the voltage range in Volts (float in 10 mV, 100 mV and 1 V).
    """,
    validator=truncated_discrete_set,
    values={10e-3:1, 100e-3:2, 1:3},
    map_values=True
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 10e-3
>>> extreme.read()
'1'
>>> extreme.voltage = 100e-3
>>> extreme.voltage
0.1

```

Here the dictionary associates each key with a particular value. Keys and values may be any type, which also supports string-valued properties:

```python
from pymeasure.instruments.validators import strict_discrete_set

from pymeasure.instruments.instrument import Instrument

Extreme5000.channel = Instrument.control(
    ":CHAN?", ":CHAN %d",
    """Control the measurement channel (string strictly in 'X', 'Y', 'Z').""",
    validator=strict_discrete_set,
    values={'X':1, 'Y':2, 'Z':3},
    map_values=True
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.channel = 'X'
>>> extreme.read()
'1'
>>> extreme.channel = 'Y'
>>> extreme.channel
'Y'

```

As shown above, validators and maps can make [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) cover substantially more cases.
