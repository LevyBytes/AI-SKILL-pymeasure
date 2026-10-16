# Version 0.16.0 (2026-05-20)

Primary changes in this release:

- Add support for Python 3.13

- The policy now permits type hints, which have already been introduced in the instruments core.

- 25 new instruments

- `Instrument.control` now applies `get_process` only to a single returned value, not to returned lists. Use the `get_process_list` parameter when a list of values needs processing.

- The Keithley 2400 implementation was improved and includes some behavioral changes. The previous implementation remains available as `Keithley2400Legacy`.
