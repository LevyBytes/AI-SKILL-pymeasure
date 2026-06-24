# Aq6370Series, Yokogawa7651, Yokogawags200

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Includes: Yokogawa AQ6370 Series of Optical Spectrum Analyzers; Yokogawa 7651 Programmable Supply; and Yokogawa GS200 Source.

## Yokogawa AQ6370 Series of Optical Spectrum Analyzers

### Yokogawa AQ6370 Series of Optical Spectrum Analyzers

 *class *pymeasure.instruments.yokogawa.aq6370series.AQ6370Series(*adapter*, *name='Yokogawa AQ3670D OSA'*, *baud_rate=115200*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model for the Yokogawa AQ6370 Series optical spectrum analyzer.

 TRA

Channel:

`Trace`

 TRB

Channel:

`Trace`

 TRC

Channel:

`Trace`

 TRD

Channel:

`Trace`

 TRE

Channel:

`Trace`

 TRF

Channel:

`Trace`

 TRG

Channel:

`Trace`

 abort()

Halt operations, including measurements and calibration.

 *property *active_trace*: Any*

Set or read the active trace (str ‘A’, ‘B’, ‘C’, …).

 authenticate_ethernet(*username*, *password=''*)

Authenticate for an ethernet connection.

 *property *automatic_sample_number*: Any*

Set or read automatic sample number behavior (bool).

 *property *calc_result*: Any*

Return the results from the most recent analysis.

 copy_trace(*source*, *destination*)

Copy data from one specified trace into another trace.

Parameters:

-

**source** – Trace used as the source (str ‘A’, ‘B’, ‘C’, …).

-

**destination** – Trace that receives the copied data (str ‘A’, ‘B’, ‘C’, …).

 delete_trace(*trace*)

Delete the specified trace.

Parameters:

**trace** – Trace selected for deletion (str ‘ALL’, ‘A’, ‘B’, ‘C’, …).

 execute_analysis()

Run the analysis using the current analysis settings.

 get_analysis()

Request the latest analysis results; if no analysis has run, a query error is returned.

 get_xdata(*trace='TRA'*)

Measure x-axis data for the specified trace and return wavelength in m.

Parameters:

**trace** – Trace selected for measurement (str ‘A’, ‘B’, ‘C’, …). (default: `'TRA'`)

Returns:

X-axis data from the specified trace.

 get_ydata(*trace='TRA'*)

Measure y-axis data for the specified trace and return power in dBm.

Parameters:

**trace** – Trace selected for measurement (str ‘A’, ‘B’, ‘C’, …). (default: `'TRA'`)

Returns:

Y-axis data from the specified trace.

 initiate_sweep()

Initiate a sweep.

 *property *level_position*: Any*

Set or read the reference level position in divisions (int, less than the total division count, which is either 8, 10 or 12).(dynamic)

 *property *reference_level*: Any*

Set or read the main level-axis scale reference level (float in dBm).

 *property *resolution_bandwidth*: Any*

Set or read measurement resolution, as a float in m. Allowed discrete values are [0.02e-9, 0.05e-9, 0.1e-9, 0.2e-9, 0.5e-9, 1e-9, 2e-9] m.(dynamic)

 *property *sample_number*: Any*

Set or read the sample number (int from 51 to 50001).

 *property *sensitivity*: Any*

Set or read sweep sensitivity (str ‘NHLD’, ‘NAUT’, ‘NORM’, ‘MID’, ‘HIGH1’, ‘HIGH2’, ‘HIGH3’)

 set_level_position_to_max()

Move the reference level position to its maximum value.

 *property *sweep_complete*: Any*

Return sweep completion status (bool, True if complete).

 *property *sweep_mode*: Any*

Set or read sweep mode (str ‘SINGLE’, ‘REPEAT’, ‘AUTO’, ‘SEGMENT’).

 *property *sweep_time_interval*: Any*

Set or read the sweep time interval (int from 0 to 99999 s).

 *property *transfer_format*: Any*

Set or read the data transfer format; reset restores default ASCII.

 trigger()

Run one sweep using the previous conditions.

 wait_for_sweep_complete(*should_stop=<function AQ6370Series.<lambda>>*, *timeout=3600*, *delay=0*)

Block program execution while waiting until the sweep completes.

Parameters:

-

**should_stop** – Function returning True when waiting should stop. (default: `<function AQ6370Series.<lambda> at 0x7aa57c817270>`)

-

**timeout** – Maximum wait time in seconds. (default: `3600`)

-

**delay** – Seconds to pause between sweep-completion checks. (default: `0`)

Returns:

True means the sweep completed; False means should_stop ended the wait.

Raises:

**TimeoutError** – Raised when the sweep is not complete before the timeout period ends.

 *property *wavelength_automatic_center*: Any*

Set or read whether the wavelength center tracks the maximum (bool).

 *property *wavelength_center*: Any*

Set or read the measurement condition center wavelength (float in m).(dynamic)

 *property *wavelength_span*: Any*

Set or read wavelength span (float from 0 to 1100e-9 m).(dynamic)

 *property *wavelength_start*: Any*

Set or read the wavelength where the measurement begins (float from 50e-9 to 2250e-9 in m).(dynamic)

 *property *wavelength_stop*: Any*

Set or read the wavelength where the measurement ends (float from 50e-9 to 2250e-9 in m).(dynamic)

 *class *pymeasure.instruments.yokogawa.aq6370series.AQ6370E(*adapter*, *name='Yokogawa AQ3670D OSA'*, *baud_rate=115200*, ***kwargs*)

Bases: `AQ6370Series`

Represents Yokogawa AQ6370E optical spectrum analyzer.

 TRA

Channel:

`Trace`

 TRB

Channel:

`Trace`

 TRC

Channel:

`Trace`

 TRD

Channel:

`Trace`

 TRE

Channel:

`Trace`

 TRF

Channel:

`Trace`

 TRG

Channel:

`Trace`

 *property *sensitivity_level*: Any*

Set or read sweep sensitivity from a requested measurement level in dBm; the nearest sensitivity and sweep speed are selected automatically.

 *property *sweep_speed*: Any*

Set or read sweep speed (str ‘1x’ or ‘2x’ for double speed).

 *class *pymeasure.instruments.yokogawa.aq6370series.AQ6370D(*adapter*, *name='Yokogawa AQ3670D OSA'*, *baud_rate=115200*, ***kwargs*)

Bases: `AQ6370Series`

Represents Yokogawa AQ6370D optical spectrum analyzer.

 TRA

Channel:

`Trace`

 TRB

Channel:

`Trace`

 TRC

Channel:

`Trace`

 TRD

Channel:

`Trace`

 TRE

Channel:

`Trace`

 TRF

Channel:

`Trace`

 TRG

Channel:

`Trace`

 *property *sweep_speed*: Any*

Set or read sweep speed (str ‘1x’ or ‘2x’ for double speed).

 *class *pymeasure.instruments.yokogawa.aq6370series.AQ6370C(*adapter*, *name='Yokogawa AQ3670D OSA'*, *baud_rate=115200*, ***kwargs*)

Bases: `AQ6370Series`

Represents Yokogawa AQ6370C optical spectrum analyzer.

 TRA

Channel:

`Trace`

 TRB

Channel:

`Trace`

 TRC

Channel:

`Trace`

 TRD

Channel:

`Trace`

 TRE

Channel:

`Trace`

 TRF

Channel:

`Trace`

 TRG

Channel:

`Trace`

 *property *sweep_speed*: Any*

Set or read sweep speed (str ‘1x’ or ‘2x’ for double speed).

 *class *pymeasure.instruments.yokogawa.aq6370series.AQ6373(*adapter*, *name='Yokogawa AQ3670D OSA'*, *baud_rate=115200*, ***kwargs*)

Bases: `AQ6370Series`

Represents Yokogawa AQ6373 optical spectrum analyzer.

 TRA

Channel:

`Trace`

 TRB

Channel:

`Trace`

 TRC

Channel:

`Trace`

 TRD

Channel:

`Trace`

 TRE

Channel:

`Trace`

 TRF

Channel:

`Trace`

 TRG

Channel:

`Trace`

 *class *pymeasure.instruments.yokogawa.aq6370series.AQ6373B(*adapter*, *name='Yokogawa AQ3670D OSA'*, *baud_rate=115200*, ***kwargs*)

Bases: `AQ6373`

Represents Yokogawa AQ6373B variant optical spectrum analyzer.

 TRA

Channel:

`Trace`

 TRB

Channel:

`Trace`

 TRC

Channel:

`Trace`

 TRD

Channel:

`Trace`

 TRE

Channel:

`Trace`

 TRF

Channel:

`Trace`

 TRG

Channel:

`Trace`

 *property *sweep_speed*: Any*

Set or read sweep speed (str ‘1x’ or ‘2x’ for double speed).

 *class *pymeasure.instruments.yokogawa.aq6370series.AQ6375(*adapter*, *name='Yokogawa AQ3670D OSA'*, *baud_rate=115200*, ***kwargs*)

Bases: `AQ6370Series`

Represents Yokogawa AQ6375 optical spectrum analyzer.

 TRA

Channel:

`Trace`

 TRB

Channel:

`Trace`

 TRC

Channel:

`Trace`

 TRD

Channel:

`Trace`

 TRE

Channel:

`Trace`

 TRF

Channel:

`Trace`

 TRG

Channel:

`Trace`

 *class *pymeasure.instruments.yokogawa.aq6370series.AQ6375B(*adapter*, *name='Yokogawa AQ3670D OSA'*, *baud_rate=115200*, ***kwargs*)

Bases: `AQ6375`

Represents Yokogawa AQ6375B variant optical spectrum analyzer.

 TRA

Channel:

`Trace`

 TRB

Channel:

`Trace`

 TRC

Channel:

`Trace`

 TRD

Channel:

`Trace`

 TRE

Channel:

`Trace`

 TRF

Channel:

`Trace`

 TRG

Channel:

`Trace`

 *property *sweep_speed*: Any*

Set or read sweep speed (str ‘1x’ or ‘2x’ for double speed).

## Yokogawa 7651 Programmable Supply

### Yokogawa 7651 Programmable Supply

 *class *pymeasure.instruments.yokogawa.Yokogawa7651(*adapter*, *name='Yokogawa 7651 Programmable DC Source'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Instrument model for the Yokogawa 7651 Programmable DC Source, with a high-level interface for interacting with the instrument.

```python
yoko = Yokogawa7651("GPIB::1")

yoko.apply_current()                # Sets up to source current
yoko.source_current_range = 10e-3   # Sets the current range to 10 mA
yoko.compliance_voltage = 10        # Sets the compliance voltage to 10 V
yoko.source_current = 0             # Sets the source current to 0 mA

yoko.enable_source()                # Enables the current output
yoko.ramp_to_current(5e-3)          # Ramps the current to 5 mA

yoko.shutdown()                     # Ramps the current to 0 mA and disables output

```

 apply_current(*max_current=0.001*, *compliance_voltage=1*)

Configure the instrument for source current, with optional parameters that fall back to the `source_current_range` and `compliance_voltage` properties.

 apply_voltage(*max_voltage=1*, *compliance_current=0.01*)

Configure the instrument for source voltage, with optional parameters that fall back to the `source_voltage_range` and `compliance_current` properties.

 *property *compliance_current*: Any*

Set or read compliance current in Amps, with allowed values from 5 to 120 mA.

 *property *compliance_voltage*: Any*

Set or read compliance voltage in Volts, with allowed values between 1 and 30 V.

 disable_source()

Disable current or voltage sourcing according to the instrument configuration.

 enable_source()

Enable current or voltage sourcing according to the instrument configuration.

 *property *id

Return the instrument identification.

 ramp_to_current(*current*, *steps=25*, *duration=0.5*)

Ramp current to a value in Amps by moving through linearly spaced current steps over a duration in seconds.

Parameters:

-

**steps** – Number of linear steps to traverse (default: `25`)

-

**duration** – Ramp time in seconds (default: `0.5`)

 ramp_to_voltage(*voltage*, *steps=25*, *duration=0.5*)

Ramp voltage to a value in Volts by moving through linearly spaced voltage steps over a duration in seconds.

Parameters:

-

**steps** – Number of linear steps to traverse (default: `25`)

-

**duration** – Ramp time in seconds (default: `0.5`)

 shutdown()

Shut down the instrument by ramping current or voltage to zero before disabling the source.

 *property *source_current*: Any*

Set or read source current in Amps when that mode is active. (float)

 *property *source_current_range*: Any*

Set or read the current range in Amps. Valid values are 1 mA, 10 mA, and 100 mA. If needed, currents are truncated to an appropriate value.

 *property *source_enabled

Return True when the source is enabled, based on whether the 5th bit of the OC flag is binary 1.

 *property *source_mode*: Any*

Set or read source mode, using either ‘current’ or ‘voltage’. You may also use the convenience methods `apply_current()` and `apply_voltage()`.

 *property *source_voltage*: Any*

Set or read source voltage in Volts when that mode is active. (float)

 *property *source_voltage_range*: Any*

Set or read source voltage range in Volts. Valid values are 10 mV, 100 mV, 1 V, 10 V, and 30 V. If needed, voltages are truncated to an appropriate value.

## Yokogawa GS200 Source

### Yokogawa GS200 Source

 *class *pymeasure.instruments.yokogawa.YokogawaGS200(*adapter*, *name='Yokogawa GS200 Source'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Instrument model for the Yokogawa GS200 source, with a high-level interface for interacting with the instrument.

 *property *current_limit*: Any*

Set or read the current limit. “Limit” means the maximum value of the electrical value conjugate to the mode (current is conjugate to voltage, and vice versa), so current limit applies only in ‘voltage’ mode.

 *property *source_enabled*: Any*

Set or read whether the source is enabled. (bool)

 *property *source_level

Set or read the output level, as either voltage or current according to the source mode. (float)

 *property *source_mode*: Any*

Set or read source mode. Allowed modes are ‘current’ and ‘voltage’.

 *property *source_range*: Any*

Set or read the output range, in voltage or current. “Range” means the maximum source level. (float)

 trigger_ramp_to_level(*level*, *ramp_time*)

Start a ramp from the current output level to “level” over “ramp_time”. This method does NOT wait for the ramp to finish, so later code evaluation is not blocked.

Parameters:

-

**level** (*float*) – final output level

-

**ramp_time** (*float*) – ramp duration in seconds

Returns:

None

 *property *voltage_limit*: Any*

Set or read the voltage limit. “Limit” means the maximum value of the electrical value conjugate to the mode (current is conjugate to voltage, and vice versa), so voltage limit applies only in ‘current’ mode.
