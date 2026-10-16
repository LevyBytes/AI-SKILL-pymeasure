# pymeasure.instruments.agilent.agilentB1500.SMUVoltageRanging

*class *pymeasure.instruments.agilent.agilentB1500.SMUVoltageRanging(*smu_type*)

Bases: `object`

Converts range names and indices for voltage measurement/sourcing.

The SMU type is used to check whether ranges are valid.

For voltage measurement, a range string without 'limited auto ranging'/'range fixed' uses 'limited auto ranging' by default.

Complete form: `'2 V range fixed'` or `'2 V limited auto ranging'`

`'2 V'` uses `'2 V limited auto ranging'` as the default
