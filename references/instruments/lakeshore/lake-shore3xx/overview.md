# pymeasure.instruments.lakeshore.LakeShore3xx

*class *pymeasure.instruments.lakeshore.LakeShore3xx(*adapter*, *name='Lakeshore Model 3xx Temperature Controller'*, *read_termination='\r\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models a Lake Shore Temperature Controller of the 3xx-Series with a high-level interface to the instrument. Multiple input-and output options are implemented. Not every channel exists in every device version. Some devices can use input option cards for additional input channels.

LS 331 and 335 provide two input channels (A and B) plus two output channels (1 and 2). LS 336 provides four input channels (A, B, C and D) plus four output channels (1, 2, 3 and 4).

LS 340 provides two input channels (A and B) and one output channel (1). Supported extension cards: * 3465 Single Capacitance Input Option Card: one added channel (C). * 3462 Dual Standard Input Option Card: two added channels (C and D). * 3464 Dual Thermocouple Input Option Card: two added channels (C and D). * 3468 Eight Channel Input Option Card: eight added channels (C1-C4, D1-D4).

LS 350 has input channels A, B, C and D (four total) and output channels 1, 2, 3 and 4 (four total). Supported extension card: * 3062 4-Channel Scanner option: D2, D3, D4, and D5 as 4 additional channels.

This driver uses the [LakeShore Channel Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#lakeshorechannels).

```python
from pymeasure.instruments.lakeshore.lakeshore3xx import LakeShore3xx

controller = LakeShore3xx("GPIB::1")

print(controller.output_1.setpoint)         # Print the current setpoint for loop 1
controller.output_1.setpoint = 50           # Change the loop 1 setpoint to 50 K
controller.output_1.heater_range = 'low'    # Change the heater range to low.
controller.input_A.wait_for_temperature()   # Wait for the temperature to stabilize.
print(controller.input_A.kelvin)            # Print the temperature at sensor A.

```
