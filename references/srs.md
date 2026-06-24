# Ldc500Series, Sr830, Sr570

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LDC500 Series Laser-diode Controllers, SR830 Lock-in Amplifier, and SR570 Lock-in Amplifier.

## LDC500 Series Laser-diode Controllers

### LDC500 Series Laser-diode Controllers

 *class *pymeasure.instruments.srs.ldc500series.LDC500Series(*adapter*, *name='LDC500Series'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models an SRS LDC500Series laser diode controller with a higher-level API for instrument operations.

 ld

Channel:

`LDC500SeriesLD`

 pd

Channel:

`LDC500SeriesPD`

 tec

Channel:

`LDC500SeriesTEC`

 check_errors()

Collect every reported instrument error.

Returns:

Returns a list containing [`last_execution_error`, `last_command_error`].

 check_set_errors()

After a property write, query errors and raise if any were reported.

 *property *last_command_error*: Any*

Return the most recent command error code; reading it also clears the execution error code to 0.

 *property *last_execution_error*: Any*

Return the most recent execution error code; reading it also clears the execution error code to 0.

 *property *next_error

The next-error query is unsupported and raises `NotImplementedError`.

 *property *options

The options query is unsupported and raises `NotImplementedError`.

 *class *pymeasure.instruments.srs.ldc500series.LDC500SeriesLD(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Channel object on LDC500Series used to operate the laser-diode (LD).

 *property *current*: Any*

Read laser diode current as a float in mA.

 *property *current_limit*: Any*

Set or read the laser diode current limit as a float in mA.

The output current is capped so it cannot rise above `current_limit` in any situation. Lowering `current_limit` beneath `current_setpoint` pulls `current_setpoint` down to match `current_limit`.

 *property *current_range*: Any*

Select the laser diode current range with str Ã¢â‚¬Å“HIGHÃ¢â‚¬Â or Ã¢â‚¬Å“LOWÃ¢â‚¬Â.

Model selection determines which currents apply to each current range:

|  | LDC500 | LDC501 | LDC502 |
| --- | --- | --- | --- |
| HIGH | 100mA | 500mA | 2000mA |
| LOW | 50mA | 250mA | 1000mA |

 *property *current_setpoint*: Any*

Set or read the laser diode current setpoint in mA while `mode == "CC"`; value type is float.

 *property *enabled*: Any*

Enable or disable the laser diode current source with a bool.

 *property *interlock_closed*: Any*

Read interlock state: True means closed and False means open. The laser operates only when the interlock is closed.

 *property *mode*: Any*

Choose the laser diode control mode using str Ã¢â‚¬Å“CCÃ¢â‚¬Â or Ã¢â‚¬Å“CPÃ¢â‚¬Â.

When `mode` changes while the laser remains on, the controller uses a *bumpless transfer* for the live mode switch.

Changing `mode` from Ã¢â‚¬Å“CCÃ¢â‚¬Â to Ã¢â‚¬Å“CPÃ¢â‚¬Â samples the current photodiode current, equivalently optical power, then uses that measurement as the CP setpoint. If the measured photodiode current or power is over the setpoint limit, an error is raised.

Changing `mode` from Ã¢â‚¬Å“CPÃ¢â‚¬Â to Ã¢â‚¬Å“CCÃ¢â‚¬Â samples the current laser current and sets the CC setpoint to that measurement. Hardware prevents the measured laser current from exceeding the setpoint limit.

 *property *modulation_bandwidth*: Any*

Set or read laser diode modulation bandwidth as str Ã¢â‚¬Å“HIGHÃ¢â‚¬Â or Ã¢â‚¬Å“LOWÃ¢â‚¬Â.

For the DC coupled analog modulation input, the Ã¢â‚¬â€œ3 dB roll-off frequency depends on `mode` and `modulation_bandwidth`:

|  | CC | CP |
| --- | --- | --- |
| LOW | 10kHz | 100Hz |
| HIGH | 1.2mhz | 5kHz |

 *property *modulation_enabled*: Any*

Enable or disable analog modulation for the laser diode with a bool.

 *property *voltage*: Any*

Read the laser diode voltage as a float in V.

 *property *voltage_limit*: Any*

Set or read the laser diode voltage limit as a float strictly in range 0.1 to 10 V. Crossing the voltage limit disables the current source.

 *class *pymeasure.instruments.srs.ldc500series.LDC500SeriesPD(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Channel object on LDC500Series used to operate the photodiode (PD).

 *property *bias*: Any*

Set or read photodiode bias as a float strictly in range 0 to 5.

 calibrate(*power*)

Use a real time power measurement to set photodiode `responsivity`.

Parmeters:

power (float): real time optical power reading, in mW.

 *property *current*: Any*

Read photodiode current as a float in uA.

 *property *current_limit*: Any*

Set/read the photodiode current limit in uA while `mode == "CP"` and `photodiode_units == "uA"`; value type is float.

 *property *current_setpoint*: Any*

Set/read the photodiode current setpoint in uA while `mode == "CP"` and `photodiode_units == "uA"`; value type is float.

 *property *power*: Any*

Read photodiode power as a float in mW.

 *property *power_limit*: Any*

Set/read the photodiode power limit in mW when `mode == "CP"` and `photodiode_units == "mW"`; value type is float.

When `power_limit` is lowered beneath `power_setpoint`, `power_setpoint` is pulled down with `power_limit`.

 *property *power_setpoint*: Any*

Set/read optical power setpoint for the photodiode in mW when `mode == "CP"` and `photodiode_units == "mW"`; value type is float.

 *property *responsivity*: Any*

Set or read photodiode responsivity as a float in uA/mW.

Changing `responsivity`, whether directly or through `calibrate`, also updates:

-

`current_setpoint` and `current_limit` when `units == "mW"`

-

`power_setpoint` and `power_limit` when `units == "uA"`

Those updates preserve these relationships:

-

`current_setpoint = power_setpoint x responsivity`

-

`current_limit = power_limit x responsivity`

 *property *units*: Any*

Set or read CP photodiode units with str Ã¢â‚¬Å“mWÃ¢â‚¬Â or Ã¢â‚¬Å“uAÃ¢â‚¬Â.

 *class *pymeasure.instruments.srs.ldc500series.LDC500SeriesTEC(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Channel object on LDC500Series used to operate the thermo-electric-controller (TEC).

 check_temperature_stability(*tolerance=0.1*, *period=10*, *points=64*)

Check whether temperature stays stable at the temperature setpoint for a requested interval.

Parameters:

-

**tolerance** Ã¢â‚¬â€œ Largest permitted offset from temperature setpoint, in degrees Centigrade. (default: `0.1`)

-

**period** Ã¢â‚¬â€œ Duration used for the stability check, in seconds. (default: `10`)

Returns:

True if stable, False otherwise.

 *property *current*: Any*

Read TEC current in A.

 *property *current_limit*: Any*

Set/read TEC current limit in A, as a float strictly in range -4.5 to 4.5.

Reducing `current_limit` below `current_setpoint` makes `current_setpoint` follow `current_limit` downward.

 *property *current_setpoint*: Any*

Set/read TEC current setpoint in A while `mode == "CC"`; value type is float.

 *property *enabled*: Any*

Enable or disable the TEC current source with a bool.

 *property *mode*: Any*

Set/read TEC control mode using str Ã¢â‚¬Å“CCÃ¢â‚¬Â or Ã¢â‚¬Å“CTÃ¢â‚¬Â.

If `mode` changes while the TEC is on, the controller uses a *bumpless transfer* for a live control-mode switch.

Changing `mode` from Ã¢â‚¬Å“CTÃ¢â‚¬Â to Ã¢â‚¬Å“CCÃ¢â‚¬Â samples the present TEC current and applies that measurement as the CC setpoint.

Changing `mode` from Ã¢â‚¬Å“CCÃ¢â‚¬Â to Ã¢â‚¬Å“CTÃ¢â‚¬Â samples the present temperature sensor value and applies that measurement as the CT setpoint.

 *property *resistance_high_limit*: Any*

Set/read the TEC high resistance limit in kÃŽÂ© as a float.

 *property *resistance_limits

Set/read TEC resistance limits in kÃŽÂ© as a two-tuple of floats.

 *property *resistance_low_limit*: Any*

Set/read the TEC low resistance limit in kÃŽÂ© as a float.

 *property *resistance_setpoint*: Any*

Set/read the TEC resistance setpoint in kÃŽÂ© as a float.

 *property *temperature*: Any*

Read TEC temperature as a float in Ã‚Â°C.

 *property *temperature_high_limit*: Any*

Set/read the TEC high temperature limit in Ã‚Â°C as a float.

 *property *temperature_limits

Set/read TEC temperature limits in Ã‚Â°C as a two-tuple of floats.

 *property *temperature_low_limit*: Any*

Set/read the TEC low temperature limit in Ã‚Â°C as a float.

 *property *temperature_setpoint*: Any*

Set/read the TEC temperature setpoint in Ã‚Â°C as a float.

 *property *thermometer_raw*: Any*

Read the raw thermometer value as a float; units are kÃŽÂ©, V, or ÃŽÂ¼A according to sensor type.

 *property *thermometer_type*: Any*

Set/read the temperature sensor type using the ThermometerType enum.

 *property *voltage*: Any*

Read TEC voltage in V as a float.

 *property *voltage_limit*: Any*

Set/read TEC voltage limit in V, as a float strictly in range -8.5 to 8.5.

 wait_for_temperature_stable(*tolerance=0.1*, *period=10*, *should_stop=<function LDC500SeriesTEC.<lambda>>*, *timeout=60*)

Block execution until the temperature reaches stability at the temperature setpoint.

Parameters:

-

**tolerance** Ã¢â‚¬â€œ Largest permitted offset from temperature setpoint, in degrees Centigrade. (default: `0.1`)

-

**period** Ã¢â‚¬â€œ Duration used for the stability check, in seconds. (default: `10`)

-

**should_stop** Ã¢â‚¬â€œ Function returning True requests that waiting stop. (default: `<function LDC500SeriesTEC.<lambda> at 0x7aa57d9701a0>`)

-

**timeout** Ã¢â‚¬â€œ Upper bound for waiting time, in seconds. (default: `60`)

Returns:

Returns True once stable, or False when should_stop stops the wait.

Raises:

**TimeoutError** Ã¢â‚¬â€œ Raised when temperature has not stabilized before the timeout period ends.

 *class *pymeasure.instruments.srs.ldc500series.ThermometerType(**values*)

Bases: `IntEnum`

ThermometerType choices supported by SRS LDC500Series. NTC means negative temperature coefficient; RTD means Resistance temperature detector.

Members:

>
-

**NTC10UA** : NTC thermistor excitation at 10 Ã‚ÂµA.

-

**NTC100UA** : NTC thermistor excitation at 100 Ã‚ÂµA.

-

**NTC1MA** : NTC thermistor excitation at 1 mA.

-

**NTCAUTO** : Finds the best NTC excitation automatically.

-

**RTD** : Usually Pt-100 or another PTC sensor

-

**LM335** : Temperature-to-voltage transducers compatible with LM335.

-

**AD590** : Temperature-to-current transducers compatible with AD590.

## SR830 Lock-in Amplifier

### SR830 Lock-in Amplifier

Class constructor: pymeasure.instruments.srs.SR830(adapter, **kwargs).
Default name: 'Stanford Research Systems SR830 Lock-in amplifier'.

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

 *property *adc1*: Any*

Read Aux input 1 in Volts, using 1/3 mV resolution.

 *property *adc2*: Any*

Read Aux input 2 in Volts, using 1/3 mV resolution.

 *property *adc3*: Any*

Read Aux input 3 in Volts, using 1/3 mV resolution.

 *property *adc4*: Any*

Read Aux input 4 in Volts, using 1/3 mV resolution.

 auto_offset(*channel*)

Zero-offset the selected channel: X, Y, or R.

 *property *aux_in_1*: Any*

Return Aux input 1 in Volts at 1/3 mV resolution.

 *property *aux_in_2*: Any*

Return Aux input 2 in Volts at 1/3 mV resolution.

 *property *aux_in_3*: Any*

Return Aux input 3 in Volts at 1/3 mV resolution.

 *property *aux_in_4*: Any*

Return Aux input 4 in Volts at 1/3 mV resolution.

 *property *aux_out_1*: Any*

Settable float property for Aux output 1 in Volts; accepted range is -10.5 V to +10.5 V.

 *property *aux_out_2*: Any*

Settable float property for Aux output 2 in Volts; accepted range is -10.5 V to +10.5 V.

 *property *aux_out_3*: Any*

Settable float property for Aux output 3 in Volts; accepted range is -10.5 V to +10.5 V.

 *property *aux_out_4*: Any*

Settable float property for Aux output 4 in Volts; accepted range is -10.5 V to +10.5 V.

 buffer_measure(*count*, *stopRequest=None*, *delay=0.001*)

Enter fast measurement mode, move buffer data, and calculate mean and std measurements.

Return mean and std values for both channels.

 *property *channel1*: Any*

Settable string property selecting Channel 1 type; allowed values are X, R, X Noise, Aux In 1, or Aux In 2.

 *property *channel2*: Any*

Settable string property selecting Channel 2 type; allowed values are Y, Theta, Y Noise, Aux In 3, or Aux In 4.

 clear()

Clear the instrument status byte.

 *property *dac1*: Any*

Settable float property for Aux output 1 in Volts; accepted range is -10.5 V to +10.5 V.

 *property *dac2*: Any*

Settable float property for Aux output 2 in Volts; accepted range is -10.5 V to +10.5 V.

 *property *dac3*: Any*

Settable float property for Aux output 3 in Volts; accepted range is -10.5 V to +10.5 V.

 *property *dac4*: Any*

Settable float property for Aux output 4 in Volts; accepted range is -10.5 V to +10.5 V.

 *property *err_status*: Any*

Read the lockin error (ERR) status byte. The result is an IntFlag whose string positions map to error flags:

| Bit | Status |
| --- | --- |
| 0 | unused |
| 1 | backup error |
| 2 | RAM error |
| 3 | unused |
| 4 | ROM error |
| 5 | GPIB error |
| 6 | DSP error |
| 7 | DSP error |

 fill_buffer(*count*, *has_aborted=<function SR830.<lambda>>*, *delay=0.001*)

Populate two numpy arrays from the instrument buffer contents.

Optionally wait until the requested number of recordings has completed.

 *property *filter_slope*: Any*

Settable integer property for filter slope. Valid values are 6, 12, 18, and 24 dB/octave; non-exact inputs are coerced upward to the next level.

 *property *filter_synchronous*: Any*

Settable boolean property for the synchronous filter; allowed values are True and False.

 *property *frequency*: Any*

Settable float property representing lock-in frequency in Hz.

 get_buffer(*channel=1*, *start=0*, *end=None*)

Acquire 32 bit floating point data by binary transfer.

 get_scaling(*channel*)

Return the offset percent and expansion term used for scaling the selected channel.

 *property *harmonic*: Any*

Settable integer property for the measured harmonic; allowed values are 1 to 19999.

 *property *id*: Any*

Return the instrument identification string.

 *property *input_config*: Any*

Settable string property for input configuration. Allowed values are: [Ã¢â‚¬ËœAÃ¢â‚¬â„¢, Ã¢â‚¬ËœA - BÃ¢â‚¬â„¢, Ã¢â‚¬ËœI (1 MOhm)Ã¢â‚¬â„¢, Ã¢â‚¬ËœI (100 MOhm)Ã¢â‚¬â„¢]

 *property *input_coupling*: Any*

Settable string property for input coupling. Allowed values are: [Ã¢â‚¬ËœACÃ¢â‚¬â„¢, Ã¢â‚¬ËœDCÃ¢â‚¬â„¢]

 *property *input_grounding*: Any*

Settable string property for input shield grounding. Allowed values are: [Ã¢â‚¬ËœFloatÃ¢â‚¬â„¢, Ã¢â‚¬ËœGroundÃ¢â‚¬â„¢]

 *property *input_notch_config*: Any*

Settable string property for input line notch filter status. Allowed values are: [Ã¢â‚¬ËœNoneÃ¢â‚¬â„¢, Ã¢â‚¬ËœLineÃ¢â‚¬â„¢, Ã¢â‚¬Ëœ2 x LineÃ¢â‚¬â„¢, Ã¢â‚¬ËœBothÃ¢â‚¬â„¢]

 is_out_of_range()

Return True when the magnitude is out of range.

 *property *lia_status*: Any*

Read the lockin amplifier (LIA) status byte. The return is a binary string whose positions map to status flags:

| Bit | Status |
| --- | --- |
| 0 | Input/Amplifier overload |
| 1 | Time constant filter overload |
| 2 | Output overload |
| 3 | Reference unlock |
| 4 | Detection frequency range switched |
| 5 | Time constant changed indirectly |
| 6 | Data storage triggered |
| 7 | unused |

 load_setup(*setup_number*)

Load an instrument configuration that was previously stored in the memory selected by an integer.

Parameters:

**setup_number** (`int`) Ã¢â‚¬â€œ integer identifying the memory, between 1 and 9 (included)

 *property *magnitude*: Any*

Reads the magnitude in Volts.

 output_conversion(*channel*)

Return a callable for determining signal from the selected channel output, X, Y, or R.

 pause_scan()

Pause the data recording

 *property *phase*: Any*

Settable float property representing lock-in phase in degrees.

 quick_range()

As long as magnitude remains out of range, step sensitivity up by one setting.

 *property *reference_source*: Any*

Settable string property for reference source. Allowed values are: [Ã¢â‚¬ËœExternalÃ¢â‚¬â„¢, Ã¢â‚¬ËœInternalÃ¢â‚¬â„¢]

 *property *reference_source_trigger*: Any*

Settable string property for reference source triggering. Allowed values are: [Ã¢â‚¬ËœSINEÃ¢â‚¬â„¢, Ã¢â‚¬ËœPOS EDGEÃ¢â‚¬â„¢, Ã¢â‚¬ËœNEG EDGEÃ¢â‚¬â„¢]

 reset()

Reset the instrument.

 *property *sample_frequency

Return the sample frequency in Hz.

 save_setup(*setup_number*)

Store the current instrument configuration, including all parameters, in the memory selected by an integer.

Parameters:

**setup_number** (`int`) Ã¢â‚¬â€œ integer identifying the memory, between 1 and 9 (included)

 *property *sensitivity*: Any*

Settable float property for sensitivity in Volts; it accepts discrete values from 2 nV to 1 V. Non-exact inputs move to the next highest level.

 set_scaling(*channel*, *percent*, *expand=0*, *precent=None*)

Set a channel offset, where X=1, Y=2, R=3, to a chosen percent (-105% to 105%) of the signal, optionally using expansion term 0, 10=1, 100=2. :rtype: `None`

Deprecated since version 0.17.0: the `precent` parameter is deprecated; use `percent` for the same behavior.

 *property *sine_voltage*: Any*

Settable float property representing reference sine-wave voltage in Volts.

 snap(*val1='X'*, *val2='Y'*, **vals*)

Record and retrieve 2 to 6 parameters at the same instant. Supported parameters include X, Y, R, and Theta.
Additional supported parameters include Aux In 1, Aux In 2, and Aux In 3.
The list also includes Aux In 4, Frequency, CH1, and CH2.
Defaults are â€œXâ€ and â€œYâ€.

Parameters:

-

**val1** Ã¢â‚¬â€œ first parameter retrieved (default: `'X'`)

-

**val2** Ã¢â‚¬â€œ second parameter retrieved (default: `'Y'`)

-

**vals** Ã¢â‚¬â€œ additional parameters to retrieve (optional)

 start_scan()

Begin recording data into the buffer.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 *property *theta*: Any*

Read theta in degrees.

 *property *time_constant*: Any*

Settable float property for time constant in seconds; discrete choices span 10 microseconds to 30,000 seconds. Non-exact inputs move to the next highest level.

 wait_for_buffer(*count*, *has_aborted=<function SR830.<lambda>>*, *timeout=60*, *timestep=0.01*)

Wait until the buffer reaches the requested count.

 *property *x*: Any*

Read X in Volts.

 *property *xy

Read X and Y in Volts.

 *property *y*: Any*

Read Y in Volts.

## SR570 Lock-in Amplifier

### SR570 Lock-in Amplifier

Class constructor: pymeasure.instruments.srs.SR570(adapter, **kwargs).
Default name: 'Stanford Research Systems SR570 Lock-in amplifier'.

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

 *property *bias_enabled*: Any*

Boolean that toggles the bias state. True enables bias; False disables bias.

 *property *bias_level*: Any*

Floating point V value for amplifier bias voltage level within [-5V,+5V], with values at up to 1 mV precision.

 blank_front()

Ã¢â‚¬Å“Blank the device frontend output

 clear_overload()

Ã¢â‚¬Å“Reset filter capacitors to clear an overload condition

 disable_bias()

Turns the bias voltage off

 disable_offset_current()

“Disables the offset current

 enable_bias()

Turns the bias voltage on

 enable_offset_current()

“Enables the offset current

 *property *filter_type*: Any*

String setting for filter type. Allowed values are: [Ã¢â‚¬Ëœ6dB HighpassÃ¢â‚¬â„¢, Ã¢â‚¬Ëœ12dB HighpassÃ¢â‚¬â„¢, Ã¢â‚¬Ëœ6dB BandpassÃ¢â‚¬â„¢, Ã¢â‚¬Ëœ6dB LowpassÃ¢â‚¬â„¢, Ã¢â‚¬Ëœ12dB LowpassÃ¢â‚¬â„¢, Ã¢â‚¬ËœnoneÃ¢â‚¬â„¢]

 *property *front_blanked*: Any*

Boolean that blanks (True) or un-blanks (False) the front panel.

 *property *gain_mode*: Any*

String setting for gain mode. Allowed values are: [Ã¢â‚¬ËœLow NoiseÃ¢â‚¬â„¢, Ã¢â‚¬ËœHigh BandwidthÃ¢â‚¬â„¢, Ã¢â‚¬ËœLow DriftÃ¢â‚¬â„¢]

 *property *high_freq*: Any*

Set amplifier highpass frequency with a floating point value on a discrete 1-3 sequence. Non-exact values are truncated to the closest allowed value. Allowed values range from 0.03 Hz to 1 MHz.

 *property *invert_signal_sign*: Any*

Boolean setting for signal invert sense. Allowed values are True (inverted) and False (not inverted).

 *property *low_freq*: Any*

Set amplifier lowpass frequency with a floating point value on a discrete 1-3 sequence. Non-exact values are truncated to the closest allowed value. Allowed values range from 0.03 Hz to 1 MHz.

 *property *offset_current*: Any*

Set the amplifier offset current absolute value in A within [1pA,5mA], using a floating point value. The offset current uses discrete 1-2-5 values; non-exact inputs are truncated to the closest allowed value.

 *property *offset_current_enabled*: Any*

Boolean that toggles offset current. True enables the current; False disables it.

 *property *offset_current_sign*: Any*

String setting for offset current sign. Allowed values are: Ã¢â‚¬ËœpositiveÃ¢â‚¬â„¢ and Ã¢â‚¬ËœnegativeÃ¢â‚¬â„¢.

 *property *sensitivity*: Any*

Set amplifier sensitivity with a floating point value chosen from a discrete 1-2-5 sequence. Non-exact values are truncated to the closest allowed value. Allowed values range from 1 pA/V to 1 mA/V.

 *property *signal_inverted*: Any*

Boolean that inverts the signal when True.

 unblank_front()

Restore the device frontend output from blanked state.
