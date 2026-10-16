# pymeasure.instruments.advantest.advantestR624X.SMUChannel.current_random_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

current_random_sweep(*sweep_mode*, *repeat*, *start_address*, *stop_address*, *current_compliance*, *bias=0*)

Configure constant current random sweep (`MDWI`). Set sweep mode, repeat count, start address, and stop address. Also set voltage compliance and bias value.

Note

- The restrictions below apply to sweep mode, number of repeats, start address, and stop address:
  - Start address < Stop address

  - Let N = (stop number 1 - start number + 1), m = 1 (one-way sweep), m = 2 (round-trip sweep).
    - When the OFM command selects output data output method 1 or 2, observe the buffer-size constraint. The required condition is m x number of repeats x N <= 2048.

    - If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

- For voltage compliance polarity, both polarities of + and - are set regardless of the specified voltage compliance polarity.

- The instrument selects the smallest voltage compliance range that contains the configured value.
