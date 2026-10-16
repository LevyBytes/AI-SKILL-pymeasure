# pymeasure.instruments.lecroy.LeCroyT3DSO1204.control — control dynamic-property example and reserved-name warning

[Owning PyMeasure class, adapter and connection contract](overview.md) / [control signature, complete parameters and return type](control-parameters.md)

The dynamic parameter can be used as shown here:

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

Unexpected behavior can appear when using dynamic properties

Use care with dynamic properties, because class or instance attributes that match reserved naming patterns can produce unwanted side effects. Treat `property_param` as reserved for dynamic property control: `property` is the dynamic property name, such as `center_frequency`, and `param` is one of this method’s parameter names other than `dynamic` and `docs`, such as `values`.
