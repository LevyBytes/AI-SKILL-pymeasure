# Advantestr624X (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

For pulse or pulse-sweep operation, the WT command settings for pulse width (Tw), pulse period (Tp), and measure delay time (Td) must stay within their allowed limits. If those limits are missed, integration time will not change. To increase integration time, adjust pulse width (Tw) and pulse period (Tp) first; to reduce pulse width and pulse cycle, reduce integration time first.

 set_sample_mode(*mode*, *auto_sampling=True*)

Configure channel-to-channel behavior for synchronous, asynchronous, tracking, or search measurement operation (`JM`).

Parameters:

-

**mode** (`SampleMode`) – Sample Mode

-

**auto_sampling** (*bool**, **optional*) – Controls auto sampling; defaults to True. If True, each trigger causes measurement data to be output automatically. If False, output occurs only when explicitly requested, for example with `FCH?`. (default: `True`)

Warning

In dual-channel synchronous modes such as `PULSED_SYNC` and `SWEEP_SYNC`, pass `auto_sampling=False`. If `auto_sampling=True` (the default), data returned through `select_for_output()` / `FCH?` reports the generated/source value instead of the measured result.

 set_timing_parameters(*hold_time*, *measurement_delay*, *pulsed_width*, *pulsed_period*)

Configure hold time, measurement delay, pulse width, and pulse period (`WT`).

Parameters:

-

**hold_time** (*float*) – Duration of the full pulse cycle before the next pulse

-

**measurement_delay** (*float*) – Interval from one measurement to the next

-

**pulsed_width** (*float*) – Pulse-width time setting

-

**pulsed_period** (*float*) – Pulse-period time setting

Note

Pulse measurement restrictions depend on the pulse period (Tp) setting listed below. These limits do not apply to pulse sweep measurements.

>
-

Tp < 2ms : Not measured.

-

2ms <= Tp < 10ms : Measure once every 5 ~ 20ms.

-

10ms <= Tp: a measurement is taken whenever a pulse is generated.

 select_for_output()

Choose this channel as the source for measurement data output (`FCH?`).

Issues the FCH? query to choose the channel whose measurement data is returned. After that, call `read_measurement()` to retrieve the value.

The instrument manual recommends this sequence:

```python
smu.ch_A.select_for_output()   # Select channel A
smu.trigger()                   # Trigger measurement
value = smu.read_measurement()  # Read channel A data

```

If a prior trigger has already produced data, use this sequence instead:

```python
smu.ch_B.select_for_output()   # Switch to channel B
value = smu.read_measurement()  # Read channel B data

```

Note

Using the RMM command to read measurements does not change the channel chosen by the FCH command. By default, channel A measurement data is returned.

 trigger()

Issue a measurement trigger for a sweep, search measurement, or sweep step (`XE`).

 measure_voltage(*enable=True*, *internal_measurement=True*, *voltage_range=VoltageRange.AUTO*)

Configure voltage measurement ON/OFF, measurement input, and voltage measurement range (`RV`).

Parameters:

-

**enable** (*bool**, **optional*) – Boolean setting that turns voltage measurement on or off. True measures voltage at the OUTPUT terminal; False measures voltage from rear-panel -ANALOG COMMON. (default: `True`)

-

**internal_measurement** (*bool**, **optional*) – Boolean setting for enabling or disabling internal measurement. (default: `True`)

-

**voltage_range** (`VoltageRange`, optional) – Specifying voltage range (default: `<VoltageRange.AUTO: 0>`)

 voltage_source(*source_range*, *source_value*, *current_compliance*)

For DC (constant voltage) measurement (`DV`), configure current compliance along with source range and source value.

Parameters:

-

**source_range** (`VoltageRange`) – Specifying source range

-

**source_value** (*float*) – Numeric source voltage setting

-

**current_compliance** (*float*) – Numeric current compliance setting

Note

The instrument applies current compliance to both polarities (+ and -), regardless of the polarity supplied. It also selects the smallest current compliance range that can contain the configured value.

 voltage_pulsed_source(*source_range*, *pulse_value*, *base_value*, *current_compliance*)

For pulse (voltage) measurement (`PV`), configure current compliance together with source range, pulse value, and base value.

Note

The instrument applies current compliance to both polarities (+ and -), regardless of the polarity supplied. It also selects the smallest current compliance range that can contain the configured value.

Warning

For pulsed sources, call `measure_current()` with a fixed range such as `CurrentRange.FIXED_BEST`. Pulsed modes do not support `CurrentRange.AUTO` or `AUTO_*` ranges and return error 00211.

 *property *change_source_voltage*: Any*

Set new target voltage (`SPOT`).

Type:

float

Note

This changes only the DC action source value and the pulse action pulse value, reusing the DC action and pulse action parameters already configured. After changing them, measure and assign the channel whose measured data should be output to the specified ch. It is equivalent to these commands:

>
1.

DV/DI/PV/PI

2.

XE xx

3.

FCH xx

 voltage_fixed_level_sweep(*voltage_range*, *voltage_level*, *measurement_count*, *current_compliance*, *bias=0*)

For `FXV`, configure bias value, current compliance, level value, and the fixed level sweep (voltage) generation range.

Note

The instrument applies current compliance to both polarities (+ and -), regardless of the polarity supplied. It also selects the smallest current compliance range that can contain the configured value.

 voltage_fixed_pulsed_sweep(*voltage_range*, *pulse*, *base*, *measurement_count*, *current_compliance*, *bias=0*)

For `PXV`, configure bias value, current compliance, number of measurements, base value, pulse value, and the fixed pulse (voltage) sweep generation range.

Note

The instrument applies current compliance to both polarities (+ and -), regardless of the polarity supplied. It also selects the smallest current compliance range that can contain the configured value.

Warning

For pulsed sweeps, `measure_current()` must be used with a fixed range, for example `CurrentRange.FIXED_BEST`. Auto ranges are unsupported and cause error 00211.

 voltage_sweep(*sweep_mode*, *repeat*, *voltage_range*, *start_value*, *stop_value*, *steps*, *current_compliance*, *bias=0*)

For staircase (linear/log) voltage sweep (`WV`), configure bias value and current compliance, then the number of steps, stop value, start value, source range, number of repeats, and sweep mode.

Note

-

The following limits apply to sweep mode, number of repeats, and number of steps.

>
  -

Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.

>
    -

For output data output method 1 or 2 selected by the OFM command, keep m x number of refreshes x N <= 2048.

    -

If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

-

Both polarities (+ and -) receive current compliance, no matter which current compliance polarity was specified.

-

The instrument selects the smallest current compliance range that contains the configured value.

 voltage_pulsed_sweep(*sweep_mode*, *repeat*, *voltage_range*, *base*, *start_value*, *stop_value*, *steps*, *current_compliance*, *bias=0*)

For pulse wave (linear/log) voltage sweep (`PWV`), configure bias value, current compliance, number of steps, stop value, start value, base value, generation range, repeat count, and sweep mode.

Note

-

These restrictions apply to sweep mode, number of refreshes, and number of steps:

>
  -

Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.

>
    -

For output data output method 1 or 2 selected by the OFM command, keep m x number of refreshes x N <= 2048.

    -

If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

-

For current compliance polarity, the compliance setting is applied to both polarities (+ and -), independent of the requested polarity.

-

The instrument selects the smallest current compliance range that contains the configured value.

Warning

For pulsed sweeps, `measure_current()` must be used with a fixed range, for example `CurrentRange.FIXED_BEST`. Auto ranges are unsupported and cause error 00211.

 voltage_random_sweep(*sweep_mode*, *repeat*, *start_address*, *stop_address*, *current_compliance*, *bias=0*)

Configure constant voltage random sweep (`MDWV`). Set sweep mode, repeat count, start address, and stop address. Also set current compliance and bias value.

Note

-

The restrictions below apply to sweep mode, number of repeats, start address, and stop address:

>
  -

Start address < Stop address

  -

Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.

>
    -

For output data output method 1 or 2 selected by the OFM command, keep m x number of refreshes x N <= 2048.

    -

If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

-

Both polarities (+ and -) receive current compliance, no matter which current compliance polarity was specified.

-

The instrument selects the smallest current compliance range that contains the configured value.

 voltage_random_pulsed_sweep(*sweep_mode*, *repeat*, *start_address*, *stop_address*, *current_compliance*, *bias=0*)

For constant voltage random pulse sweep (`MPWV`), configure bias value and current compliance, plus stop address, start address, base value, repeat count, and sweep mode.

Note

-

The restrictions below apply to sweep mode, number of repeats, start address, and stop address:

>
  -

Start address < Stop address

  -

Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.

>
    -

For output data output method 1 or 2 selected by the OFM command, keep m x number of refreshes x N <= 2048.

    -

If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

-

Both polarities (+ and -) receive current compliance, no matter which current compliance polarity was specified.

-

The instrument selects the smallest current compliance range that contains the configured value.

 set_voltage_random_memory(*address*, *voltage_range*, *output*, *current_compliance*)

Write voltage parameters into random sweep data memory (`RMS`).

The MDWV, MDWI, MPWV, MPWI commands sweep the stored generated values over the selected memory address range.

 current_source(*source_range*, *source_value*, *voltage_compliance*)

For DC (constant current) measurement (`DI`), configure voltage compliance along with source range and source value.

Parameters:

-

**source_range** (`CurrentRange`) – Specifying source range

-

**source_value** (*float*) – Numeric source current setting

-

**voltage_compliance** (*float*) – Numeric voltage compliance setting

Note

Voltage compliance is set for both polarities (+ and -), regardless of the polarity supplied. The instrument chooses the smallest voltage compliance range that contains the configured value.

 current_pulsed_source(*source_range*, *pulse_value*, *base_value*, *voltage_compliance*)

For pulse (current) measurement (`PI`), configure voltage compliance together with source range, pulse value, and base value.

Note

Voltage compliance is set for both polarities (+ and -), regardless of the polarity supplied. The instrument chooses the smallest voltage compliance range that contains the configured value.

Warning

`source_range` must be a fixed range, for example `CurrentRange.FIXED_BEST`. Pulsed modes do not support `CurrentRange.AUTO` or `AUTO_*` ranges and return error 00211.

 *property *change_source_current*: Any*

Set new target current (`SPOT`).

Type:

float

Note

This changes only the DC action source value and the pulse action pulse value, reusing the DC action and pulse action parameters already configured. After changing them, measure and assign the channel whose measured data should be output to the specified ch. It is equivalent to these commands:

>
1.

DV/DI/PV/PI

2.

XE xx

3.

FCH xx

 current_fixed_level_sweep(*current_range*, *current_level*, *measurement_count*, *voltage_compliance*, *bias=0*)

For `FXI`, configure bias value, voltage compliance, level value, and the fixed level sweep (current) generation range.

Note

Voltage compliance is set for both polarities (+ and -), regardless of the polarity supplied. The instrument chooses the smallest voltage compliance range that contains the configured value.

 current_fixed_pulsed_sweep(*current_range*, *pulse*, *base*, *measurement_count*, *voltage_compliance*, *bias=0*)

For `PXI`, configure bias value, voltage compliance, number of measurements, base value, pulse value, and the fixed pulse (current) sweep generation range.

Note

Voltage compliance is set for both polarities (+ and -), regardless of the polarity supplied. The instrument chooses the smallest voltage compliance range that contains the configured value.

Warning

`current_range` must be a fixed range, for example `CurrentRange.FIXED_BEST`. `CurrentRange.AUTO` and `AUTO_*` ranges are unavailable for pulse sweep and cause error 00211.

 current_sweep(*sweep_mode*, *repeat*, *current_range*, *start_value*, *stop_value*, *steps*, *voltage_compliance*, *bias=0*)

For staircase (linear/log) current sweep (`WI`), configure bias value and voltage compliance, then the number of steps, stop value, start value, source range, number of repeats, and sweep mode.

Note

-

These restrictions apply to sweep mode, number of refreshes, and number of steps:

>
  -

Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.

>
    -

For output data output method 1 or 2 selected by the OFM command, keep m x number of repeats x N <= 2048.

    -

If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

-

Both polarities (+ and -) receive voltage compliance, regardless of the voltage compliance polarity specified.

-

The instrument selects the smallest voltage compliance range that contains the configured value.

 current_pulsed_sweep(*sweep_mode*, *repeat*, *current_range*, *base*, *start_value*, *stop_value*, *steps*, *voltage_compliance*, *bias=0*)

For pulse wave (linear/log) current sweep (`PWI`), configure bias value, voltage compliance, number of steps, stop value, start value, base value, generation range, repeat count, and sweep mode.

Note

-

These restrictions apply to sweep mode, number of refreshes, and number of steps:

>
  -

Use N = number of steps; use m = l for a one-way sweep and m = 2 for a round-trip sweep.

>
    -

For output data output method 1 or 2 selected by the OFM command, keep m x number of repeats x N <= 2048.

    -

If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

-

Both polarities (+ and -) receive voltage compliance, regardless of the voltage compliance polarity specified.

-

The instrument selects the smallest voltage compliance range that contains the configured value.

Warning

`current_range` must be a fixed range, for example `CurrentRange.FIXED_BEST`. `CurrentRange.AUTO` and `AUTO_*` ranges are unavailable for pulse sweep and cause error 00211.

 measure_current(*enable=True*, *internal_measurement=True*, *current_range=CurrentRange.AUTO*)

Configure current measurement ON/OFF, measurement input, and current measurement range (`RI`).

Parameters:

-

**enable** (*bool**, **optional*) – Boolean setting that turns current measurement on or off. True measures current at the OUTPUT terminal; False measures current from rear-panel -ANALOG COMMON. (default: `True`)

-

**internal_measurement** (*bool**, **optional*) – Boolean setting for enabling or disabling internal measurement. (default: `True`)

-

**current_range** (`CurrentRange`, optional) – Specifying current range. (default: `<CurrentRange.AUTO: 0>`)

Warning

`CurrentRange.AUTO` and `AUTO_*` ranges are invalid when the channel is set for pulse measurement or pulse sweep and will produce error 00211. For pulsed modes, select a fixed range such as `CurrentRange.FIXED_BEST`.

 current_random_sweep(*sweep_mode*, *repeat*, *start_address*, *stop_address*, *current_compliance*, *bias=0*)

Configure constant current random sweep (`MDWI`). Set sweep mode, repeat count, start address, and stop address. Also set voltage compliance and bias value.

Note

-

The restrictions below apply to sweep mode, number of repeats, start address, and stop address:

>
  -

Start address < Stop address

  -

Let N = (stop number 1 - start number + 1), m = 1 (one-way sweep), m = 2 (round-trip sweep).

>
    -

When the OFM command selects output data output method 1 or 2, observe the buffer-size constraint. The required condition is m x number of repeats x N <= 2048.

    -

If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

-

For voltage compliance polarity, both polarities of + and - are set regardless of the specified voltage compliance polarity.

-

The instrument selects the smallest voltage compliance range that contains the configured value.

 current_random_pulsed_sweep(*sweep_mode*, *repeat*, *start_address*, *stop_address*, *current_compliance*, *bias=0*)

For constant current random pulse sweep (`MPWI`), configure bias value and voltage compliance, plus stop address, start address, base value, repeat count, and sweep mode.

Note

-

The restrictions below apply to sweep mode, number of repeats, start address, and stop address:

>
  -

Start address < Stop address

  -

Let N = (stop number 1 - start number + 1), m = 1 (one-way sweep), m = 2 (round-trip sweep).

>
    -

When output data output method 1 or 2 is selected by the OFM command, keep the buffer-size rule satisfied. The condition is m x number of repeats x N <= 2048.

    -

If the OFM command sets the output data output method to 3, m x N <= 2048 must hold.

-

For voltage compliance polarity, both polarities of + and - are set regardless of the specified voltage compliance polarity.

-

The instrument selects the smallest voltage compliance range that contains the configured value.

 set_current_random_memory(*address*, *current_range*, *output*, *voltage_compliance*)

Write current parameters into random sweep data memory (`RMS`).

The MDWV, MDWI, MPWV, MPWI commands sweep the stored generated values over the selected memory address range.

 read_random_memory(*address*)

Read random sweep memory at a specified address (`RMS?`).

Parameters:

**address** (*int*) – Address identifying the memory location.

Returns:

Values set at the specified address location are returned by the device.

Return type:

str

 enable_source()

Set this channel to the operating state (`CN`).

 standby()

Set this channel to standby state (`CL`).

 stop()

Stop the sweep that was started by the XE command or trigger input signal (`SP`).

 output_all_measurements()

Return every measurement stored in this channel's measurement data buffer (`RMM?`).

Note

See `AdvantestR624X.output_format()` for the output format. Reading a memory address with no stored measurement data returns 999.999E+99.

 read_measurement_from_addr(*addr*)

Return one measurement from this channel's measurement data buffer at the specified memory address (`RMM?`).

Parameters:

**addr** (*int*) – Address to read.

Returns:

float Measurement data

Note

See `AdvantestR624X.output_format()` for the output format. Reading a memory address with no stored measurement data returns 999.999E+99.

 *property *measurement_count*: Any*

Read the count of measurements held in the measurement data buffer (`NUB?`).

 *property *null_operation_enabled*: Any*

Enable or disable the null operation (bool) (`NUG`).

Type:

bool

Note

-

Disabling the null operation does not rewrite null data.

-

Null data is rewritten only when the null operation changes from OFF to ON, or when initialization occurs during DC operation or pulse operation.

 set_wire_mode(*four_wire*, *lo_guard=True*)

Configure remote sense and the LO-GUARD relay ON/OFF (`OSL`).

Parameters:

-

**four_wire** (*bool*) – Boolean setting for four wire measurements. True enables 4-wire sensing; False enables two-terminal sensing.

-

**lo_guard** (*bool*) – Boolean setting that enables or disables the LO-GUARD relay.

 *property *auto_zero_enabled*: Any*

Turn the auto zero option ON or OFF (bool) (`CM`).

Type:

bool

This command configures auto zero, which automatically calibrates the measured-value zero point.

1.

Periodically perform auto zero.

2.

Run auto zero one time, with no repeated auto zero operations afterward.

If auto zero mode is True, these operations occur.

-

For DC operation and pulse operation:

>
  -

At the end of a sweep, when more than 10 seconds have elapsed since the previous autozero, one autozero is performed.

  -

If sweep start is requested during auto zero, the sweep begins after auto zero finishes.

-

Sweep operation

>
  -

Auto zero runs once per 10 seconds.

  -

If measurement or pulse output is requested during auto zero, it runs after auto zero completes.

 set_comparison_limits(*comparison*, *voltage_value*, *upper_limit*, *lower_limit*)

Configure measurement comparison ON/OFF and the upper/lower limit values (`CMD`).

Parameters:

-

**comparison** (*bool*) – Boolean setting that enables or disables the comparison function. Valid values are True or False.

-

**voltage_value** (*bool*) – Boolean setting that selects whether voltage or current values are passed. Valid values are True or False.

-

**upper_limit** (*float*) – Numeric upper comparison limit

-

**lower_limit** (*float*) – Numeric lower comparison limit

 *property *relay_mode*: Any*

Configure HI/LO relay behavior for standby mode (`OPM`).

Type:

int

1.

Mode where the HI side alone turns ON during execution, while standby turns both HI and LO OFF.

2.

Mode where the LO side alone turns ON during execution, while standby turns both HI and LO OFF.

3.

Mode where HI and LO both turn ON during execution, while standby turns both HI and LO OFF.

4.

Mode where the HI side alone turns ON during execution, while standby turns only the HI side OFF.

 *property *operation_register*: Any*

Read the Channel Operations Register (COR) as a `COR` `IntFlag` (`COC?`).

 *property *output_enable_register*: Any*

Use (`COE?`) with the channel operation output enable register (COER), represented as a `COR` `IntFlag`.

 init_calibration()

Initialize the calibration data (`CINI`).

 store_calibration_factor()

Save the calibration factor to non-volatile memory (EEPROM) (`CSRT`).

 calibration_init()

Initialize the calibration data.

Deprecated since version 0.16: call `init_calibration()` instead.

 calibration_store_factor()

Store the calibration factor.

Deprecated since version 0.16: call `store_calibration_factor()` instead.

 *property *calibration_measured_value*: Any*

Configure the externally measured standard value and begin calibration (`STD`).

Type:

float

 *property *calibration_generation_factor*: Any*

For the current generation range (`CCS`), configure the generation calibration factor increment or decrement.

Type:

float

 *property *calibration_measurement_factor*: Any*

Configure the increment for the measurement calibration factor of the current measurement range (`CCM`).

Type:

float

 *class *pymeasure.instruments.advantest.advantestR624X.SampleHold(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.SampleMode(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.VoltageRange(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.CurrentRange(**values*)

Bases: `IntEnum`

Current measurement/source range selection.

Warning

`AUTO` and `AUTO_*` (limited auto) ranges are invalid for pulse measurement or pulse sweep. In pulsed modes they trigger error 00211 (“command cannot be executed in current settings”); choose a fixed range such as `FIXED_BEST` instead.

With integration time in sample hold mode (SH) from 100 μs through 500 μs, resolution drops: 10 digits at 100 μs, 5 at 200 μs, and 2 at 500 μs.

 AUTO* = 0*

Auto range - selects the range automatically to maximize digits. **Cannot be used for pulse measurement or pulse sweep.**

 AUTO_6nA* = 23*

Limited auto range (minimum = 6nA). Works like auto range while enforcing a floor. **Cannot be used for pulse measurement or pulse sweep.**

 *class *pymeasure.instruments.advantest.advantestR624X.SweepMode(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.OutputType(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.TriggerInputType(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.MeasurementType(**values*)

Bases: `IntEnum`
