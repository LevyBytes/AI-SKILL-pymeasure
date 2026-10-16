# pymeasure.instruments.lecroy.lecroyT3DSO1204.LeCroyT3DSO1204Channel.trigger_level2

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_level2*: Any*

Set the lower trigger level voltage for the specified source (float). Runt/slope triggers use both higher and lower trigger levels. When setting the trigger level, divide it by the probe attenuation. This behavior is not documented in the datasheet and is probably a scope firmware bug. Out-of-range values are adjusted to the nearest legal value.
