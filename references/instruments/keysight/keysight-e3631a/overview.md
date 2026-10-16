# pymeasure.instruments.keysight.KeysightE3631A

Covers: APIs for Keysight E3631A Triple Output Power Supply; Keysight N5767A Power Supply.

## Keysight E3631A Triple Output Power Supply

### Keysight E3631A Triple Output Power Supply

 *class *pymeasure.instruments.keysight.KeysightE3631A(*adapter*, *name='Keysight E3631A'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Interface wrapper for controlling and querying a Keysight E3631A Triple Output DC Power Supply.

```python
from pymeasure.instruments.keysight.keysightE3631A import KeysightE3631A

supply = KeysightE3631A(resource)
supply.ch_1.voltage_setpoint=10
supply.ch_1.current_setpoint=0.1
supply.ch_1.output_enabled=True
print(supply.ch_1.voltage)

```
