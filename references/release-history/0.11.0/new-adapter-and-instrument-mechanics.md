# Version 0.11.0 (2022-11-19) - New adapter and instrument mechanics

- User-facing behavior should stay the same; this section mostly matters to instrument implementors.

- Documents the details under 'Advanced communication protocols' in 'Adding instruments'.

- Makes Adapter log both written and read messages.

- Leaves real communication work to specific adapters such as VISAAdapter.

- `Instrument.control` getter calls `Instrument.values`.

- Routes `Instrument.values` through `Instrument.ask`, then through `Instrument.write`, `wait_for`, and `read`.

- Implements instrument-specific protocol quirks by overriding `Instrument.write` and `read`.

- Uses `Instrument.wait_until_read` for the pause between writing and reading.

- Keeps binary value reads and writes in the `Adapter` class itself.

- Bases `PrologixAdapter` on `VISAAdapter` now.

- Brings `SerialAdapter` closer to `VISAAdapter`: `read`/`write` work with strings, while `read/write_bytes` work with bytes. - Adds termination character support.
