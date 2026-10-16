# pymeasure.instruments.hp.hp856Xx.HP856Xx.request_service_conditions

HP856Xx.request_service_conditions

Set the bit mask that determines which service requests are allowed to interrupt a program sequence.

```python
from pymeasure.instruments.hp.hp856Xx import StatusRegister

instr.request_service_conditions = StatusRegister.ERROR_PRESENT | StatusRegister.TRIGGER

print(instr.request_service_conditions)
assert instr.request_service_conditions == (StatusRegister.ERROR_PRESENT | StatusRegister.TRIGGER)

```
