# pymeasure.instruments.advantest.advantestR624X.SMUChannel.voltage_random_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

voltage_random_sweep(*sweep_mode*, *repeat*, *start_address*, *stop_address*, *current_compliance*, *bias=0*)

Configure constant voltage random sweep (`MDWV`). Set sweep mode, repeat count, start address, and stop address. Also set current compliance and bias value.

Note

- The restrictions below apply to sweep mode, number of repeats, start address, and stop address:
  - Start address < Stop address

  - Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.
    - For output data output method 1 or 2 selected by the OFM command, keep m x number of refreshes x N <= 2048.

    - If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

- Both polarities (+ and -) receive current compliance, no matter which current compliance polarity was specified.

- The instrument selects the smallest current compliance range that contains the configured value.
