# Instrument family with different parameter values

A frequent pattern is an instrument family where each model shares the same interface but has different parameter ranges. In that case, update the class-specific range parameter without rewriting the property:

```python
from pymeasure.instruments.validators import strict_range

from pymeasure.instruments.instrument import Instrument

class FictionalInstrumentFamily(Instrument):
    frequency = Instrument.setting(
        "FREQ %g",
        """Set the frequency (float).""",
        validator=strict_range,
        values=[0, 1e9],
        dynamic=True,
        # ... other possible parameters follow
    )

    # ... complete class implementation here

class FictionalInstrument_1GHz(FictionalInstrumentFamily):
    pass

class FictionalInstrument_3GHz(FictionalInstrumentFamily):
    frequency_values = [0, 3e9]

class FictionalInstrument_9GHz(FictionalInstrumentFamily):
    frequency_values = [0, 9e9]

```

This makes each family member easy to derive from the shared class, with the adjusted attribute defined on the class rather than on each instance.
