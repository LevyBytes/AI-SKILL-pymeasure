# pymeasure.instruments.keithley.KeithleyDAQ6510.resistance_nplc

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *resistance_nplc*: Any*

Set or read the 2-wire resistance NPLC setting; it controls integration time and measurement speed. The accepted span starts at 5E-4, with an upper limit of 15 at 60 Hz or 12 at 50 Hz or 400 Hz. Smaller settings shorten the integration period and produce the fastest reading rate, with more reading noise and fewer usable digits. Larger settings lengthen the integration period and produce the slowest reading rate, with more usable digits.
