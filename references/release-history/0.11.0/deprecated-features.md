# Version 0.11.0 (2022-11-19) — Deprecated features

For the stable 1.0 path and a more uniform API, several features are now formally deprecated. Using them should emit warnings.

- Deprecates Adapter methods `ask`, `values`, `binary_values`; call the matching `Instrument` methods instead.

- Adapter parameter `preprocess_reply`, override `Instrument.read` instead.

- Replaces `Adapter.query_delay` with `Instrument.wait_for()`.

- For Keithley 2260B, deprecates the `enabled` property in favor of `output_enabled`.
