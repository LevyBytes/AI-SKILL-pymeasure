# pymeasure.instruments.keysight.KeysightE36312A

Includes coverage for: Keysight E36312A Triple Output Power Supply; Keysight N5776C Power Supply.

## Keysight E36312A Triple Output Power Supply

### Keysight E36312A Triple Output Power Supply

 *class *pymeasure.instruments.keysight.KeysightE36312A(*adapter*, *name='Keysight E36312A'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Defines the Keysight E36312A Power supply interface used to communicate with the instrument.

```python
from pymeasure.instruments.keysight.keysightE36312A import KeysightE36312A

supply = KeysightE36312A(resource)
supply.ch_1.voltage_setpoint=10
supply.ch_1.current_setpoint=0.1
supply.ch_1.output_enabled=True
print(supply.ch_1.voltage)

```
