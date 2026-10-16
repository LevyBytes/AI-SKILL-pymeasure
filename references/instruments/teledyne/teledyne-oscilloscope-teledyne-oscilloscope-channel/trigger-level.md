# pymeasure.instruments.teledyne.teledyne_oscilloscope.TeledyneOscilloscopeChannel.trigger_level

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_level*: Any*

Set the trigger level voltage for the active trigger source as a float.

When two trigger levels are required, this command sets the higher trigger level voltage for the chosen source. `trigger_level2` sets the lower trigger level voltage.

When assigning the trigger level, divide it by probe attenuation. The datasheet does not document this behavior, so it is likely a scope firmware bug. Values outside the permitted range are clipped to the nearest legal value.
