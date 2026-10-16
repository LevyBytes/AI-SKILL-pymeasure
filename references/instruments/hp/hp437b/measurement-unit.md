# pymeasure.instruments.hp.HP437B.measurement_unit

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *measurement_unit*: Any*

Return the measurement unit currently used by the power meter for reported power values.

Dependency: `relative_mode_enabled` and attr:linear_display_enabled

```python
from pymeasure.instruments.hp.hp437b import MeasurementUnit

instr.relative_mode_enabled = False
instr.linear_display_enabled = True

assert instr.measurement_unit == MeasurementUnit.WATTS

```

## Related property contracts

- Open when checking pymeasure.instruments.hp.HP437B.offset: [offset](offset.md).
