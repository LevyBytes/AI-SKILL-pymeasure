# pymeasure.instruments.advantest.advantestR624X.SMUChannel.auto_zero_enabled

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *auto_zero_enabled*: Any*

Turn the auto zero option ON or OFF (bool) (`CM`).

Type:

bool

This command configures auto zero, which automatically calibrates the measured-value zero point.

1. Periodically perform auto zero.

2. Run auto zero one time, with no repeated auto zero operations afterward.

If auto zero mode is True, these operations occur.

- For DC operation and pulse operation:
  - At the end of a sweep, when more than 10 seconds have elapsed since the previous autozero, one autozero is performed.

  - If sweep start is requested during auto zero, the sweep begins after auto zero finishes.

- Sweep operation
  - Auto zero runs once per 10 seconds.

  - If measurement or pulse output is requested during auto zero, it runs after auto zero completes.
