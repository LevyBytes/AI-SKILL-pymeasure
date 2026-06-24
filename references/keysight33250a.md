# Keysight33250A

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Keysight 33250A Function/Arbitrary Waveform Generator

Class constructor: pymeasure.instruments.keysight.Keysight33250A(adapter, **kwargs).
Default name: 'Keysight 33250A Function/Arbitrary Waveform Generator'.

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keysight 33250A 80 MHz Function/Arbitrary Waveform Generator.

 *property *amplitude*: Any*

Control the output amplitude.

 *property *amplitude_unit*: Any*

Control the output amplitude unit.

 beep()

Cause a system beep.

 *property *burst_enabled*: Any*

Get or set the enabled state for burst mode (bool).

 *property *burst_mode*: Any*

Control the burst mode.

 *property *burst_ncycles*: Any*

Get or set the burst-cycle count used after a burst trigger (int, strict from 1 to 1000000, or INF).

 *property *burst_period*: Any*

Get or set the interval between later bursts in seconds (float, strict from 1e-6 to 500).

 *property *burst_phase*: Any*

Get or set the burst-mode start phase in degrees (float, strict from -360 to 360).

 *property *frequency*: Any*

Get or set output waveform frequency in Hz (float, strict from 1e-6 to 80e6). The valid range depends on function: SIN/SQU 1e-6 to 80e6, RAMP 1e-6 to 1e6, PULS 500e-6 to 50e6, USER/ARB 1e-6 to 25e6.

 *property *offset*: Any*

Control the DC offset voltage.

 *property *output_enabled*: Any*

Get or set whether the main output is enabled (bool).

 *property *output_load*: Any*

Get or set the load resistance the output expects, expressed in Ohms. Accepts float values, strict from 1 to 10000, or INF.

 *property *output_polarity*: Any*

Get or set output polarity (string, strict from NORM, INV).

 *property *pulse_period*: Any*

Get or set the pulse waveform function period in seconds (float, strict from 20e-9 to 2000).

 *property *pulse_transition*: Any*

Get or set the transition duration for the rising and falling edges, using seconds. Accepts float values, strict from 5e-9 to 1e-3.

 *property *pulse_width*: Any*

Get or set the pulse waveform function width in seconds (float, strict from 8e-9 to 2000).

 *property *ramp_symmetry*: Any*

Get or set ramp waveform symmetry, expressed in percent.

 *property *shape*: Any*

Control the output waveform shape.

 *property *square_dutycycle*: Any*

Get or set square waveform function duty cycle in percent (float, strict from 20 to 80). Extra limits depend on frequency: 20-80% below 25 MHz, 40-60% from 25 to 50 MHz, and 50% above 50 MHz.

 *property *sync_output_enabled*: Any*

Get or set whether the sync output is enabled (bool).

 trigger()

Issue a trigger signal to the function generator.

 *property *trigger_delay*: Any*

Get or set trigger delay in seconds (float, strict from 0 to 85).

 *property *trigger_output_enabled*: Any*

Get or set whether trigger output is enabled (bool).

 *property *trigger_output_slope*: Any*

Get or set trigger output slope (string, strict from POS, NEG).

 *property *trigger_slope*: Any*

Get or set external trigger slope (string, strict from POS, NEG).

 *property *trigger_source*: Any*

Control the trigger source.

 *property *voltage_high*: Any*

Control the high voltage level.

 *property *voltage_low*: Any*

Control the low voltage level.

 wait_for_trigger(*timeout=None*, *should_stop=<function Keysight33250A.<lambda>>*)

Block until triggering is complete.

This method sends `*OPC?`, then waits for the instrument response `"1"`.

Parameters:

-

**timeout** (`Optional`[`float`]) â€“ Upper wait duration in seconds. `None` means wait without a time limit. (default: `None`)

-

**should_stop** (`Callable`[[], `bool`]) â€“ Callback that returns `True` to stop waiting before completion. (default: `<function Keysight33250A.<lambda> at 0x7aa581663cc0>`)

Raises:

**TimeoutError** â€“ Raised when `timeout` is not `None` and completion does not occur before expiration.

Return type:

`None`
