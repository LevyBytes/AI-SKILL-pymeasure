# pymeasure.instruments.keysight.KeysightE36312A.control — control dynamic-property example and reserved-name warning

[Owning PyMeasure class, adapter and connection contract](overview.md) / [control signature, complete parameters and return type](control-parameters.md)

Dynamic parameter usage can follow this pattern:

```python
from pymeasure.instruments.validators import strict_range

from pymeasure.instruments.instrument import Instrument

class GenericInstrument(Instrument):
    center_frequency = Instrument.control(
        ":SENS:FREQ:CENT?;", ":SENS:FREQ:CENT %e GHz;",
        " A floating point property that represents the frequency ... ",
        validator=strict_range,
        # Redefine this in subclasses to reflect actual instrument value:
        values=(1, 20),
        dynamic=True  # enable changing property parameters on-the-fly
    )

class SpecificInstrument(GenericInstrument):
    # Identical to GenericInstrument, except for frequency range
    # Override the "values" parameter of the "center_frequency" property
    center_frequency_values = (1, 10) # Redefined at subclass level

instrument = SpecificInstrument()
instrument.center_frequency_values = (1, 6e9) # Redefined at instance level

```

Warning

Unexpected side effects from dynamic properties

Users need care with dynamic properties, because defining class and/or instance attributes with particular name patterns can create unwanted side effects. The reserved pattern is property_param, where property names the dynamic property (for example, center_frequency in the example) and param is any parameter name of this method except dynamic and docs (for example, values in the example); those names control dynamic property behavior.
