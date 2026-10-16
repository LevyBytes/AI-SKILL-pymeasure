# Version 0.15.0 (2025-01-15) — Automation

- File reads and writes now explicitly use utf8 encoding, enabling special characters in stored data. Earlier releases did not set the encoding explicitly, which may affect loading older data files; when needed, the encoding can be changed, for example by monkey-patching the `pymeasure.experiment.Results.ENCODING` property. (@CasperSchippers, #1123)

- Procedure gained a `has_next` method (@Did-Mas, #1185).

- Logging changed from the root logger to a module-specific logger (@mmerlo, #1165).
