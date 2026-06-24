# Agilent4284A, Agilentn8975A, Agilente4408B

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

This reference covers three instruments: Agilent 4284A LCR Meter, Agilent N8975A Noise Figure Analyzer, and Agilent E4408B Spectrum Analyzer.

## Agilent 4284A LCR Meter

### Agilent 4284A LCR Meter

 *class *pymeasure.instruments.agilent.Agilent4284A(*adapter*, *name='Agilent 4284A LCR meter'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent 4284A precision LCR meter.

```python
agilent = Agilent4284A("GPIB::1::INSTR")

agilent.reset()                         # Return instrument settings to default
                                          values
agilent.frequency = 10e3                # Set frequency to 10 kHz
agilent.voltage = 0.02                  # Set AC voltage to 20 mV
agilent.mode = 'ZTR'                    # Set impedance mode to measure
                                          impedance magnitude [Ohm] and phase
                                          [rad]
agilent.sweep_measurement(
    'frequency', [1e4, 1e3, 100]        # Perform frequency sweep measurement
)                                       # at 10 kHz, 1 kHz, and 100 Hz
agilent.enable_high_power()             # Enable upper current, voltage, and
                                          bias limits, if properly configured.

agilent.correction.open_enabled = True     # Enable the OPEN correction
agilent.correction.spot1.enabled = True    # Enable the correction for SPOT1
agilent.correction.spot1.frequency = 10e3  # Set SPOT1 frequency to 10 kHz
agilent.correction.spot1.measure_open()    # Measure the OPEN structure for SPOT1

```

 correction

Channel:

`Agilent4284ACorrection`

 *property *ac_current*: Any*

Sets the AC current level in Amps. In default operation, allowed values span 50 uA to 20 mA; high-power mode permits 50 uA to 200 mA.(dynamic)

 *property *ac_voltage*: Any*

Sets the AC voltage level in Volts. Default values run from 5 mV to 2 V; high-power mode allows 5 mV to 20 V.(dynamic)

 *property *auto_range_enabled*: Any*

Enables or disables impedance auto range.

 *property *bias_current*: Any*

Sets DC bias current in Amps. Option 001 (power amplifier / DC bias) must be installed. Maximum is 100 mA.(dynamic)

 *property *bias_enabled*: Any*

Enables or disables DC bias.

 *property *bias_voltage*: Any*

Sets DC bias voltage in Volts. Maximum is 2 V by default and 40 V in high-power mode.(dynamic)

 *property *frequency*: Any*

Sets AC frequency in Hertz over 20 Hz to 1 MHz.(dynamic)

 *property *high_power_enabled

Enables or disables high power mode. Enabling it requires option 001 (power amplifier / DC bias) to be installed.

 *property *impedance_mode*: Any*

Control impedance measurement function.

-

CPD: Parallel capacitance [F] paired with dissipation factor [number]

-

CPQ: Parallel capacitance [F] paired with quality factor [number]

-

CPG: Parallel capacitance [F] paired with parallel conductance [S]

-

CPRP: Parallel capacitance [F] paired with parallel resistance [Ohm]

-

CSD: Series capacitance [F] paired with dissipation factor [number]

-

CSQ: Series capacitance [F] paired with quality factor [number]

-

CSRS: Series capacitance [F] paired with series resistance [Ohm]

-

LPQ: Parallel inductance [H] paired with quality factor [number]

-

LPD: Parallel inductance [H] paired with dissipation factor [number]

-

LPG: Parallel inductance [H] paired with parallel conductance [S]

-

LPRP: Parallel inductance [H] paired with parallel resistance [Ohm]

-

LSD: Series inductance [H] paired with dissipation factor [number]

-

LSQ: Seriesinductance [H] paired with quality factor [number]

-

LSRS: Series inductance [H] paired with series resistance [Ohm]

-

RX: Resistance [Ohm] paired with reactance [Ohm]

-

ZTD: Impedance magnitude [Ohm] paired with phase [deg]

-

ZTR: Impedance magnitude [Ohm] paired with phase [rad]

-

GB: Conductance [S] paired with susceptance [S]

-

YTD: Admittance magnitude [Ohm] paired with phase [deg]

-

YTR: Admittance magnitude [Ohm] paired with phase [rad]

 *property *impedance_range*: Any*

Sets the impedance measurement range. For the supplied setting value, the 4284A chooses a suitable measurement range.

 sweep_measurement(*sweep_mode*, *sweep_values*)

Performs list sweep measurement with a sequential trigger.

Parameters:

-

**sweep_mode** (*str*) - parameter selected for sweeping. Valid choices are frequency, voltage, current, bias_voltage, and bias_current.

-

**sweep_values** - list containing the parameter values used for the sweep.

Returns:

values configured with `impedance_mode`, together with sweep parameters formatted as ([val A], [val B], [sweep_values])

 trigger()

Issues a bus trigger no matter what the trigger state is. Usable when `trigger_source` is BUS. Returns the triggered measurement result.

 *property *trigger_continuous_enabled*: Any*

Controls whether, after a measurement, trigger state automatically returns to WAIT FOR TRIGGER.

 *property *trigger_delay*: Any*

Sets trigger delay in seconds. Allowed values run from 0 to 60, with 1 ms resolution.

 trigger_immediate()

Issues a bus trigger no matter what the trigger state is. Usable when `trigger_source` is BUS. Retrieve the measurement result with the FETCH? command.

 trigger_initiate()

Moves trigger state from IDLE into WAIT FOR TRIGGER for a single trigger sequence.

 *property *trigger_source*: Any*

Chooses trigger mode; valid options are INT, EXT, BUS, or HOLD.

 *class *pymeasure.instruments.agilent.agilent4284A.Agilent4284ACorrection(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for the correction functions.

 *property *cable_length*: Any*

Sets the cable-length correction value in meters, (int strictly 0, 1, 2 or 4).

 *property *load_enabled*: Any*

Control the LOAD correction (bool).

 *property *load_function*: Any*

Control the spot LOAD standard.

Type:

str, limited strictly to `CPD`, `CPQ`, `CPG`, `CPRP`, `CSD`, `CSQ`, `CSRS`, `LPQ`, `LPD`, `LPG`, `LPRP`, `LSD`, `LSQ`, `LSRS`, `RX`, `ZTD`, `ZTR`, `GB`, `YTD`, `YTR`

For details, see `Agilent4284A.impedance_mode`.

 measure_load()

Measure the LOAD correction standard.

 measure_open()

Measure the OPEN correction standard.

 measure_short()

Measure the SHORT correction standard.

 *property *open_enabled*: Any*

Control the OPEN correction (bool).

 *property *short_enabled*: Any*

Control the SHORT correction (bool).

 *class *pymeasure.instruments.agilent.agilent4284A.Agilent4284ASpot(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for the spot correction functions.

 *property *enabled*: Any*

Control this spot correction (bool).

 *property *frequency*: Any*

Sets this spot's frequency in Hz.

 *property *load_function*: Any*

Sets this spot's LOAD standard.

Type:

str, limited strictly to `CPD`, `CPQ`, `CPG`, `CPRP`, `CSD`, `CSQ`, `CSRS`, `LPQ`, `LPD`, `LPG`, `LPRP`, `LSD`, `LSQ`, `LSRS`, `RX`, `ZTD`, `ZTR`, `GB`, `YTD`, `YTR`

For details, see `Agilent4284A.impedance_mode`.

 measure_load()

Measures this spot's LOAD correction standard.

 measure_open()

Measures this spot's OPEN correction standard.

 measure_short()

Measures this spot's SHORT correction standard.

## Agilent N8975A Noise Figure Analyzer

### Agilent N8975A Noise Figure Analyzer

 *class *pymeasure.instruments.agilent.AgilentN8975A(*adapter*, *name='Agilent N8975A'*, *timeout=5000*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the Agilent N8975A Noise Figure Analyzer.

```python
nfa = AgilentN8975A("GPIB0::16::INSTR")
nfa.adapter.connection.timeout = 30000  # set a new timeout to 30 sec
nfa.abort()  # abort all running measurements
nfa.single()  # perform a single sweep measurement
nfa.complete
noise_figure = nfa.noise_figure_db  # get the noise figure data
gain = nfa.gain_db  # get the gain data

```

 frequency

Channel:

`AgilentN8975AFrequency`

 abort()

Stop any current measurement.

 *property *average*: Any*

Sets averaging sample count (int, strictly from `1` to `999`).

 *property *average_enabled*: Any*

Enables or disables averaging (bool).

 *property *bandwidth*: Any*

Sets measurement bandwidth in Hz (float, strictly `100e3`, `200e3`, `400e3`, `1e6`, `2e6` or `4e6`).

 calibrate()

Initiate a user calibration.

 *property *continuous_mode_enabled*: Any*

Enables or disables continuous sweep mode (bool).

 *property *gain

Retrieves corrected gain data in dB (list of float).

 initiate()

Trigger a measurement.

 *property *noise_figure

Retrieves corrected noise figure data in dB (list of float).

 single()

Perform a single sweep.

 *class *pymeasure.instruments.agilent.agilentN8975A.AgilentN8975AFrequency(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for the Noise Figure Analyzer frequency subsystem.

 *property *fixed_value*: Any*

Sets frequency in Hz for fixed frequency `mode` (float, strictly from `10e6` to `26.5e9`).

 *property *list_data*: Any*

Sets frequencies in Hz for list frequency `mode` (list of float).

 *property *mode*: Any*

Sets how measurement frequencies are generated (str, strictly `sweep`, `fixed` or `list`).

-

`sweep`: frequency values come from the `start`, `stop` and `number_of_points` parameters

-

`fixed`: uses the `fixed_value` frequency

-

`list`: takes frequencies from `list_data`

 *property *number_of_entries*: Any*

Retrieves the entry count for list frequency `mode` (int).

 *property *number_of_points*: Any*

Sets point count for sweep frequency `mode` (int, strictly from `2` to `401`).

 *property *start_frequency*: Any*

Sets start frequency in Hz for sweep frequency `mode` (float, strictly from `10e6` to `26.4999e9`).

 *property *stop_frequency*: Any*

Sets stop frequency in Hz for sweep frequency `mode` (float, strictly from `10.1e6` to `26.5e9`).

## Agilent E4408B Spectrum Analyzer

### Agilent E4408B Spectrum Analyzer

 *class *pymeasure.instruments.agilent.AgilentE4408B(*adapter*, *name='Agilent E4408B Spectrum Analyzer'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the AgilentE4408B Spectrum Analyzer and exposes high-level scan operations for high-frequency spectrums.

 *property *center_frequency*: Any*

Sets center frequency in Hz (float).

 *property *frequencies

Returns a numpy array of frequencies in Hz for the current settings.

 *property *frequency_points*: Any*

Sets the frequency-point count in the sweep (int, truncated from 101 to 8192).

 *property *frequency_step*: Any*

Sets frequency step in Hz (float).

 *property *start_frequency*: Any*

Sets start frequency in Hz (float).

 *property *stop_frequency*: Any*

Sets stop frequency in Hz (float).

 *property *sweep_time*: Any*

Sets sweep time in seconds (float).

 trace(*number=1*)

Returns a numpy array containing data for a selected trace.

Parameters:

**number** (`int`) - Trace number (1, 2, or 3). (default: `1`)

 trace_df(*number=1*)

Returns a pandas DataFrame with frequency and peak data for a selected trace.
