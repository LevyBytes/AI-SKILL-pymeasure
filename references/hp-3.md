# Hp3478A, Hp33120A, Hp8116A, Hp34401A

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: HP 3478A Multimeter, plus HP 33120A Arbitrary Waveform Generator, HP 8116A 50 MHz Pulse/Function Generator, and HP 34401A Multimeter.

## HP 3478A Multimeter

### HP 3478A Multimeter

 *class *pymeasure.instruments.hp.HP3478A(*adapter*, *name='Hewlett-Packard HP3478A'*, ***kwargs*)

Bases: [`HPLegacyInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html#pymeasure.instruments.hp.HPLegacyInstrument)

Model wrapper for the Hewlett Packard 3478A 5 1/2 digit multimeter, exposing high-level operations for the instrument.

 *class *ERRORS(**values*)

Bases: `IntFlag`

Enum member used when decoding errror bits.

 *property *SRQ_mask

Gets the active SRQ mask; the property is writable.

bit assigment for SRQ:

| Bit (dec) | Description |
| --- | --- |
| 1 | SRQ when Data ready |
| 4 | SRQ when Syntax error |
| 8 | SRQ when internal error |
| 16 | front panel SQR button |
| 32 | SRQ by invalid calibration |

 *property *active_connectors

Reports the selected connector (?front?/?back?) from the front-panel selector switch.

 *property *auto_range_enabled

Describes whether auto-ranging is active.

| Value | Status |
| --- | --- |
| True | auto-range function activated |
| False | manual range selection / auto-range disabled |

Use the `range` property to choose the range.

 *property *auto_zero_enabled

Gets auto-zero status; this property is writable.

| Value | Status |
| --- | --- |
| True | auto-zero active |
| False | auto-zero disabled |

 *property *calibration_data

Read and update calibration data as a 256-value array containing values from 0 through 15.

The HP 3478A calibration data resides in 256x4 SRAM kept alive by a 3v Lithium battery; if that battery is depleted, the data is erased and the instrument must be recalibrated.

On read, the property retrieves calibration data and returns it for backup use.

On assignment, provide an array of 256 values from 0 to 15; those values are written to the instrument.

Write operations raise exceptions in these cases:

-

The front-panel CAL ENABLE switch is not ON.

-

The value array has a length other than 256 elements.

-

The value array fails the verification check.

IMPORTANT: editing calibration data permanently replaces the prior data. Use with care!

 *property *calibration_enabled

Reports the calibration enable switch state from the front-panel selector switch.

| Value | Status |
| --- | --- |
| True | calbration possible |
| False | calibration locked |

 check_errors()

Reads the error status register.

Return error_status:

One byte carrying the error status register content.

Rtype error_status:

int

 display_reset()

Restores the instrument display to its reset state.

 *property *display_text*: Any*

Shows as many as 12 upper-case ASCII characters on the display.

 *property *display_text_no_symbol*: Any*

Shows as many as 12 upper-case ASCII characters while turning off every display symbol.

 *property *error_status*: Any*

Checks the error status register

 *property *measure_ACI*: Any*

Measured AC current value, returned as a float in A.

 *property *measure_ACV*: Any*

Measured AC Voltage value, returned as a float in V.

 *property *measure_DCI*: Any*

Measured DC current value, returned as a float in A.

 *property *measure_DCV*: Any*

Measured DC Voltage value, returned as a float in V.

 *property *measure_R2W*: Any*

Measured 2-wire resistance value, returned as a float in Ohm.

 *property *measure_R4W*: Any*

Measured 4-wire resistance value, returned as a float in Ohm.

 *property *measure_Rext*: Any*

Measured extended resistance mode (>30M, 2-wire) resistance, returned as a float in Ohm.

 *property *mode

Gets the selected measurement mode; this property is writable. Allowed values are

| Mode | Function |
| --- | --- |
| ACI | AC current |
| ACV | AC voltage |
| DCI | DC current |
| DCV | DC voltage |
| R2W | 2-wire resistance |
| R4W | 4-wire resistance |
| Rext | extended resistance method (requires additional 10 M resistor) |

 *property *range

Gets the active measurement range; this property is writable.

Valid values are :

| Mode | Range |
| --- | --- |
| ACI | 0.3, 3, auto |
| ACV | 0.3, 3, 30, 300, auto |
| DCI | 0.3, 3, auto |
| DCV | 0.03, 0.3, 3, 30, 300, auto |
| R2W | 30, 300, 3000, 3E4, 3E5, 3E6, 3E7, auto |
| R4W | 30, 300, 3000, 3E4, 3E5, 3E6, 3E7, auto |
| Rext | 3E7, auto |

 *property *resolution

Gets the selected resolution; this property is writable.

Allowed values are 3,4 or 5; these correspond respectively to 3 1/2, 4 1/2, and 5 1/2 resolution digits.

 status_desc

alias of `Status`

 *property *trigger

Gets the active trigger mode; this property is writable.

Possibe values are:

| Value | Meaning |
| --- | --- |
| auto | automatic trigger (internal) |
| internal | automatic trigger (internal) |
| external | external trigger (back-panel connector or GET) |
| hold | holds the measurement |
| fast | fast trigger for AC measurements |

 verify_calibration_data(*cal_data*)

Checks every calibration-entry checksum.

Requires an array of 256 values containing calibration data.

Return calibration_correct:

True if every checksum is correct.

Rtype calibration_correct:

boolean

 verify_calibration_entry(*cal_data*, *entry_nr*)

Checks the checksum for a single calibration entry.

Requires an array of 256 calibration-data values plus an entry number from 0 to 18.

Returns True if the selected calibration entry checksum is correct.

 write_calibration_data(*cal_data*, *verify_calibration_data=True*)

Method to write calibration data.

The cal_data parameter uses the same format as the `calibration_data` property.

Set `verify_calibration_data` to `False` to skip verification of the cal_data array.

## HP 33120A Arbitrary Waveform Generator

### HP 33120A Arbitrary Waveform Generator

 Class: pymeasure.instruments.hp.HP33120A; parameters: adapter, name='Hewlett Packard 33120A Function Generator', **kwargs.

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model wrapper for the Hewlett Packard 33120A Arbitrary Waveform Generator, exposing high-level operations for the instrument.

 *property *amplitude*: Any*

Sets or reads output-signal voltage amplitude. Units default to peak-to-peak Volts and can be changed with `amplitude_units`; waveform shape determines the allowed range, which `max_amplitude` and `min_amplitude` can query. (float)

 *property *amplitude_units*: Any*

Sets the amplitude units; accepted values are Vpp, Vrms, dBm, and default. (str)

 beep()

Causes a system beep.

 *property *burst_count*: Any*

Sets the burst length in cycles (1 to 50,000 cycles).

 *property *burst_enabled*: Any*

Control state of burst modulation

 *property *burst_phase*: Any*

Sets the burst starting phase angle (-360 to +360 degrees).

 *property *burst_rate*: Any*

Sets the internal burst-source rate in Hz.

 *property *burst_source*: Any*

Selects internal or external as the gate source for burst modulation.

 *property *frequency*: Any*

Sets output frequency in Hz. Waveform shape determines the allowed range, and `max_frequency` / `min_frequency` can query it. (float)

 *property *max_amplitude*: Any*

Returns the maximum `amplitude` in Volts for the requested shape.

 *property *max_burst_count*: Any*

Get the maximum `burst_count`

 *property *max_burst_phase*: Any*

Get the maximum `burst_phase`

 *property *max_burst_rate*: Any*

Get the maximum `burst_rate`

 *property *max_frequency*: Any*

Returns the maximum `frequency` in Hz for the requested shape.

 *property *max_offset*: Any*

Returns the maximum `offset` in Volts for the requested shape.

 *property *min_amplitude*: Any*

Returns the minimum `amplitude` in Volts for the requested shape.

 *property *min_burst_count*: Any*

Get the minimum `burst_count`

 *property *min_burst_phase*: Any*

Get the minimum `burst_phase`

 *property *min_burst_rate*: Any*

Get the minimum `burst_rate`

 *property *min_frequency*: Any*

Returns the minimum `frequency` in Hz for the requested shape.

 *property *min_offset*: Any*

Returns the minimum `offset` in Volts for the requested shape.

 *property *offset*: Any*

Sets the amplitude voltage offset in Volts. Waveform shape determines the allowed range, which `max_offset` and `min_offset` can query.

 *property *shape*: Any*

Sets the waveform shape; allowed values are sinusoid, square, triangle, ramp, noise, dc, and user. (str)

## HP 8116A 50 MHz Pulse/Function Generator

### HP 8116A 50 MHz Pulse/Function Generator

 *class *pymeasure.instruments.hp.HP8116A(*adapter*, *name='Hewlett-Packard 8116A'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model wrapper for the Hewlett-Packard 8116A 50 MHz Pulse/Function Generator, exposing high-level operations for the instrument. Floating point instrument parameters use 3 digits of resolution.

 *class *Digit(**values*)

Bases: `Enum`

Enum for digits used by the autovernier (see `HP8116A.start_autovernier()`).

 *class *Direction(**values*)

Bases: `Enum`

Enum for autovernier directions (see `HP8116A.start_autovernier()`).

 GPIB_trigger()

Starts a trigger using the low-level GPIB-command, also called GET - group execute trigger.

 *property *amplitude*: Any*

Sets output amplitude in V (strict float from 10e-3 to 16). The current offset further constrains the allowed amplitude range.

 ask(*command*, *num_bytes=None*)

Sends a command to the instrument, reads the reply, and returns that reply as ASCII text.

Parameters:

-

**command** ? Command sent to the instrument.

-

**num_bytes** ? Number of bytes to read from the instrument. When omitted, the command determines the byte count automatically. (default: `None`)

 *property *autovernier_enabled*: Any*

Enables or disables the autovernier (bool).

 *property *burst_number*: Any*

Sets the burst period count (strict int from 1 to 1999). This applies only to units with Option 001 while using one of the burst modes.

 check_errors()

Checks the 8116A for errors.

Returns:

List of error entries, or an empty list when no error occurred.

 *property *complement_enabled*: Any*

Enables generation of the signal complement (bool).

 *property *complete

Returns whether the measurement has completed (bool).

 *property *control_mode*: Any*

Sets the instrument control mode. Possible values are ?off?, ?FM?, ?AM?, ?PWM?, ?VCO?.

 *property *duty_cycle*: Any*

Sets output duty cycle in percent (float). The range is generally 10 % to 90 %, but current frequency also affects it. Valid for every shape except ?pulse?; use `pulse_width` for ?pulse?.

 *property *frequency*: Any*

Sets output frequency in Hz (strict float from 1e-3 to 52.5e6).

 *property *haversine_enabled*: Any*

Enables generation of a haversine/havertriangle signal in ?triggered?, ?internal_burst? or ?external_burst? operating mode.

 *property *high_level*: Any*

Sets the output high level in V (strict float from -7.9 to 8). The high level must be at least 10 mV above the low level.

 *property *limit_enabled*: Any*

Enables or disables parameter limiting (bool).

 *property *low_level*: Any*

Sets the output low level in V (strict float from -8 to 7.9). The low level must be at least 10 mV below the high level.

 *property *offset*: Any*

Sets the output offset in V (strit float from -7.95 to 7.95). Amplitude also constrains the allowed offset range.

 *property *operating_mode*: Any*

Sets the operating mode. Without Option 001, use one of: ?normal?, ?triggered?, ?gate?, ?external_width?. Option 001 additionally exposes: ?internal_sweep?, ?external_sweep?, ?external_width?, ?external_pulse?.

 *property *options

Returns installed device options; the only possible option is 001.

 *property *output_enabled*: Any*

Enables or disables the output (bool).

 *property *pulse_width*: Any*

Sets pulse width in s (strict float from 8e-9 to 999e-3). Pulse width cannot exceed the period.

 *property *repetition_rate*: Any*

Sets repetition rate in s, meaning the time between bursts, for ?internal_burst? mode (strict float from 20e-9 to 999e-3).

 reset()

Starts an 8116A reset equivalent to a power-on reset.

 *property *shape*: Any*

Sets output waveform shape. Possible values are: ?dc?, ?sine?, ?triangle?, ?square?, ?pulse?.

 shutdown()

Closes the 8116A connection cleanly.

 start_autovernier(*control*, *digit*, *direction*, *start_value=None*)

Starts autovernier for the selected control.

Parameters:

-

**control** ? Control to modify, passed as `HP8116A.some_control`. Allowed controls are frequency, amplitude, offset, duty_cycle, and pulse_width

-

**digit** ? Digit to modify; type: `HP8116A.Digit`.

-

**direction** ? Direction used to modify the control; type: `HP8116A.Direction`.

-

**start_value** ? Optional starting value for autovernier. If omitted, the current value of the control is used. (default: `None`)

 *property *status

Returns the 8116A status byte as a `Status` IntFlag-type enum.

 *property *sweep_marker_frequency*: Any*

Sets the frequency marker, specified in Hz as a strict float from 1e-3 to 52.5e6, for both sweep modes. At that frequency, marker output changes from low to high.

 *property *sweep_start*: Any*

Sets the sweep start frequency, in Hz, for both sweep modes (strict float from 1e-3 to 52.5e6).

 *property *sweep_stop*: Any*

Sets the sweep stop frequency, in Hz, for both sweep modes (strict float from 1e-3 to 52.5e6).

 *property *sweep_time*: Any*

Sets sweep time per decade for both sweep modes in s (float). Selectable sweep times follow a 1-2-5 sequence from 10 ms through 500 s.

 *property *trigger_slope*: Any*

Sets the trigger slope. Possible values are: ?off?, ?positive?, ?negative?.

 write(*command*)

Sends a command to the instrument and waits until the 8116A has interpreted it.

## HP 34401A Multimeter

### HP 34401A Multimeter

 *class *pymeasure.instruments.hp.HP34401A(*adapter*, *name='HP 34401A'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model wrapper for the HP / Agilent / Keysight 34401A Multimeter, exposing high-level operations for the instrument.

```python
dmm = HP34401A("GPIB::1")
dmm.function_ = "DCV"
print(dmm.reading)  # -> Single float reading

dmm.nplc = 0.02
dmm.autozero_enabled = False
dmm.trigger_count = 100
dmm.trigger_delay = "MIN"
print(dmm.reading)  # -> Array of 100 very fast readings

```

 *property *auto_input_impedance_enabled*: Any*

Enables or disables automatic input resistance mode.

Valid only during dc voltage measurements. Disabled by default, it fixes input resistance at 10 MOhms on every range; with AUTO ON, input resistance becomes >10 GOhms on the 100 mV, 1 V, and 10 V ranges.

 *property *autorange*: Any*

Sets the autorange state for the active function.

 *property *autozero_enabled*: Any*

Control the autozero state.

 beep()

Makes the multimeter emit one beep.

 *property *beeper_enabled*: Any*

Enables or disables the beeper.

 *property *current_ac*: Any*

AC current, in Amps

Deprecated since version 0.12: prefer the `function_` and `reading` properties.

 *property *current_dc*: Any*

DC current, in Amps

Deprecated since version 0.12: prefer the `function_` and `reading` properties.

 *property *detector_bandwidth*: Any*

Sets the lowest expected input-signal frequency in Hertz.

Valid values: 3, 20, 200, “MIN”, “MAX”.

 *property *display_enabled*: Any*

Control the display state.

 *property *displayed_text*: Any*

Sets the text shown on the multimeter?s display.

Text length is limited to 12 characters; the multimeter truncates anything beyond that.

 *property *function_*: Any*

Control the measurement function.

Allowed values: “DCV”, “DCV_RATIO”, “ACV”, “DCI”, “ACI”, “R2W”, “R4W”, “FREQ”, “PERIOD”, “CONTINUITY”, “DIODE”.

 *property *gate_time*: Any*

Sets gate time, also called aperture time, for frequency or period measurements.

Valid values: 0.01, 0.1, 1, ?MIN?, ?MAX?. Specifically, 0.01 selects 10 ms (4.5 digits); 0.1 selects 100 ms (default; 5.5 digits); 1 selects 1 second (6.5 digits).

 init_trigger()

Moves the triggering system into the ?wait-for-trigger? state.

After this command is received, measurements start once the configured trigger conditions are met.

 *property *nplc*: Any*

Sets integration time as a number of power line cycles (NPLC).

Allowed settings are 0.02, 0.2, 1, 10, 100, ?MIN?, and ?MAX?. The command applies to these functions only: dc volts, ratio, dc current, 2-wire ohms, and 4-wire ohms.

 *property *range_*: Any*

Sets the range for the active function.

For frequency and period measurements, range selection concerns the signal?s input voltage rather than its frequency

 *property *reading*: Any*

Performs a measurement using the selected function.

Reading this property behaves like calling init_trigger(), waiting for completion, then fetching the reading(s).

 *property *remote_control_enabled*: Any*

Enables or disables remote control.

 *property *remote_lock_enabled*: Any*

Enables or disables the beeper.

 *property *resistance*: Any*

Resistance, in Ohms

Deprecated since version 0.12: prefer the `function_` and `reading` properties.

 *property *resistance_4w*: Any*

Four-wires (remote sensing) mode, resistance in Ohms.

Deprecated since version 0.12: prefer the `function_` and `reading` properties.

 *property *resolution*: Any*

Sets measurement resolution.

Not valid for frequency, period, or ratio. Enter resolution in the active measurement function?s units, not as a digit count. If autorange is enabled, this produces a ?Settings Conflict? error. MIN selects the smallest accepted value and therefore highest resolution; MAX selects the largest accepted value and therefore lowest resolution.

 *property *sample_count*: Any*

Sets how many samples are taken for each trigger event.

Valid values: 1 to 50000, “MIN”, “MAX”.

 *property *scpi_version*: Any*

The SCPI version reported by the multimeter.

 *property *self_test_result*: Any*

Runs the multimeter self-test and returns its result.

Set a suitable connection timeout; otherwise this command will fail.

 *property *stored_reading*: Any*

Fetches the reading(s) currently held in the multimeter?s internal memory.

Reading this property does NOT start a trigger. Use the reading property when triggering is required.

 *property *stored_readings_count*: Any*

Count of readings currently stored in internal memory.

 *property *terminals_used*: Any*

Queries which input terminals, front or rear, are selected on the multimeter.

Returns “FRONT” or “REAR”.

 *property *trigger_auto_delay_enabled*: Any*

Enables or disables automatic trigger delay.

When enabled, delay is computed from function, range, integration time, and ac filter setting. Setting an explicit trigger delay value disables automatic trigger delay.

 *property *trigger_count*: Any*

Sets how many triggers are accepted before the instrument returns to the ?idle? state.

Valid values: 1 to 50000, ?MIN?, ?MAX?, ?INF?. The INFinite parameter makes the multimeter keep accepting triggers continuously; send a device clear to return to the ?idle? state.

 *property *trigger_delay*: Any*

Sets trigger delay in seconds.

Valid values (incl. floats): 0 to 3600 seconds, ?MIN?, ?MAX?.

 trigger_single_autozero()

Trigger an autozero measurement.

Consequent autozero measurements are disabled.

 *property *trigger_source*: Any*

Control the trigger source.

Valid values: ?IMM?, ?BUS?, ?EXT?. These select, respectively, an immediate internal trigger (default source), a software (bus) trigger, or a hardware trigger at the rear-panel Ext Trig (external trigger) terminal.

 *property *voltage_ac*: Any*

AC voltage, in Volts

Deprecated since version 0.12: prefer the `function_` and `reading` properties.

 write(*command*)

Sends a command to the instrument.
