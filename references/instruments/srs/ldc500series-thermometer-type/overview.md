# pymeasure.instruments.srs.ldc500series.ThermometerType

*class *pymeasure.instruments.srs.ldc500series.ThermometerType(**values*)

Bases: `IntEnum`

ThermometerType choices supported by SRS LDC500Series. NTC means negative temperature coefficient; RTD means Resistance temperature detector.

Members:
- **NTC10UA** : NTC thermistor excitation at 10 µA.

- **NTC100UA** : NTC thermistor excitation at 100 µA.

- **NTC1MA** : NTC thermistor excitation at 1 mA.

- **NTCAUTO** : Finds the best NTC excitation automatically.

- **RTD** : Usually Pt-100 or another PTC sensor

- **LM335** : Temperature-to-voltage transducers compatible with LM335.

- **AD590** : Temperature-to-current transducers compatible with AD590.
