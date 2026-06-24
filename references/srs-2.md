# Sr860, Sr510

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Scope: SR860 Lock-in Amplifier; SR510 Lock-in Amplifier; Stanford Research Systems.

## SR860 Lock-in Amplifier

### SR860 Lock-in Amplifier

 Class constructor: *pymeasure.instruments.srs.SR860* with *adapter*, *name='Stanford Research Systems SR860 Lock-in amplifier'*, and ***kwargs*.

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

 *property *adc1*: Any*

Returns Aux input 1 in Volts, with 1/3 mV resolution.

 *property *adc2*: Any*

Returns Aux input 2 in Volts, with 1/3 mV resolution.

 *property *adc3*: Any*

Returns Aux input 3 in Volts, with 1/3 mV resolution.

 *property *adc4*: Any*

Returns Aux input 4 in Volts, with 1/3 mV resolution.

 *property *aux_in_1*: Any*

Returns Aux input 1 in Volts, with 1/3 mV resolution.

 *property *aux_in_2*: Any*

Returns Aux input 2 in Volts, with 1/3 mV resolution.

 *property *aux_in_3*: Any*

Returns Aux input 3 in Volts, with 1/3 mV resolution.

 *property *aux_in_4*: Any*

Returns Aux input 4 in Volts, with 1/3 mV resolution.

 *property *aux_out_1*: Any*

Settable floating point property controlling Aux output 1 in Volts; values are between -10.5 V and +10.5 V.

 *property *aux_out_2*: Any*

Settable floating point property controlling Aux output 2 in Volts; values are between -10.5 V and +10.5 V.

 *property *aux_out_3*: Any*

Settable floating point property controlling Aux output 3 in Volts; values are between -10.5 V and +10.5 V.

 *property *aux_out_4*: Any*

Settable floating point property controlling Aux output 4 in Volts; values are between -10.5 V and +10.5 V.

 *property *dac1*: Any*

Settable floating point property controlling Aux output 1 in Volts; values are between -10.5 V and +10.5 V.

 *property *dac2*: Any*

Settable floating point property controlling Aux output 2 in Volts; values are between -10.5 V and +10.5 V.

 *property *dac3*: Any*

Settable floating point property controlling Aux output 3 in Volts; values are between -10.5 V and +10.5 V.

 *property *dac4*: Any*

Settable floating point property controlling Aux output 4 in Volts; values are between -10.5 V and +10.5 V.

 *property *dcmode*: Any*

Settable string property for the sine out dc mode. Allowed values are:[‘COM’, ‘DIF’, ‘common’, ‘difference’]

 *property *detectedfrequency*: Any*

Gives the actual detected frequency in HZ.

 *property *extfreqency*: Any*

Gives the external frequency in Hz.

 *property *filer_synchronous

Use the filer_synchronous (sic) property to access the filter_synchronous attribute.

Deprecated since version 0.16.0: use filter_synchronous instead.

 *property *filter_advanced*: Any*

Settable string property for the advanced filter. Allowed values are:[‘Off’, ‘On’]

 *property *filter_slope*: Any*

Integer property selecting the filter slope: 6 dB/oct(i=0), 12 DB/oct(i=1), 18 dB/oct(i=2), or 24 dB/oct(i=3).

 *property *filter_synchronous*: Any*

Settable string property for the synchronous filter. Allowed values are:[‘Off’, ‘On’]

 *property *frequency*: Any*

Settable floating point property for the lock-in frequency in Hz.

 *property *frequencypreset1*: Any*

Settable floating point property for the F1 preset button frequency.

 *property *frequencypreset2*: Any*

Settable floating point property for the F2 preset button frequency.

 *property *frequencypreset3*: Any*

Settable floating point property for the F3 preset button frequency.

 *property *frequencypreset4*: Any*

Settable floating point property for the F4 preset button frequency.

 *property *front_panel*: Any*

Sets front panel blanking on(i=0) or off(i=1).

 *property *get_noise_bandwidth*: Any*

Reports the equivalent noise bandwidth, in hertz.

 *property *get_signal_strength_indicator*: Any*

Returns the signal strength indicator.

 *property *gettimebase*: Any*

Reports the active 10 MHz timebase source.

 *property *harmonic*: Any*

Settable integer property controlling the measured harmonic. Allowed values are 1 to 99.

 *property *harmonicdual*: Any*

Settable integer property controlling the measured harmonic in dual reference mode. Allowed values are 1 to 99.

 *property *horizontal_time_div*: Any*

Selects the horizontal time/div using this table: [‘0=0.5s’ | ‘1=1s’ | ‘2=2s’ | ‘3=5s’ | ‘4=10s’ | ‘5=30s’ | ‘6=1min’ | ‘7=2min’ | ‘8=5min’ | ‘9=10min’ | ‘10=30min’ | ‘11=1hour’ | ‘12=2hour’ | ‘13=6hour’ | ‘14=12hour’ | ‘15=1day’ | ‘16=2days’]

 *property *input_config*: Any*

Settable string property for the voltage input mode. Allowed values are:[‘A’, ‘A-B’]

 *property *input_coupling*: Any*

Settable string property for the input coupling. Allowed values are:[‘AC’, ‘DC’]

 *property *input_current_gain*: Any*

Settable string property for the current input gain. Allowed values are:[‘1MEG’, ‘100MEG’]

 *property *input_grounding*: Any*

Settable string property for input shield grounding. Allowed values are:[‘Float’, ‘Ground’]

 *property *input_range*: Any*

Settable string property for the input range. Allowed values are:[‘1V’, ‘300M’, ‘100M’, ‘30M’, ‘10M’]

 *property *input_shields*: Any*

Settable string property for input shield grounding. Allowed values are:[‘Float’, ‘Ground’]

 *property *input_signal*: Any*

Settable string property for the signal input. Allowed values are:[‘VOLT’, ‘CURR’, ‘voltage’, ‘current’]

 *property *input_voltage_mode*: Any*

Settable string property for the voltage input mode. Allowed values are:[‘A’, ‘A-B’]

 *property *internalfrequency*: Any*

Settable floating property for the internal lock-in frequency in Hz.

 *property *magnitude*: Any*

Reads the magnitude in Volts.

 *property *parameter_DAT1*: Any*

Settable integer property assigning a parameter to data channel 1(green). Allowed values are: [‘i=’ | ‘0=Xoutput’ | ‘1=Youtput’ | ‘2=Routput’ | ‘Thetaoutput’ | ‘4=Aux IN1’ | ‘5=Aux IN2’ | ‘6=Aux IN3’ | ‘7=Aux IN4’ | ‘8=Xnoise’ | ‘9=Ynoise’ | ‘10=AUXOut1’ | ‘11=AuxOut2’ | ‘12=Phase’ | ‘13=Sine Out amplitude’ | ‘14=DCLevel’ | ‘15I=nt.referenceFreq’ | ‘16=Ext.referenceFreq’]

 *property *parameter_DAT2*: Any*

Settable integer property assigning a parameter to data channel 2(blue). Allowed values are: [‘i=’ | ‘0=Xoutput’ | ‘1=Youtput’ | ‘2=Routput’ | ‘Thetaoutput’ | ‘4=Aux IN1’ | ‘5=Aux IN2’ | ‘6=Aux IN3’ | ‘7=Aux IN4’ | ‘8=Xnoise’ | ‘9=Ynoise’ | ‘10=AUXOut1’ | ‘11=AuxOut2’ | ‘12=Phase’ | ‘13=Sine Out amplitude’ | ‘14=DCLevel’ | ‘15I=nt.referenceFreq’ | ‘16=Ext.referenceFreq’]

 *property *parameter_DAT3*: Any*

Settable integer property assigning a parameter to data channel 3(yellow). Allowed values are: [‘i=’ | ‘0=Xoutput’ | ‘1=Youtput’ | ‘2=Routput’ | ‘Thetaoutput’ | ‘4=Aux IN1’ | ‘5=Aux IN2’ | ‘6=Aux IN3’ | ‘7=Aux IN4’ | ‘8=Xnoise’ | ‘9=Ynoise’ | ‘10=AUXOut1’ | ‘11=AuxOut2’ | ‘12=Phase’ | ‘13=Sine Out amplitude’ | ‘14=DCLevel’ | ‘15I=nt.referenceFreq’ | ‘16=Ext.referenceFreq’]

 *property *parameter_DAT4*: Any*

Settable integer property assigning a parameter to data channel 3(orange). Allowed values are: [‘i=’ | ‘0=Xoutput’ | ‘1=Youtput’ | ‘2=Routput’ | ‘Thetaoutput’ | ‘4=Aux IN1’ | ‘5=Aux IN2’ | ‘6=Aux IN3’ | ‘7=Aux IN4’ | ‘8=Xnoise’ | ‘9=Ynoise’ | ‘10=AUXOut1’ | ‘11=AuxOut2’ | ‘12=Phase’ | ‘13=Sine Out amplitude’ | ‘14=DCLevel’ | ‘15I=nt.referenceFreq’ | ‘16=Ext.referenceFreq’]

 *property *phase*: Any*

Settable floating point property for the lock-in phase in degrees.

 *property *reference_externalinput*: Any*

Settable string property for the external reference input. Allowed values are:[‘50OHMS’, ‘1MEG’]

 *property *reference_source*: Any*

Settable string property for the reference source. Allowed values are:[‘INT’, ‘EXT’, ‘DUAL’, ‘CHOP’]

 *property *reference_source_trigger*: Any*

Settable string property for the external reference trigger mode. Allowed values are:[‘SIN’, ‘POS’, ‘NEG’, ‘POSTTL’, ‘NEGTTL’]

 *property *reference_triggermode*: Any*

Settable string property for the external reference trigger mode. Allowed values are:[‘SIN’, ‘POS’, ‘NEG’, ‘POSTTL’, ‘NEGTTL’]

 *property *screen_layout*: Any*

Integer property selecting the screen layout. Set i=0 for trend, i=1 for full strip chart history, i=2 for half strip chart history, i=3 for full FFT, i=4 for half FFT, or i=5 for big numerical.

 screenshot()

Triggers a device screenshot. The DCAP command writes a screenshot to a USB memory stick and performs the same action as pressing the [Screen Shot] key. The front panel USB port must contain a USB memory stick.

 *property *sensitivity*: Any*

Floating point property controlling sensitivity in Volts; discrete values run from 2 nV to 1 V. Non-exact values are truncated to the next highest level.

 *property *sensitvity

Use the sensitvity (sic) property to access the sensitivity attribute.

Deprecated since version 0.16.0: use sensitivity instead.

 *property *sine_amplitudepreset1*: Any*

Settable floating point property for the preset sine out amplitude on the A1 preset button.

 *property *sine_amplitudepreset2*: Any*

Settable floating point property for the preset sine out amplitude on the A2 preset button.

 *property *sine_amplitudepreset3*: Any*

Settable floating point property for the preset sine out amplitude on the A3 preset button.

 *property *sine_amplitudepreset4*: Any*

Settable floating point property for the preset sine out amplitude on the A4 preset button.

 *property *sine_dclevelpreset1*: Any*

Settable floating point property for the preset sine out dc level on the L1 button.

 *property *sine_dclevelpreset2*: Any*

Settable floating point property for the preset sine out dc level on the L2 button.

 *property *sine_dclevelpreset3*: Any*

Settable floating point property for the preset sine out dc level on the L3 button.

 *property *sine_dclevelpreset4*: Any*

Settable floating point property for the preset sine out dc level on the L4 button.

 *property *sine_voltage*: Any*

Settable floating point property for the reference sine-wave voltage in Volts.

 snap(*val1='X'*, *val2='Y'*, *val3=None*)

Retrieves 2 or 3 parameters together; parameters may be selected by index or enumeration as follows:

| index | enumeration | parameter |
| --- | --- | --- |
| 0 | X | X output |
| 1 | Y | Y output |
| 2 | R | R output |
| 3 | THeta | θ output |
| 4 | IN1 | Aux In1 |
| 5 | IN2 | Aux In2 |
| 6 | IN3 | Aux In3 |
| 7 | IN4 | Aux In4 |
| 8 | XNOise | Xnoise |
| 9 | YNOise | Ynoise |
| 10 | OUT1 | Aux Out1 |
| 11 | OUT2 | Aux Out2 |
| 12 | PHAse | Reference Phase |
| 13 | SAMp | Sine Out Amplitude |
| 14 | LEVel | DC Level |
| 15 | FInt | Int. Ref. Frequency |
| 16 | FExt | Ext. Ref. Frequency |

Parameters:

-

**val1** – parameter enumeration/index (default: `'X'`)

-

**val2** – parameter enumeration/index (default: `'Y'`)

-

**val3** – parameter enumeration/index (optional) (default: `None`)

Defaults:

val1 = “X” val2 = “Y” val3 = None

 snap_all()

snap retrieves X,Y,R,THETA parameters at once

 *property *strip_chart_dat1*: Any*

Integer property enabling or disabling the strip chart graph for data channel 1, off(i=0) or on(i=1).

 *property *strip_chart_dat2*: Any*

Integer property enabling or disabling the strip chart graph for data channel 2, off(i=0) or on(i=1).

 *property *strip_chart_dat3*: Any*

Integer property enabling or disabling the strip chart graph for data channel 3, off(i=0) or on(i=1).

 *property *strip_chart_dat4*: Any*

Integer property enabling or disabling the strip chart graph for data channel 4, off(i=0) or on(i=1).

 *property *theta*: Any*

Returns the theta value in degrees.

 *property *time_constant*: Any*

Floating point property controlling the time constant in seconds; discrete values run from 10 microseconds to 30,000 seconds. Non-exact values are truncated to the next highest level.

 *property *timebase*: Any*

Sets how the external 10 MHZ timebase is selected: auto(i=0) or internal(i=1).

 *property *x*: Any*

Returns the X value in Volts

 *property *y*: Any*

Returns the Y value in Volts

## SR510 Lock-in Amplifier

### SR510 Lock-in Amplifier

 Class constructor: *pymeasure.instruments.srs.SR510* with *adapter*, *name='Stanford Research Systems SR510 Lock-in amplifier'*, and ***kwargs*.

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

 *property *frequency*: Any*

Float property for the SR510 input reference frequency

 *property *output*: Any*

Float property for the SR510 output voltage in Volts.

 *property *phase*: Any*

Float property for the SR510 phase offset between reference and input, in degrees. Queries return values between -180 and 180 degrees. The settable range is -999 to 999 degrees, with set values internally mapped in the lockin to -180 and 180 degrees.

 *property *sensitivity*: Any*

Settable float property for the SR510 sensitivity value.

 *property *status*: Any*

String property for the bits set within the SR510 status byte

 *property *time_constant*: Any*

Settable float property for the SR510 PRE filter time constant.

## Stanford Research Systems

### Stanford Research Systems

This section documents the implemented Stanford Research Systems (SRS) instruments. For an instrument not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [LDC500 Series Laser-diode Controllers](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/ldc500series.html)
  - [`LDC500Series`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/ldc500series.html#pymeasure.instruments.srs.ldc500series.LDC500Series)
  - [`LDC500SeriesLD`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/ldc500series.html#pymeasure.instruments.srs.ldc500series.LDC500SeriesLD)
  - [`LDC500SeriesPD`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/ldc500series.html#pymeasure.instruments.srs.ldc500series.LDC500SeriesPD)
  - [`LDC500SeriesTEC`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/ldc500series.html#pymeasure.instruments.srs.ldc500series.LDC500SeriesTEC)
  - [`ThermometerType`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/ldc500series.html#pymeasure.instruments.srs.ldc500series.ThermometerType)

- [SR510 Lock-in Amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/sr510.html)
  - [`SR510`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/sr510.html#pymeasure.instruments.srs.SR510)

- [SR570 Lock-in Amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/sr570.html)
  - [`SR570`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/sr570.html#pymeasure.instruments.srs.SR570)

- [SR830 Lock-in Amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/sr830.html)
  - [`SR830`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/sr830.html#pymeasure.instruments.srs.SR830)

- [SR860 Lock-in Amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/sr860.html)
  - [`SR860`](https://pymeasure.readthedocs.io/en/latest/api/instruments/srs/sr860.html#pymeasure.instruments.srs.SR860)
