# pymeasure.instruments.hp.HP437B.event_status

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *event_status*: Any*

Return the status byte together with the Master Summary Status bit.

For a connected HP437B named `instr`, inspect the event-status flags:

```python
from pymeasure.instruments.hp.hp437b import EventStatusRegister

status = instr.event_status
if status & EventStatusRegister.COMMAND_ERROR:
    print("The meter reported a command error.")
```
