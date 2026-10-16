# pymeasure.instruments.agilent.agilentB1500.SMUCurrentRanging

*class *pymeasure.instruments.agilent.agilentB1500.SMUCurrentRanging(*smu_type*)

Bases: `object`

Converts range names and indices for current measurement/sourcing.

The SMU type is used to check whether ranges are valid.

For current measurement, a range string without 'limited auto ranging'/'range fixed' uses 'limited auto ranging' by default.

Complete form: `'1 nA range fixed'` or `'1 nA limited auto ranging'`

`'1 nA'` uses `'1 nA limited auto ranging'` as the default
