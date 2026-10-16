# pymeasure.instruments.advantest.advantestR624X.SMUChannel.voltage_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

voltage_sweep(*sweep_mode*, *repeat*, *voltage_range*, *start_value*, *stop_value*, *steps*, *current_compliance*, *bias=0*)

For staircase (linear/log) voltage sweep (`WV`), configure bias value and current compliance, then the number of steps, stop value, start value, source range, number of repeats, and sweep mode.

Note

- The following limits apply to sweep mode, number of repeats, and number of steps.
  - Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.
    - For output data output method 1 or 2 selected by the OFM command, keep m x number of refreshes x N <= 2048.

    - If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

- Both polarities (+ and -) receive current compliance, no matter which current compliance polarity was specified.

- The instrument selects the smallest current compliance range that contains the configured value.
