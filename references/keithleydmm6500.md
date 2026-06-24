# Keithleydmm6500 (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Keithley DMM6500 Multimeter

 *class *pymeasure.instruments.keithley.KeithleyDMM6500(*adapter*, *name='Keithley DMM6500 6½-Digit Multimeter'*, *read_termination='\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model the Keithely DMM6500 6??-Digit Multimeter and expose a higher-level API for instrument operations. Communication in this class is limited to the `SCPI` command set; see `command_set` as well.

```python
# Access via LAN
ip_address = "xxx.xxx.xxx.xxx"
dmm = KeithleyDMM6500(f"TCPIP::{ip_address}::inst0::INSTR")

```

You may identify the DMM6500 USB port name with PyVISA, then pass that name to `KeithleyDMM6500`.

```python
import pyvisa
rm = pyvisa.ResourceManager()
resources = rm.list_resources()

# assume there is only one USB instruments
# Ex. ('USB0::1510::25856::01234567::0::INSTR')

dmm = KeithleyDMM6500( resources[0] )

# Measure voltage
dmm.measure_voltage()
print(dmm.voltage)

# Measure AC voltage
dmm.measure_voltage(ac=True)
print(dmm.voltage)

```

 channels

Channels:

`ch_1`: `ScannerCard2000Channel`, `ch_2`: `ScannerCard2000Channel`, `ch_3`: `ScannerCard2000Channel`, `ch_4`: `ScannerCard2000Channel`, `ch_5`: `ScannerCard2000Channel`, `ch_6`: `ScannerCard2000Channel`, `ch_7`: `ScannerCard2000Channel`, `ch_8`: `ScannerCard2000Channel`, `ch_9`: `ScannerCard2000Channel`, `ch_10`: `ScannerCard2000Channel`

 acquire_relative(*mode=None*)

Use the active reading as the relative value for the active mode, or provide a mode name to target a different mode.

Parameters:

**mode** ??? A valid `mode` name, or None to use the active mode (default: `None`)

Returns:

The acquired relative value

 *property *aperture*: Any*

Manage the aperture time for the currently active `mode`.

Accepted values are `MIN`, `DEF`, `MAX`, or a number from 8.333u through 0.25 s.

Note

Aperture configuration applies to `voltage`, `current`, `resistance`, and `resistance 4W`; it also applies to `diode`, `temperature`, `frequency`, `period`, and `voltage ratio` mode. If the active mode has no aperture support, the command waits for the adapter timeout and then raises -113 "Undefined header".

 auto_range(*mode=None*)

Enable auto-range for the active mode, or pass a mode name to configure another mode.

Autorange support covers these modes: `current` (DC) and `current ac`; `voltage` (DC) and `voltage ac`; `resistance` (2-wire) and `resistance 4W` (4-wire); plus `capacitance` and `voltage ratio`. Selecting any other mode leaves the instrument unchanged.

Parameters:

**mode** ??? A valid `mode` name, or None to use the active mode (default: `None`)

 auto_range_status(*mode=None*)

Return whether auto-range is enabled for the active mode, or for a supplied mode name. Supported modes are grouped as `current` (DC) with `current ac`, `voltage` (DC) with `voltage ac`, `resistance` (2-wire) with `resistance 4W` (4-wire), plus `capacitance` and `voltage ratio`; unsupported modes also return `False`.

Parameters:

**mode** ??? A valid `mode` name, or None to use the active mode (default: `None`)

Returns:

Boolean indicating whether auto-range is enabled

Return type:

bool

 *property *autorange_enabled*: Any*

Set the autorange state for the currently active `mode`.

Note

When the active mode has no autorange command, this call waits for the adapter timeout and then reports -113 "Undefined header".

 *property *autozero_enabled*: Any*

Configure autozero, the instrument feature that automatically refreshes internal reference measurements.

 beep(*frequency*, *duration*)

Sound a system beep.

Parameters:

-

**frequency** ??? Frequency in Hz from 20 Hz through 8000 Hz

-

**duration** ??? Tone playback time from 0.001 s through 100 s

Returns:

None

 *property *buffer_points*: Any*

Set the configured buffer point count. This value is the buffer configuration, not the current occupied point count. `0` requests the largest buffer allowed by available memory at buffer creation time.

 *property *buffer_size*: Any*

Adjust the configured number of buffer points. It is not the number of points currently stored; it is the setup value. `0` means create the biggest buffer that available memory permits.

 *property *capacitance*: Any*

Read capacitance in Farad using the active `mode`.

 *property *capacitance_digits*: Any*

Set capacitance display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *capacitance_range*: Any*

Set the capacitance full-scale measurement range in Farad. Use 1e-9, 10e-9, or 100e-9 for the smallest ranges; 1e-6, 10e-6, or 100e-6 for larger ranges; or 1e-3 at the top end. Setting this property turns auto-range off. See also the `range`.

 *property *capacitance_relative*: Any*

Set the capacitance relative value in Farad. The allowed value is a float greater than -0.001 and less than 0.001 F. See also the `relative`.

 *property *capacitance_relative_status*: Any*

Set whether a relative offset value is applied during capacitance measurement. See also the `relative_enabled`.

 close()

Close the connection

 *property *command_set*: Any*

Select the command set used by the DMM6500. The instrument must be rebooted after this setting changes. Available values are `SCPI`, `TSP`, `SCPI2000`, and `SCPI34401`. The `KeithleyDMM6500` class is implemented for the `SCPI` command set only.

Note

For the TSP command set, send TSP commands directly with `write()` and `ask()` instead.

 *property *current*: Any*

Read DC or AC current in Amps using the active `mode`.

 *property *current_ac_bandwidth*: Any*

Set the AC current detector bandwidth in Hz, restricted to the integers 3, 30, and 300.

 *property *current_ac_digits*: Any*

Set the number of displayed AC current digits, using an integer strictly from 3 to 6. See also the `digits`.

 *property *current_ac_range*: Any*

Set the positive full-scale range for AC current in Amps. Front-terminal ranges are 1e-3, 10e-3, 100e-3, 1, and 3 Amps; rear terminals allow 10 Amps. See also the `range`.

 *property *current_ac_relative*: Any*

Set the AC current relative value in Amps, as a float strictly from -3 to 3. See also the `relative`.

 *property *current_ac_relative_enabled*: Any*

Set whether a relative offset value is applied during AC current measurement. See also the `relative_enabled`.

 *property *current_digits*: Any*

Set DC current display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *current_nplc*: Any*

Set the DC current integration in number of power line cycles (NPLC), as a float strictly from 0.0005 to 15. See also the `nplc`.

 *property *current_range*: Any*

Set the DC current full-scale range in Amps. Front-terminal range options start at 10e-6 and 100e-6, continue through 1e-3, 10e-3, and 100e-3, and also include 1 and 3 Amps; rear terminals allow 10 Amps. Setting this property disables auto-range. See also the `range`.

 *property *current_relative*: Any*

Set the DC current relative value in Amps, as a float strictly from -3 to 3. See also the `relative`.

 *property *current_relative_enabled*: Any*

Set whether a relative offset value is applied during DC current measurement. See also the `relative_enabled`.

 *property *data_format*: Any*

Choose the data format used to transfer readings through the remote interface. Supported values are `ASC` (ASCII), `REAL` (double-precision), or `SRE` (single-precision).

 *property *detector_bandwidth*: Any*

Set the lowest expected input-signal frequency in Hz, only for AC voltage and AC current measurements.

Valid values: 3, 30, 300, `MIN`, `DEF`, `MAX`.

 *property *digits*: Any*

Set how many digits are displayed for the currently active `mode`. Values from 3 to 6 correspond to 3.5 through 6.5 display digits.

 *property *diode*: Any*

Measure either the forward voltage drop of general-purpose diodes or, for Zener diodes, the Zener voltage on the 10V range using a constant test current (bias level), based on the active `mode`.

 *property *diode_bias*: Any*

Set the source current in Amps used during measurement. Bias choices are 1e-5, 0.0001, 0.001, and 0.01.

 *property *diode_nplc*: Any*

Set the diode measurement integration in number of power line cycles (NPLC), as a float strictly from 0.0005 to 15. See also the `nplc`.

 disable_filter(*mode=None*)

Turn off the averaging filter for the active mode, or provide a mode name to affect another mode.

Parameters:

**mode** ??? A valid `mode` name, or None to use the active mode (default: `None`)

Returns:

Filter status returned by the instrument

 disable_relative(*mode=None*)

Disable relative-offset application for measurements in the active mode, or pass a mode name for a different mode.

Parameters:

**mode** ??? A valid `mode` name, or None to use the active mode (default: `None`)

 *property *display_screen*: Any*

Choose the front-panel screen by name. Home and data screens are `HOME` (home), `HOME_LARG` (home screen with large readings), `READ` (reading table), and `HIST` (histogram). For swipe screens, select `SWIPE_FUNC` for the FUNCTIONS swipe screen, `SWIPE_GRAP` for the GRAPH swipe screen, `SWIPE_SEC` for the SECONDARY swipe screen, `SWIPE_SETT` for the SETTINGS swipe screen, `SWIPE_STAT` for the STATISTICS swipe screen, `SWIPE_USER` for the USER swipe screen, `SWIPE_CHAN` for the CHANNEL swipe screen, `SWIPE_NONS` for the NONSWITCH swipe screen, or `SWIPE_SCAN` for the SCAN swipe screen. Channel choices are `CHANNEL_CONT` (Channel control screen), `CHANNEL_SETT` (Channel settings screen), and `CHANNEL_SCAN` (Channel scan screen); `PROC` selects minimal CPU resources.

 displayed_text(*top_line=None*, *bot_line=None*)

Show text messages on the front-panel USER swipe screen. If no messages are supplied, the screen is cleared.

Parameters:

-

**top_line** – 1st line message (default: `None`)

-

**bot_line** – 2nd line message (default: `None`)

Returns:

None

 enable_filter(*mode=None*, *type='repeat'*, *count=1*)

Turn on the averaging filter for the active mode, or pass a mode name to affect another mode.

Parameters:

-

**mode** ??? A valid `mode` name, or None to use the active mode (default: `None`)

-

**type** ??? Averaging filter type; valid choices are `REPeat`, `MOVing`, or `HYBRid`. (default: `'repeat'`)

-

**count** ??? Number of averages, with allowed values from 1 to 100 (default: `1`)

Returns:

Filter status returned by the instrument

 enable_relative(*mode=None*)

Enable relative-offset application for measurements in the active mode, or pass a mode name for another mode.

Parameters:

**mode** ??? A valid `mode` name, or None to use the active mode (default: `None`)

 *property *frequency*: Any*

Read frequency in Hz using the active `mode`.

 *property *frequency_aperature*: Any*

Set frequency aperture time in seconds, as a float strictly from 2 ms to 273 ms. See also `aperture`.

 *property *frequency_digits*: Any*

Set frequency display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *frequency_relative*: Any*

Set the frequency relative value in Hz, as a float strictly from -1 MHz to 1 MHz. See also the `relative`.

 *property *frequency_relative_enabled*: Any*

Set whether a relative offset value is applied during frequency measurement. See also the `relative_enabled`.

 *property *frequency_threshold*: Any*

Set the expected input level in Volts for frequency measurement, as a float strictly from 0.1 to 750V.

 *property *frequency_threshold_auto_enabled*: Any*

Enable or disable automatic threshold ranging for frequency measurement.

 *property *line_frequency*: Any*

Return the power line frequency detected automatically when the instrument was powered on.

 measure_capacitance(*max_capacitance=0.001*)

Set up the instrument for capacitance measurement.

Parameters:

**max_capacitance** ??? Value used to set `capacitance_range` after changing `mode` (default: `0.001`)

Returns:

None

 measure_continuity()

Set up the instrument for continuity testing.

Returns:

None

 measure_current(*max_current=0.01*, *ac=False*)

Set up current measurement using a maximum current for range selection and a boolean choice for DC versus AC.

Parameters:

-

**max_current** ??? Current value in Volts used to select the current range (default: `0.01`)

-

**ac** ??? False selects DC current, and True selects AC current (default: `False`)

 measure_diode()

Set up the instrument for diode testing.

Returns:

None

 measure_frequency()

Set up the instrument for frequency measurement.

 measure_period()

Set up the instrument for period measurement.

 measure_resistance(*max_resistance=10000000.0*, *wires=2*)

Set up resistance measurement using the maximum resistance to choose the range.

Parameters:

-

**max_resistance** (*float*) ??? Resistance in Ohms used to select the resistance range (default: `10000000.0`)

-

**wires** (*int*) ??? `2` selects normal resistance, and `4` selects 4-wires resistance (default: `2`)

Returns:

None

 measure_temperature()

Set up the instrument for temperature measurement.

 measure_voltage(*max_voltage=1*, *ac=False*)

Set up voltage measurement using a maximum voltage for range selection and a boolean choice for DC versus AC.

Parameters:

-

**max_voltage** ??? Voltage in Volts used to select the voltage range (default: `1`)

-

**ac** ??? False selects DC voltage, and True selects AC voltage (default: `False`)

 *property *mode*: Any*

Set the active measurement function. Current choices are `current` (DC) and `current ac`; voltage choices are `voltage` (DC), `voltage ac`, and `voltage ratio`; resistance choices are `resistance` (2-wire) and `resistance 4W` (4-wire). Other functions are `diode`, `capacitance`, `temperature`, `continuity`, `period`, and `frequency`.

 *property *nplc*: Any*

Set integration time for the currently active `mode` in number of power line cycles (NPLC). It controls measurement duration for the input signal. Use 0.0005 to 15 at 60Hz, or 12 at 50Hz or 400Hz.

Note

`voltage`, `current`, `resistance`, `resistance 4W`, `diode`, `temperature`, and `voltage ratio` mode are the only modes with NPLC support. If the active mode lacks NPLC, the command waits for the adapter timeout and then raises -113 "Undefined header".

 *property *period*: Any*

Read period in seconds using the active `mode`.

 *property *period_aperature*: Any*

Set period aperture time in seconds, as a float strictly from 2 ms to 273 ms. See also `aperture`

 *property *period_digits*: Any*

Set period display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *period_relative*: Any*

Set the period relative value in seconds, as a float strictly from -1 s to 1 s. See also the `relative`.

 *property *period_relative_enabled*: Any*

Set whether a relative offset value is applied during period measurement. See also the `relative_enabled`.

 *property *period_threshold*: Any*

Set the expected input level in Volts for period measurement, as a float strictly from 0.1 to 750V.

 *property *period_threshold_auto_enabled*: Any*

Enable or disable automatic threshold ranging for period measurement.

 *property *points_in_buffer*: Any*

Return the count of readings currently stored in the buffer.

 *property *pseudo_scanner_enabled*: Any*

Configure a pseudo scanner card when the instrument has no scanner card installed. Afterward, check the current scanner card with `scan_id`. If a scanner card is present, this setting has no effect.

 *property *range*: Any*

Set the positive full-scale measurement range for the currently active `mode`. Setting this property disables auto-range.

For frequency and period measurements, range selection applies to the input voltage of the signal, not to its frequency

 *property *relative*: Any*

Set the relative offset value for the currently active `mode`. When relative offset is enabled, later readings are shifted by the value configured with this command. If the instrument captures the value internally, reading this setting returns that measured value. See also the `relative_enabled`.

 *property *relative_enabled*: Any*

Set whether the relative offset value is applied to new measurements for the currently active `mode`.

 *property *resistance*: Any*

Measure resistance in Ohms for both 2-wire and 4-wire configurations using the active `mode`.

 *property *resistance_4W_digits*: Any*

Set 4-wire resistance display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *resistance_4W_nplc*: Any*

Set 4-wire resistance integration in number of power line cycles (NPLC), as a float strictly from 0.0005 to 15. See also the `nplc`.

 *property *resistance_4W_range*: Any*

Set the 4-wire resistance full-scale range in Ohms. Valid ranges are 1, 10, 100, 1e3, 10e3, 100e3, 1e6, 10e6, and 100e6. Setting this property disables auto-range. See also the `range`.

 *property *resistance_4W_relative*: Any*

Set the 4-wire resistance relative value in Ohms, as a float strictly from -100M to 100M. See also the `relative`.

 *property *resistance_4W_relative_enabled*: Any*

Set whether a relative offset value is applied during 4-wire resistance measurement. See also the `relative_enabled`.

 *property *resistance_digits*: Any*

Set 2-wire resistance display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *resistance_nplc*: Any*

Set 2-wire resistance integration in number of power line cycles (NPLC), as a float strictly from 0.0005 to 15. See also the `nplc`.

 *property *resistance_range*: Any*

Set the 2-wire resistance full-scale range in Ohms. Valid ranges are 10, 100, 1e3, 10e3, 100e3, 1e6, 10e6, and 100e6. Setting this property disables auto-range. See also the `range`.

 *property *resistance_relative*: Any*

Set the 2-wire resistance relative value in Ohms, as a float strictly from -100M to 100M. See also the `relative`.

 *property *resistance_relative_enabled*: Any*

Set whether a relative offset value is applied during 2-wire resistance measurement. See also the `relative_enabled`.

 *property *scan_card_vmax*: Any*

Return the maximum voltage across all channels.

 *property *scan_channels*: Any*

Set the channel list used for scanning. An empty string clears the list. Separate individual channels with commas, and separate the first and last channel of a range with a colon. Examples: `1`, `1,3,5`, `1:2, 7:8`, or `1:10`.

 *property *scan_channels_list

Convert the `scan_channels` string into a list of integers.

For example, `scan_channels` set to `1,3:5,7:8,10` returns `[1,3,4,5,7,8,10]`. Assigning `scan_channels_list=[1,2,3,4,6]` sets `scan_channels` to `1:4,6`.

 *property *scan_count*: Any*

Set how many times the scan repeats. Use `0` to repeat the scan until it is aborted.

 *property *scan_id*: Any*

Get scanner card’s ID.

 *property *scan_interval*: Any*

Set the interval time, from 0s to 100ks, between scan starts when `scan_count` is greater than one.

 *property *scan_iscomplete

Read bit 0 of the Event Status Register (ESR) to determine whether prior work completed. This property is used during time-consuming scanning operations.

 *property *scan_modes

Return a dictionary mapping each channel to its mode.

 scan_start(*block_communication=True*, *count=None*, *interval=None*)

Start the scanner card so it closes each channel in `scan_channels` sequentially and performs measurements.

If `scan_count` is greater than 1, another scan begins after `scan_interval` second. Scans with large counts or long intervals can take significant time. Prefer `block_communication=False`, then poll `scan_iscomplete` to determine whether measurement has finished.

Parameters:

-

**block_communication** ??? Bool controlling the communication state during scanning. Default is `True`; communication waits for commands to complete before accepting new commands (default: `True`)

-

**count** ??? Alternate way to set `scan_count` before scanning. (default: `None`)

-

**interval** ??? Alternate way to set `scan_interval` in second before scanning. (default: `None`)

Returns:

None

 scan_stop()

Stop the measurement arming and triggering sequence to abort the scanning measurement.

Returns:

None

 *property *scan_vch_end*: Any*

Return the slot's final channel that can perform voltage or 2-wire measurements.

 *property *scan_vch_start*: Any*

Return the slot's first channel capable of voltage or 2-wire measurements.

 scanned_data(*start_idx=None*, *end_idx=None*, *raw=False*)

Return scan values from the buffer as a list.

Parameters:

-

**start_idx** ??? Bool value controlling communication state during scanning. Default is `True`, meaning communication waits for command completion before new commands are accepted (default: `None`)

-

**end_idx** ??? Alternate way to set `scan_count` (default: `None`)

-

**raw** ??? Alternate way to set `scan_interval` in second (default: `False`)

Returns:

List of measured scan-channel values

Return type:

A list of channels’ list

 *property *system_time*: Any*

Set or read the instrument system time. Accepted set formats are `year, month, day, hour, minute, second` or `hour, minute, second`. Example using the `time` package to set the instrument clock: `dmm.system_time = time.strftime("%Y, %m, %d, %H, %M, %S")`

 *property *temperature*: Any*

Read temperature in Celsius using the active `mode`.

 *property *temperature_digits*: Any*

Set temperature display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *temperature_nplc*: Any*

Set temperature integration in number of power line cycles (NPLC), as a float strictly from 0.0005 to 15. See also the `nplc`.

 *property *temperature_relative*: Any*

Set the temperature relative value in Celsius, as a float strictly from -3310 C to 3310 C. See also the `relative`.

 *property *temperature_relative_enabled*: Any*

Set whether a relative offset value is applied during temperature measurement. See also the `relative_enabled`.

 *property *terminals_used*: Any*

Return which input and output terminal set the instrument is using. The value can be `FRONT` or `REAR`.

 trigger_single_autozero()

Refresh the instrument reference and zero measurements one time.

Consequent autozero measurements are disabled.

 *property *voltage*: Any*

Read DC or AC voltage in Volts using the active `mode`.

 *property *voltage_ac_bandwidth*: Any*

Set the AC voltage detector bandwidth in Hz, restricted to the integers 3, 30, and 300.

 *property *voltage_ac_digits*: Any*

Set AC voltage display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *voltage_ac_range*: Any*

Set the positive full-scale range for AC voltage in Volts. Valid ranges are 0.1, 1, 10, 100, 750. Setting this property disables auto-range. See also the `range`.

 *property *voltage_ac_relative*: Any*

Set the AC voltage relative value in Volts, as a float strictly from -750 to 750. See also the `relative`.

 *property *voltage_ac_relative_enabled*: Any*

Set whether a relative offset value is applied during AC voltage measurement. See also the `relative_enabled`.

 *property *voltage_digits*: Any*

Set DC voltage display precision, using an integer strictly from 3 to 6. See also the `digits`.

 *property *voltage_nplc*: Any*

Set DC voltage integration in number of power line cycles (NPLC), as a float strictly from 0.0005 to 15. See also the `nplc`.

 *property *voltage_range*: Any*

Set the DC voltage full-scale range in Volts. Valid ranges are 0.1, 1, 10, 100, 1000. Setting this property disables auto-range. See also the `range`.

 *property *voltage_relative*: Any*

Set the DC voltage relative value in Volts, as a float strictly from -1000 to 1000. See also the `relative`.

 *property *voltage_relative_enabled*: Any*

Set whether a relative offset value is applied during DC voltage measurement. See also the `relative_enabled`.

 *class *pymeasure.instruments.keithley.keithleyDMM6500.ScannerCard2000Channel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

 *property *autorange_enabled*: Any*

Set the autorange state for the currently active mode.

Note
