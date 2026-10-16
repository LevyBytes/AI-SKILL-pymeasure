# Using multiple values

Occasionally one command needs to send or receive several values. [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) supports this by taking multiple values as a tuple. If the Extreme 5000 sets voltage and frequency through `:VOLTFREQ?` and `:VOLTFREQ <float>,<float>`, the property could look like this:

```python
from pymeasure.instruments.instrument import Instrument

Extreme5000.combination = Instrument.control(
    ":VOLTFREQ?", ":VOLTFREQ %g,%g",
    """Simultaneously control the voltage in Volts and the frequency in Hertz (both float).

    This property is set by a tuple.
    """
)

```

Using that property, set 200 mV for voltage and 931 Hz for Frequency, then read the pair back right away.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.combination = (0.2, 931)        # Executes ":VOLTFREQ 0.2,931"
>>> extreme.combination                     # Reads ":VOLTFREQ?"
[0.2, 931.0]

```

The interface is awkward, but the pattern is rarely required.
