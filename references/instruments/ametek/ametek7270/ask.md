# pymeasure.instruments.ametek.Ametek7270.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command*, *query_delay=None*)

Send a command, read the response, and strip whitespace.

Most properties rely on the [`values()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.values) method, which performs stripping. A few methods instead cast the direct ask result into other types, so stripping must happen here too because every response ends with a newline character.

## Related property contracts

- Open when checking pymeasure.instruments.ametek.Ametek7270.auto_gain: [auto_gain](auto-gain.md).
