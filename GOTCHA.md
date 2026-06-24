# PyMeasure Gotchas

Recurring failure modes when relying on the PyMeasure reference, and what to do instead. Read alongside `SKILL.md`.

- Treat every identifier (instrument class name, property/method name, Adapter type, VISA resource string, parameter name) as an exact reference fact - do not invent or paraphrase the API.
- PyMeasure builds on PyVISA: it needs a VISA backend (pyvisa-py or a vendor library like NI-VISA) plus the instrument's connection. Available instruments, properties, and behavior depend on the installed pymeasure version and backend, not on the docs alone.
- These docs track the latest pymeasure; verify version-sensitive instrument drivers, properties, ranges, and defaults against the installed version.
- Coverage is the documented driver set; an instrument not listed may still be controllable via a generic Instrument plus manual SCPI/commands. Use `references/INDEX.md` or `rg -n "PATTERN" references/*.md` to locate a class or property.
