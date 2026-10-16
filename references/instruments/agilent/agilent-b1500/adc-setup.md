# pymeasure.instruments.agilent.agilentB1500.AgilentB1500.adc_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

adc_setup(*adc_type*, *mode*, *N=''*)

Configure ADC operation mode and parameters for each ADC type. (`AIT`)

Defaults:
- HSADC: Auto N=1, Manual N=1, PLC N=1, Time N=0.000002(s)

- HRADC: Auto N=6, Manual N=3, PLC N=1

Parameters:

- **adc_type** (*ADCType*) – ADC type

- **mode** (*ADCMode*) – ADC mode

- **N** (*str*) – Extra parameter; see documentation, defaults to `''`
