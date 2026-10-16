# pymeasure.instruments.hp.HP8560A.source_leveling_control

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *source_leveling_control*: Any*

Choose whether the built-in tracking generator uses internal or external leveling. Accepts ‘INT’, ‘EXT’, or members of the `SourceLevelingControlMode` enumeration

Type: `str`

```python
from pymeasure.instruments.hp.hp856Xx import SourceLevelingControlMode

instr.preset()
instr.sweep_single()
instr.center_frequency = 300e6
instr.span = 1e6

instr.source_power = -5

instr.trigger_sweep()
instr.source_leveling_control = SourceLevelingControlMode.External

if ErrorCode(900) in instr.errors:
    print("UNLEVELED CONDITION. CHECK LEVELING LOOP.")

```

Note

Available only with an HP 8560A Option 002.
