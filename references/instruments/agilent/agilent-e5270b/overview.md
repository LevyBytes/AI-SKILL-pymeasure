# pymeasure.instruments.agilent.AgilentE5270B

*class *pymeasure.instruments.agilent.AgilentE5270B(*adapter*, *name='Agilent E5270B'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent E5270B 8 slot SMU mainframe.

Supported plug-in modules are:

| Name | Type | Slots | Range | Resolution |
| --- | --- | --- | --- | --- |
| E5280B | HPSMU | 2 | ±200 V, ±1 A | 2 µV, 10 fA |
| E5281B | MPSMU | 1 | ±100 V, ±100 mA | 0.5 µV, 10 fA |
| E5287A | HRSMU | 1 | ±100 V, ±100 mA | 0.5 µV, 1 fA |
| E5288A | ASU | — | ±100 V, ±100 mA | 0.5 µV, 0.1 fA |
