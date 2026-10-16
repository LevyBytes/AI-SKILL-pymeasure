# pymeasure.instruments.agilent.agilentB1500.AgilentB1500.adc_averaging

[Owning PyMeasure class, adapter and connection contract](overview.md)

adc_averaging(*number*, *mode='Auto'*)

Configure the HSADC averaging sample count. (`AV`)

Defaults: N=1, Auto

Parameters:

- **number** (*int*) – Number of averages

- **mode** (*AutoManual*) – Operating mode (`'Auto','Manual'`), defaults to ‘Auto’

## Related property contracts

- Open when checking pymeasure.instruments.agilent.agilentB1500.AgilentB1500.adc_auto_zero: [adc_auto_zero](adc-auto-zero.md).
- Open when checking pymeasure.instruments.agilent.agilentB1500.AgilentB1500.time_stamp: [time_stamp](time-stamp.md).
