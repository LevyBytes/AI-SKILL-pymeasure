# pymeasure.instruments.ni.virtualbench.VirtualBench.DigitalInputOutput.export_signal

[Owning DigitalInputOutput contract](overview.md)

export_signal(*line*, *digitalSignalSource*)

Routes a signal onto the requested line.

Parameters:

- **line** (*str*) – Line string

- **digitalSignalSource** (*int*) — use `0` for FGEN start or `1` for MSO trigger
