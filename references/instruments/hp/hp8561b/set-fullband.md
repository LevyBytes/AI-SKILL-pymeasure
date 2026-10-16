# pymeasure.instruments.hp.HP8561B.set_fullband

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_fullband(*band*)

Choose a common external-mixer frequency band from the table. This also sets `harmonic_number_lock`, locking the harmonic for the selected band. External-mixing functions are unavailable on an HP 8560A Option 002. The value is a frequency-band letter supplied as a string.

External mixer frequency bands:

| Frequency Band | Frequency Range (GHz) | Mixing Harmonic | Conversion Loss |
| --- | --- | --- | --- |
| K | 18.0 — 26.5 | 6 | 30 dB |
| A | 26.5 — 40.0 | 8 | 30 dB |
| Q | 33.0—50.0 | 10 | 30 dB |
| U | 40.0—60.0 | 10 | 30 dB |
| V | 50.0—75.0 | 14 | 30 dB |
| E | 60.0—90.0 | 16 | 30 dB |
| W | 75.0—110.0 | 18 | 30 dB |
| F | 90.0—140.0 | 24 | 30 dB |
| D | 110.0—170.0 | 30 | 30 dB |
| G | 140.0—220.0 | 36 | 30 dB |
| Y | 170.0—260.0 | 44 | 30 dB |
| J | 220.0—325.0 | 54 | 30 dB |
