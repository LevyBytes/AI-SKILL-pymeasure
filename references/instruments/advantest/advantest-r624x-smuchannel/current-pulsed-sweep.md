# pymeasure.instruments.advantest.advantestR624X.SMUChannel.current_pulsed_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

current_pulsed_sweep(*sweep_mode*, *repeat*, *current_range*, *base*, *start_value*, *stop_value*, *steps*, *voltage_compliance*, *bias=0*)

For pulse wave (linear/log) current sweep (`PWI`), configure bias value, voltage compliance, number of steps, stop value, start value, base value, generation range, repeat count, and sweep mode.

Note

- These restrictions apply to sweep mode, number of refreshes, and number of steps:
  - Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.
    - For output data output method 1 or 2 selected by the OFM command, keep m x number of repeats x N <= 2048.

    - If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

- Both polarities (+ and -) receive voltage compliance, regardless of the voltage compliance polarity specified.

- The instrument selects the smallest voltage compliance range that contains the configured value.

Warning

`current_range` must be a fixed range, for example `CurrentRange.FIXED_BEST`. `CurrentRange.AUTO` and `AUTO_*` ranges are unavailable for pulse sweep and cause error 00211.
