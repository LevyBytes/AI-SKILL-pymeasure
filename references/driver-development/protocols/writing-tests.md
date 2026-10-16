# Writing tests

Good tests make driver code easier to trust. The pymeasure project already includes tests for its own implementation, stored under the `tests` directory. CI runs them automatically, and you can execute the same suite locally with `pytest`.

For a new instrument, focus first on tests for the *instrument driver* you are adding. Instrument tests fall into two categories. One category runs without hardware and checks that the driver sends and receives the expected protocol messages, such as those described in a device manual; these are "protocol tests". The other category runs against a connected device.

Add device test modules under `tests/instruments/...`, matching the package layout used by the corresponding instrument implementations. Existing instrument tests in that tree are useful patterns to follow.
