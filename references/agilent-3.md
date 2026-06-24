# Agilent34450A, Agilent4294A, Agilent33220A, Agilent8722Es

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Scope includes the HP/Agilent/Keysight 34450A Digital Multimeter, the Agilent 4294A Precision Impedance Analyzer, the Agilent 33220A Arbitrary Waveform Generator, and the Agilent 8722ES Vector Network Analyzer.

## HP/Agilent/Keysight 34450A Digital Multimeter

### HP/Agilent/Keysight 34450A Digital Multimeter

Class constructor: pymeasure.instruments.agilent.Agilent34450A(adapter, name='HP/Agilent/Keysight 34450A Multimeter', **kwargs).

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Python interface for the HP/Agilent/Keysight 34450A and related multimeters.

```python
dmm = Agilent34450A("USB0::...")
dmm.reset()
dmm.configure_voltage()
print(dmm.voltage)
dmm.shutdown()

```

 beep()

Sounds a system beep.

 *property *capacitance*: Any*

Read capacitance in Farads using the active `mode`.

 *property *capacitance_auto_range*: Any*

Control auto ranging for capacitance.

 *property *capacitance_range*: Any*

Set or query capacitance range in Farads. Accepted values are 1E-9, 10E-9, 100E-9, 1E-6, 10E-6, 100E-6, 1E-3, 10E-3, plus “MIN”, “MAX”, or “DEF” (1E-6). Setting this property turns auto-range off.

 configure_capacitance(*capacitance_range='AUTO'*)

Prepare the instrument for capacitance measurements.

Parameters:

**capacitance_range** – Capacitance range to apply, in Farads: 1E-9, 10E-9, 100E-9, 1E-6, 10E-6, 100E-6, 1E-3, 10E-3, “MIN”, “MAX”, “DEF” (1E-6), or “AUTO”. (default: `'AUTO'`)

 configure_continuity()

Prepare the instrument for continuity measurements.

 configure_current(*current_range='AUTO'*, *ac=False*, *resolution='DEF'*)

Prepare the instrument for current measurements.

Parameters:

-

**current_range** – Current range to apply, in Amps. For DC, valid choices are 100E-6, 1E-3, 10E-3, 100E-3, 1, 10, “MIN”, “MAX”, “DEF” (100 mA), or “AUTO”. For AC, valid choices are 10E-3, 100E-3, 1, 10, “MIN”, “MAX”, “DEF” (100 mA), or “AUTO”. (default: `'AUTO'`)

-

**ac** – Use False for DC current and True for AC current (default: `False`)

-

**resolution** – Requested resolution; valid choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), “MIN”, “MAX”, or “DEF” (1.50E-6). (default: `'DEF'`)

 configure_diode()

Prepare the instrument for diode voltage measurements.

 configure_frequency(*measured_from='voltage_ac'*, *measured_from_range='AUTO'*, *aperture='DEF'*)

Prepare the instrument for frequency measurements.

Parameters:

-

**measured_from** – Select “voltage_ac” or “current_ac” (default: `'voltage_ac'`)

-

**measured_from_range** – Range applied to measured_from. AC voltage ranges are 100E-3, 1, 10, 100, 750, plus “MIN”, “MAX”, “DEF” (10 V), or “AUTO”. AC current ranges are 10E-3, 100E-3, 1, 10, plus “MIN”, “MAX”, “DEF” (100 mA), or “AUTO”. (default: `'AUTO'`)

-

**aperture** – Aperture time in Seconds; accepted choices are 100 ms, 1 s, “MIN”, “MAX”, or “DEF” (1 s). (default: `'DEF'`)

 configure_resistance(*resistance_range='AUTO'*, *wires=2*, *resolution='DEF'*)

Prepare the instrument for resistance measurements.

Parameters:

-

**resistance_range** – Resistance range to apply, in Ohms: 100, 1E3, 10E3, 100E3, 1E6, 10E6, 100E6, “MIN”, “MAX”, “DEF” (1E3), or “AUTO”. (default: `'AUTO'`)

-

**wires** – Wire count for the measurement, either 2 or 4. (default: `2`)

-

**resolution** – Requested resolution; valid choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), “MIN”, “MAX”, or “DEF” (1.50E-6). (default: `'DEF'`)

 configure_temperature()

Prepare the instrument for temperature measurements.

 configure_voltage(*voltage_range='AUTO'*, *ac=False*, *resolution='DEF'*)

Prepare the instrument for voltage measurements.

Parameters:

-

**voltage_range** – Voltage range to apply, in Volts. For DC, valid choices are 100E-3, 1, 10, 100, 1000, “MIN”, “MAX”, “DEF” (10 V), or “AUTO”. For AC, valid choices are 100E-3, 1, 10, 100, 750, “MIN”, “MAX”, “DEF” (10 V), or “AUTO”. (default: `'AUTO'`)

-

**ac** – Use False for DC voltage and True for AC voltage (default: `False`)

-

**resolution** – Requested resolution; valid choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), “MIN”, “MAX”, or “DEF” (1.50E-6). (default: `'DEF'`)

 *property *continuity*: Any*

Read continuity in Ohms using the active `mode`.

 *property *current*: Any*

Read DC current in Amps using the active `mode`.

 *property *current_ac*: Any*

Read AC current in Amps using the active `mode`.

 *property *current_ac_auto_range*: Any*

Enable or disable auto ranging for AC current.

 *property *current_ac_range*: Any*

Set or query AC current range in Amps. Allowed choices are 10E-3, 100E-3, 1, 10, plus “MIN”, “MAX”, or “DEF” (100 mA). Setting this property turns auto-range off.

 *property *current_ac_resolution*: Any*

Set the AC current reading resolution. Allowed choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), plus “MIN”, “MAX”, and “DEF” (1.50E-6).

 *property *current_auto_range*: Any*

Enable or disable auto ranging for DC current.

 *property *current_range*: Any*

Set or query DC current range in Amps. Allowed choices are 100E-6, 1E-3, 10E-3, 100E-3, 1, 10, plus “MIN”, “MAX”, or “DEF” (100 mA). Setting this property turns auto-range off.

 *property *current_resolution*: Any*

Set the DC current reading resolution. Allowed choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), plus “MIN”, “MAX”, and “DEF” (3.00E-5).

 *property *diode*: Any*

Read diode voltage in Volts using the active `mode`.

 *property *frequency*: Any*

Read frequency in Hz using the active `mode`.

 *property *frequency_aperture*: Any*

Set the frequency aperture in seconds; this determines integration period and measurement speed. Valid choices are 100 ms, 1 s, plus “MIN”, “MAX”, or “DEF” (1 s).

 *property *frequency_current_auto_range*: Any*

Enable or disable auto ranging for AC current while measuring frequency.

 *property *frequency_current_range*: Any*

Set or query the current range in Amps for frequency on AC current measurements. Allowed choices are 10E-3, 100E-3, 1, 10, plus “MIN”, “MAX”, or “DEF” (100 mA). Setting this property turns auto-range off.

 *property *frequency_voltage_auto_range*: Any*

Enable or disable auto ranging for AC voltage while measuring frequency.

 *property *frequency_voltage_range*: Any*

Set or query the voltage range in Volts for frequency on AC voltage measurements. Allowed choices are 100E-3, 1, 10, 100, 750, plus “MIN”, “MAX”, or “DEF” (10 V). Setting this property turns auto-range off.

 local()

Switch the instrument to local mode and restore front-panel control.

 *property *mode

Select the multimeter measurement mode. Supported options are the DC current mode “current”, the AC current mode “ac current”, the DC voltage mode “voltage”, the AC voltage mode “ac voltage”, the resistance mode “resistance”, the 4-wire resistance mode “4w resistance”, the AC-current frequency mode “current frequency”, the AC-voltage frequency mode “voltage frequency”, the continuity mode “continuity”, the diode mode “diode”, the temperature mode “temperature”, or the capacitance mode “capacitance”.

 *property *resistance*: Any*

Read resistance in Ohms for the 2-wire configuration using the active `mode`.

 *property *resistance_4w*: Any*

Read resistance in Ohms for the 4-wire configuration using the active `mode`.

 *property *resistance_4w_auto_range*: Any*

Enable or disable auto ranging for 4-wire resistance.

 *property *resistance_4w_range*: Any*

Set or query 4-wire resistance range in Ohms. Allowed choices are 100, 1E3, 10E3, 100E3, 1E6, 10E6, 100E6, plus “MIN”, “MAX”, or “DEF” (1E3). Setting this property turns auto-range off.

 *property *resistance_4w_resolution*: Any*

Set the 4-wire resistance reading resolution. Allowed choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), plus “MIN”, “MAX”, and “DEF” (1.50E-6).

 *property *resistance_auto_range*: Any*

Enable or disable auto ranging for 2-wire resistance.

 *property *resistance_range*: Any*

Set or query 2-wire resistance range in Ohms. Allowed choices are 100, 1E3, 10E3, 100E3, 1E6, 10E6, 100E6, plus “MIN”, “MAX”, or “DEF” (1E3). Setting this property turns auto-range off.

 *property *resistance_resolution*: Any*

Set the 2-wire resistance reading resolution. Allowed choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), plus “MIN”, “MAX”, and “DEF” (1.50E-6).

 *property *temperature*: Any*

Read temperature in Celsius using the active `mode`.

 *property *voltage*: Any*

Read DC voltage in Volts using the active `mode`.

 *property *voltage_ac*: Any*

Read AC voltage in Volts using the active `mode`.

 *property *voltage_ac_auto_range*: Any*

Enable or disable auto ranging for AC voltage.

 *property *voltage_ac_range*: Any*

Set or query AC voltage range in Volts. Allowed choices are 100E-3, 1, 10, 100, 750, plus “MIN”, “MAX”, or “DEF” (10 V). Setting this property turns auto-range off.

 *property *voltage_ac_resolution*: Any*

Set the AC voltage reading resolution. Allowed choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), plus “MIN”, “MAX”, or “DEF” (1.50E-6).

 *property *voltage_auto_range*: Any*

Enable or disable auto ranging for DC voltage.

 *property *voltage_range*: Any*

Set or query DC voltage range in Volts. Allowed choices are 100E-3, 1, 10, 100, 1000, plus “MIN”, “MAX”, or “DEF” (10 V). Setting this property turns auto-range off.

 *property *voltage_resolution*: Any*

Set the DC voltage reading resolution. Allowed choices are 3.00E-5, 2.00E-5, 1.50E-6 (5 1/2 digits), plus “MIN”, “MAX”, or “DEF” (1.50E-6).

## Agilent 4294A Precision Impedance Analyzer

### Agilent 4294A Precision Impedance Analyzer

Class constructor: pymeasure.instruments.agilent.Agilent4294A(adapter, **kwargs).
Default name: 'Agilent 4294A Precision Impedance Analyzer'.
Terminations default to read_termination='\n' and write_termination='\n'.
Default timeout setting: timeout=5000

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Python interface for the Agilent 4294A Precision Impedance Analyzer.

 *property *active_trace*: Any*

Control the active trace

 get_data(*path=None*)

After completion, retrieve measurement data from the instrument.

Parameters:

**path** – Optional CSV export path. (default: `None`)

Returns:

Pandas Dataframe

 *property *measurement_type*: Any*

Select the measurement type. See MEASUREMENT_TYPES

 *property *num_points*: Any*

Set the number of points measured for each sweep

 save_graphics(*path=''*)

Store the current screen graphics as a file on the local computer. Adapted from: [https://www.keysight.com/se/en/lib/software-detail/programming-examples/4294a-data-transfer-program-excel-vba-1645196.html](https://www.keysight.com/se/en/lib/software-detail/programming-examples/4294a-data-transfer-program-excel-vba-1645196.html)

 *property *start_frequency*: Any*

Set the start frequency in Hz

 *property *stop_frequency*: Any*

Set the stop frequency in Hz

 *property *title*: Any*

Set the title of the active trace

## Agilent 33220A Arbitrary Waveform Generator

### Agilent 33220A Arbitrary Waveform Generator

Class constructor: pymeasure.instruments.agilent.Agilent33220A(adapter, name='Agilent 33220A Arbitrary Waveform generator', **kwargs).

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Python interface for the Agilent 33220A Arbitrary Waveform Generator.

```python
# Default channel for the Agilent 33220A
wfg = Agilent33220A("GPIB::10")

wfg.shape = "SINUSOID"          # Sets a sine waveform
wfg.frequency = 4.7e3           # Sets the frequency to 4.7 kHz
wfg.amplitude = 1               # Set amplitude of 1 V
wfg.offset = 0                  # Set the amplitude to 0 V

wfg.burst_state = True          # Enable burst mode
wfg.burst_ncycles = 10          # A burst will consist of 10 cycles
wfg.burst_mode = "TRIGGERED"    # A burst will be applied on a trigger
wfg.trigger_source = "BUS"      # A burst will be triggered on TRG*

wfg.output = True               # Enable output of waveform generator
wfg.trigger()                   # Trigger a burst
wfg.wait_for_trigger()          # Wait until the triggering is finished
wfg.beep()                      # "beep"

print(wfg.check_errors())       # Get the error queue

```

 *property *amplitude*: Any*

Set the output waveform amplitude. The selected amplitude unit determines whether the value is Volt (peak-to-peak), Volt (RMS) or dBm. Limits vary with the configured output termination, with 50 Ohm to High Impedance changing by a factor of 2, and with the offset. The device may silently clip out-of-bound values (float, in V or dBm)

 *property *amplitude_unit*: Any*

Choose amplitude units (string, strict from VPP, VRMS, DBM).

 beep()

Causes a system beep.

 *property *beeper_state*: Any*

Turn the beeper on or off (bool).

 *property *burst_mode*: Any*

Set burst mode (string, strict from TRIG, TRIGGERED, GAT, GATED).

 *property *burst_ncycles*: Any*

Set the cycle count emitted after a burst trigger (int, strict from 1 to 50000).

 *property *burst_state*: Any*

Enable or disable burst mode (bool).

 *property *frequency*: Any*

Set output waveform frequency. Supported frequency range varies with the selected output shape. The device may silently clip out-of-bound values (float, in Hz)

 *property *offset*: Any*

Set the output waveform voltage offset. The amplitude and output termination impose the limit. The device may silently clip out-of-bound values. (float, in V)

 *property *output*: Any*

Enable or disable function generator output (bool).

 *property *pulse_dutycycle*: Any*

Set pulse waveform duty cycle in percent (float, strict from 0 to 100).

 *property *pulse_hold*: Any*

Choose whether pulse width or duty cycle is preserved when waveform period or frequency changes (string, strict from WIDT, WIDTH, DCYC, DCYCLE).

 *property *pulse_period*: Any*

Set pulse waveform period in seconds (float, strict from 200e-9 to 2e3). The period replaces frequency for all waveforms. If the period is shorter than pulse width + edge time, the edge time and pulse width are adjusted accordingly.

 *property *pulse_transition*: Any*

Set edge time in seconds for rising and falling edges. It is the interval between 0.1 and 0.9 of the threshold. Valid values run from 5 ns to 100 ns. Transition time must be smaller than 0.625 * the pulse width.

 *property *pulse_width*: Any*

Set pulse waveform width in seconds (float, strict from 20e-9 to 2e3).

 *property *ramp_symmetry*: Any*

Set ramp waveform symmetry percentage (float, strict from 0 to 100).

 *property *remote_local_state*: Any*

Set the function generator remote/local state (string, strict from LOC, LOCAL, REM, REMOTE, RWL, RWLOCK).

 *property *shape*: Any*

Choose the output waveform (string, strict from full names and aliases: SINUSOID / SIN, SQUARE / SQU, RAMP, PULSE / PULS, NOISE / NOIS, plus DC and USER).

 *property *square_dutycycle*: Any*

Set square waveform duty cycle (float, strict from 20 to 80).

 trigger()

Send a trigger signal to the function generator.

 *property *trigger_source*: Any*

Choose the trigger source (string, strict from IMM, IMMEDIATE, EXT, EXTERNAL, BUS).

 *property *trigger_state*: Any*

Enable or disable triggered output (bool).

 *property *voltage_high*: Any*

Set the output waveform upper voltage. Limits depend on output termination. The device may silently clip out-of-bound values. (float, in V)

 *property *voltage_low*: Any*

Set the output waveform lower voltage. Limits depend on output termination. The device may silently clip out-of-bound values. (float, in V)

 wait_for_trigger(*timeout=3600*, *should_stop=<function Agilent33220A.<lambda>>*)

Block until trigger activity completes or the timeout is reached.

Parameters:

-

**timeout** – Upper bound for waiting. Crossing that limit raises TimeoutError. A zero timeout disables the timeout. (default: `3600`)

-

**should_stop** – Optional callable returning a bool that can stop the wait before it completes. (default: `<function Agilent33220A.<lambda> at 0x7aa592a2e770>`)

## Agilent 8722ES Vector Network Analyzer

### Agilent 8722ES Vector Network Analyzer

 *class *pymeasure.instruments.agilent.Agilent8722ES(*adapter*, *name='Agilent 8722ES Vector Network Analyzer'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Python interface for the Agilent8722ES Vector Network Analyzer, with high-level support for scans of the scattering parameters.

 *property *averages*: Any*

Integer property for the number of averages to take. Averaging must be enabled before this has an effect. This property can be set.

 *property *averaging_enabled*: Any*

Boolean property indicating whether averaging is enabled. This property can be set.

 *property *data

Return real and imaginary data from the most recent scan

 *property *data_complex

Return complex power from the most recent scan

 *property *data_log_magnitude

Return absolute magnitude values in dB from the most recent scan

 *property *data_magnitude

Return absolute magnitude values from the most recent scan

 *property *data_phase

Return phase in degrees from the most recent scan

 disable_averaging()

Disables averaging

 enable_averaging()

Enables averaging

 *property *frequencies

Return a frequency list from the most recent scan

 is_averaging()

Return True when averaging is enabled

 log_magnitude(*real*, *imaginary*)

Return magnitude in dB from a real and imaginary number or numpy arrays

 magnitude(*real*, *imaginary*)

Return magnitude from a real and imaginary number or numpy arrays

 phase(*real*, *imaginary*)

Return phase in degrees from a real and imaginary number or numpy arrays

 scan(*averages=None*, *blocking=None*, *timeout=None*, *delay=None*)

Start a scan using the specified number of averages and block until completion.

 scan_continuous()

Initiates a continuous scan

 *property *scan_points

Return the number of scan points

 scan_single()

Initiates a single scan

 set_IF_bandwidth(*bandwidth*)

Set the resolution bandwidth (IF bandwidth)

 set_averaging(*averages*)

Set the number of averages and enable/disable averaging. Value should be between 1 and 999

 set_fixed_frequency(*frequency*)

Configure the scan for only one frequency in Hz

 *property *start_frequency*: Any*

Floating point property for the start frequency in Hz. This property can be set.

 *property *stop_frequency*: Any*

Floating point property for the stop frequency in Hz. This property can be set.

 *property *sweep_time*: Any*

Floating point property for sweep time in seconds. This property can be set.
