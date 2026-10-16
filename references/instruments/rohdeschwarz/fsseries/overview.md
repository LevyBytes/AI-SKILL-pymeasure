# pymeasure.instruments.rohdeschwarz.fsseries.FSSeries

*class *pymeasure.instruments.rohdeschwarz.fsseries.FSSeries(*adapter*, *name='Rohde&Schwarz FS series instrument'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models a Rohde&Schwarz FS Series spectrum analyzer, including FSL and FSW.

Settable physical quantities accept either a value-with-unit string such as “1.2 GHz” or a float expressed in base units (Hz, dBm, etc.).
