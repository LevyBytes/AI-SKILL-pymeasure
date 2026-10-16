# pymeasure.instruments.advantest.advantestR624X.SMUChannel.voltage_pulsed_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

voltage_pulsed_sweep(*sweep_mode*, *repeat*, *voltage_range*, *base*, *start_value*, *stop_value*, *steps*, *current_compliance*, *bias=0*)

For pulse wave (linear/log) voltage sweep (`PWV`), configure bias value, current compliance, number of steps, stop value, start value, base value, generation range, repeat count, and sweep mode.

Note

- These restrictions apply to sweep mode, number of refreshes, and number of steps:
  - Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.
    - For output data output method 1 or 2 selected by the OFM command, keep m x number of refreshes x N <= 2048.

    - If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

- For current compliance polarity, the compliance setting is applied to both polarities (+ and -), independent of the requested polarity.

- The instrument selects the smallest current compliance range that contains the configured value.

Warning

For pulsed sweeps, `measure_current()` must be used with a fixed range, for example `CurrentRange.FIXED_BEST`. Auto ranges are unsupported and cause error 00211.
