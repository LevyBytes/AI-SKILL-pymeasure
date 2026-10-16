# Dynamic validity range

Consider an instrument whose accepted value range changes with current state. The following code demonstrates that situation using dynamic properties.

```python
from pymeasure.instruments.validators import strict_range

from pymeasure.instruments.instrument import Instrument

Extreme5000.voltage = Instrument.control(
    ":VOLT?", ":VOLT %g",
    """Control the voltage in Volts (float).""",
    validator=strict_range,
    values=[-1, 1],
    dynamic = True,
)
def set_bipolar_mode(self, enabled = True):
    """Safely switch between bipolar/unipolar mode."""

    # some code to switch off the output first
    # ...

    if enabled:
        self.mode = "BIPOLAR"
        # set valid range of "voltage" property
        self.voltage_values = [-1, 1]
    else:
        self.mode = "UNIPOLAR"
        # note the "propertyname_parametername" form of the attribute
        self.voltage_values = [0, 1]

```

The voltage property now switches between the dynamic ranges [-1, 1] and [0, 1]. Because the range can change, the property's docstring should stay general and avoid details such as the active admissible value range. Here the property was named `voltage`, the adjustable parameter was `values`, and `self.voltage_values` supplied the chosen range.
