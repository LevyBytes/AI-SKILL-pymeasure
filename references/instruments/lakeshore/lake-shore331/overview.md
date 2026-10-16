# pymeasure.instruments.lakeshore.LakeShore331

*class *pymeasure.instruments.lakeshore.LakeShore331(*adapter*, *name='Lakeshore Model 331 Temperature Controller'*, *read_termination='\r\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Lake Shore 331 Temperature Controller for instrument access through a high-level interface. The 331 includes two input channels (A and B) plus two output channels (1 and 2). This driver uses the [LakeShore Channel Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#lakeshorechannels).

```python
from pymeasure.instruments.lakeshore import LakeShore331

controller = LakeShore331("GPIB::1")

print(controller.output_1.setpoint)         # Print the current setpoint for loop 1
controller.output_1.setpoint = 50           # Change the loop 1 setpoint to 50 K
controller.output_1.heater_range = 'low'    # Change the heater range to low.
controller.input_A.wait_for_temperature(target=50)   # Wait for the temperature to stabilize.
print(controller.input_A.kelvin)             # Print the temperature at sensor A.

```

Deprecated since version 0.16.0: LakeShore3xx is the replacement.
