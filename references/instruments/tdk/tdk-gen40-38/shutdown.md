# pymeasure.instruments.tdk.tdk_gen40_38.TDK_Gen40_38.shutdown

[Owning PyMeasure class, adapter and connection contract](overview.md)

shutdown()

Safety shutdown the power supply.

Use `self.ramp_to_current(0.0)` to ramp the power supply to zero current, then switch output off.
