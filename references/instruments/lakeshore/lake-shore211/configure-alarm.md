# pymeasure.instruments.lakeshore.LakeShore211.configure_alarm

[Owning PyMeasure class, adapter and connection contract](overview.md)

configure_alarm(*on=True*, *high_value=270.0*, *low_value=0.0*, *deadband=0*, *latch=False*)

Set the alarm parameters for the input.

Parameters:

- **on** - Boolean alarm setting, default True (default: `True`)

- **high_value** - High value used as the temperature check for alarm activation (default: `270.0`)

- **low_value** - Low value used as the temperature check for alarm activation (default: `0.0`)

- **deadband** - Value by which the temperature must change outside an alarm condition (default: `0`)

- **latch** - Determines whether the alarm latches (default: `False`)
