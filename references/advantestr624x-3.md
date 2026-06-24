# Advantestr624X (part 3)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

*class *pymeasure.instruments.advantest.advantestR624X.SequenceInterruptionType(**values*)

Bases: `IntEnum`

1.

Release pause state only has effect while the sequence program is in pause state; otherwise, the command is ignored.

2.

Pause state is entered after the currently executing program finishes.

3.

Abort sequence program halts the sequence program after the program now running finishes. If that program is a sweep operation, the sweep is interrupted and the sequence program stops, with the output set to the bias value.

 *class *pymeasure.instruments.advantest.advantestR624X.DOR(**values*)

Bases: `IntFlag`

Device Operation Register (DOR) bit assigment:

| Bit (dec) | Description |
| --- | --- |
| 13 | Shows that the fast tokens program is currently running. |
| 12 | Error in search measurement |
| 11 | Marks completion of sequence program/high-speed sequence program execution. |
| 10 | Sequence program Pause state |
| 9 | Fan stop detection |
| 8 | Self-test error occurred (logic part) |
| 7 | Trigger wait state during trigger link master operation |
| 6 | Calibration mode status |
| 5 | Trigger link ON state |
| 4 | Trigger link bus error |
| 3 | Sequence program/high-speed sequence 1 program/add/de) waiting |
| 2 | Wait state for the sequence program wait time |
| 1 | Sequence program running |
| 0 | Synchronous operation state |

 *class *pymeasure.instruments.advantest.advantestR624X.COR(**values*)

Bases: `IntFlag`

Channel Operations Register (COR) bit assigment:

| Bit (dec) | Description |
| --- | --- |
| 14 | Comparison operation result is HI |
| 13 | Comparison operation result is GO |
| 12 | Comparison operation result is LO |
| 11 | Overheat detection |
| 10 | Overload detection |
| 9 | Oscillation detection |
| 8 | Compliance detection |
| 7 | Synchronous operation master channel |
| 6 | Measurement data output specification |
| 5 | There is measurement data |
| 4 | Self-test error occurrence (analog part) |
| 3 | Measurement data buffer full |
| 2 | Waiting for trigger |
| 1 | End of sweep |
| 0 | Operated state |

 *class *pymeasure.instruments.advantest.advantestR624X.SRER(**values*)

Bases: `IntFlag`

Service Request Enable Register (SRER) bit assigment:

| Bit (dec) | Description |
| --- | --- |
| 0 | none |
| 1 | ERR is set when any SESR flag QYE, DDE, EXE, or CME is set in the Standard Event Status Register (SESR). |
| 2 | DOP is set when an enabled bit in the device operation register becomes set. Reading the device operation register clears DOP. |
| 3 | none |
| 4 | MAV is set after output data enters the output queue. Reading the output data clears MAV. |
| 5 | ESB is set when an enabled bit in the Standard Event Status Register (SESR) is set. Reading SESR clears ESB. |
| 6 | RQS (MSS) is set when bit O through bit 5 and bit 7 are set in the Status Byte register. (this bit is read-only) |
| 7 | COP is set when an enabled bit in the Channel Operations Register becomes set. Reading the Channel Operations Register clears COP. |

 *class *pymeasure.instruments.advantest.advantestR624X.SESR(**values*)

Bases: `IntFlag`

Standard Event Status Register (SESR) bit assigment:

| Bit (dec) | Description |
| --- | --- |
| 0 | OPC (Operation Complete) not used |
| 1 | RQC unused |
| 2 | QYE (Query Error) is set if the output queue overflows, or if a read is attempted without output data. |
| 3 | DDE (Device Dependent Error) is set when the self-test reports an error. |
| 4 | EXE (Execution Error) is set when input data falls outside the internally configured range, or when the command is not executable. |
| 5 | CME (Command Error) is set for an undefined header, an invalid data format, or command syntax error. |
| 6 | URQ unused |
| 7 | PON is set after power changes from OFF to ON. |

 *class *pymeasure.instruments.advantest.advantestR624X.TriggerOutputSignalTiming(**values*)

Bases: `IntFlag`

Timing bit assigment for the trigger output signal sent from rear-panel TRIGGER OUT:

>
| Bit (dec) | Description |
| --- | --- |
| 5 | When the sweep ends |
| 4 | When the pulse width ends |
| 3 | When the pulse cycle ends |
| 2 | At the end of measurement |
| 1 | At the start of measurement |
| 0 | At the start of occurrence |

 *class *pymeasure.instruments.advantest.advantestR624X.SearchMode(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.OccurrenceAfterStop(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.HighSpeedTriggerMode(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.JumpCondition(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.ProgramClearMode(**values*)

Bases: `IntEnum`

 *class *pymeasure.instruments.advantest.advantestR624X.ComparisonMode(**values*)

Bases: `IntEnum`

Comparison mode used by search comparison setup.

 *class *pymeasure.instruments.advantest.advantestR624X.ComparisonValueType(**values*)

Bases: `IntEnum`

Value type used by search comparison setup.

 *class *pymeasure.instruments.advantest.advantestR624X.SequenceWaitMode(**values*)

Bases: `IntEnum`

WAIT sequence command wait mode.

 pymeasure.instruments.advantest.advantestR624X.seq_voltage_source(*channel*, *source_range*, *source_value*, *compliance*)

Create the command string for DV (DC voltage source).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**source_range** (int or `VoltageRange`) ? Source range for voltage.

-

**source_value** (*float*) – Source voltage value.

-

**compliance** (*float*) – Current compliance value.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_current_source(*channel*, *source_range*, *source_value*, *compliance*)

Create the command string for DI (DC current source).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**source_range** (int or `CurrentRange`) ? Source range for current.

-

**source_value** (*float*) – Source current value.

-

**compliance** (*float*) – Voltage compliance value.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_voltage_pulsed_source(*channel*, *source_range*, *pulse_value*, *base_value*, *compliance*)

Create the command string for PV (pulsed voltage source).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**source_range** (int or `VoltageRange`) ? Source range for voltage.

-

**pulse_value** (*float*) – Pulse voltage value.

-

**base_value** (*float*) – Base voltage value.

-

**compliance** (*float*) – Current compliance value.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_current_pulsed_source(*channel*, *source_range*, *pulse_value*, *base_value*, *compliance*)

Create the command string for PI (pulsed current source).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**source_range** (int or `CurrentRange`) ? Source range for current.

-

**pulse_value** (*float*) – Pulse current value.

-

**base_value** (*float*) – Base current value.

-

**compliance** (*float*) – Voltage compliance value.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_measure_voltage(*channel*, *enable=True*, *internal_measurement=True*, *voltage_range=VoltageRange.AUTO*)

Create the command string for RV (voltage measurement).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**enable** (*bool*) – Enable voltage measurement.

-

**internal_measurement** (*bool*) ? Select the internal measurement input.

-

**voltage_range** (int or `VoltageRange`) ? Measurement range for voltage. (default: `<VoltageRange.AUTO: 0>`)

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_measure_current(*channel*, *enable=True*, *internal_measurement=True*, *current_range=CurrentRange.AUTO*)

Create the command string for RI (current measurement).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**enable** (*bool*) – Enable current measurement.

-

**internal_measurement** (*bool*) ? Select the internal measurement input.

-

**current_range** (int or `CurrentRange`) ? Measurement range for current. (default: `<CurrentRange.AUTO: 0>`)

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_timing_parameters(*channel*, *hold_time*, *measurement_delay*, *pulsed_width*, *pulsed_period*)

Create the command string for WT (timing parameters).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**hold_time** (*float*) ? Hold interval, in seconds.

-

**measurement_delay** (*float*) ? Measurement delay interval, in seconds.

-

**pulsed_width** (*float*) ? Pulse width, in seconds.

-

**pulsed_period** (*float*) ? Pulse period, in seconds.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_sample_hold_mode(*channel*, *mode*)

Create the command string for MST (sample/hold mode).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**mode** (int or `SampleHold`) ? Integration time mode selection.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_comparison_limits(*channel*, *comparison*, *voltage_value*, *upper_limit*, *lower_limit*)

Create the command string for CMD (comparison limits).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**comparison** (*bool*) ? Turn comparison on or off (True=ON, False=OFF).

-

**voltage_value** (*bool*) ? Set True for voltage and False for current.

-

**upper_limit** (*float*) – Upper comparison limit.

-

**lower_limit** (*float*) – Lower comparison limit.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_enable_source(*channel*)

Create the command string for CN (enable output).

Parameters:

**channel** (*int*) ? Channel identifier (1=A, 2=B).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_standby(*channel*)

Create the command string for CL (standby/disable output).

Parameters:

**channel** (*int*) ? Channel identifier (1=A, 2=B).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_relay_mode(*channel*, *mode*)

Create the command string for OPM (relay mode).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**mode** (*int*) – Relay mode (1-4).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_fast_mode(*channel*, *fast*)

Create the command string for FL (fast/slow response).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**fast** (*bool*) ? Set True for fast response and False for slow.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_voltage_fixed_level_sweep(*channel*, *voltage_range*, *voltage_level*, *measurement_count*, *current_compliance*, *bias=0*)

Create the command string for FXV (fixed level voltage sweep).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**voltage_range** (int or `VoltageRange`) ? Source range for voltage.

-

**voltage_level** (*float*) – Voltage level value.

-

**measurement_count** (*int*) ? Count of measurements.

-

**current_compliance** (*float*) – Current compliance value.

-

**bias** (*float*) – Bias value (default 0).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_current_fixed_level_sweep(*channel*, *current_range*, *current_level*, *measurement_count*, *voltage_compliance*, *bias=0*)

Create the command string for FXI (fixed level current sweep).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**current_range** (int or `CurrentRange`) ? Source range for current.

-

**current_level** (*float*) – Current level value.

-

**measurement_count** (*int*) ? Count of measurements.

-

**voltage_compliance** (*float*) – Voltage compliance value.

-

**bias** (*float*) – Bias value (default 0).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_voltage_fixed_pulsed_sweep(*channel*, *voltage_range*, *pulse*, *base*, *measurement_count*, *current_compliance*, *bias=0*)

Create the command string for PXV (fixed pulsed voltage sweep).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**voltage_range** (int or `VoltageRange`) ? Source range for voltage.

-

**pulse** (*float*) – Pulse voltage value.

-

**base** (*float*) – Base voltage value.

-

**measurement_count** (*int*) ? Count of measurements.

-

**current_compliance** (*float*) – Current compliance value.

-

**bias** (*float*) – Bias value (default 0).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_current_fixed_pulsed_sweep(*channel*, *current_range*, *pulse*, *base*, *measurement_count*, *voltage_compliance*, *bias=0*)

Create the command string for PXI (fixed pulsed current sweep).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**current_range** (int or `CurrentRange`) ? Source range for current.

-

**pulse** (*float*) – Pulse current value.

-

**base** (*float*) – Base current value.

-

**measurement_count** (*int*) ? Count of measurements.

-

**voltage_compliance** (*float*) – Voltage compliance value.

-

**bias** (*float*) – Bias value (default 0).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_voltage_sweep(*channel*, *sweep_mode*, *repeat*, *voltage_range*, *start_value*, *stop_value*, *steps*, *current_compliance*, *bias=0*)

Create the command string for WV (staircase voltage sweep).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**sweep_mode** (int or `SweepMode`) ? Sweep mode selection.

-

**repeat** (*int*) – Number of repeats (0-1024).

-

**voltage_range** (int or `VoltageRange`) ? Source range for voltage.

-

**start_value** (*float*) – Start voltage value.

-

**stop_value** (*float*) – Stop voltage value.

-

**steps** (*int*) – Number of steps (2-2048).

-

**current_compliance** (*float*) – Current compliance value.

-

**bias** (*float*) – Bias value (default 0).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_current_sweep(*channel*, *sweep_mode*, *repeat*, *current_range*, *start_value*, *stop_value*, *steps*, *voltage_compliance*, *bias=0*)

Create the command string for WI (staircase current sweep).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**sweep_mode** (int or `SweepMode`) ? Sweep mode selection.

-

**repeat** (*int*) – Number of repeats (0-1024).

-

**current_range** (int or `CurrentRange`) ? Source range for current.

-

**start_value** (*float*) – Start current value.

-

**stop_value** (*float*) – Stop current value.

-

**steps** (*int*) – Number of steps (2-2048).

-

**voltage_compliance** (*float*) – Voltage compliance value.

-

**bias** (*float*) – Bias value (default 0).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_voltage_pulsed_sweep(*channel*, *sweep_mode*, *repeat*, *voltage_range*, *base*, *start_value*, *stop_value*, *steps*, *current_compliance*, *bias=0*)

Create the command string for PWV (pulsed voltage sweep).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**sweep_mode** (int or `SweepMode`) ? Sweep mode selection.

-

**repeat** (*int*) – Number of repeats (0-1024).

-

**voltage_range** (int or `VoltageRange`) ? Source range for voltage.

-

**base** (*float*) – Base voltage value.

-

**start_value** (*float*) – Start voltage value.

-

**stop_value** (*float*) – Stop voltage value.

-

**steps** (*int*) – Number of steps (2-2048).

-

**current_compliance** (*float*) – Current compliance value.

-

**bias** (*float*) – Bias value (default 0).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_current_pulsed_sweep(*channel*, *sweep_mode*, *repeat*, *current_range*, *base*, *start_value*, *stop_value*, *steps*, *voltage_compliance*, *bias=0*)

Create the command string for PWI (pulsed current sweep).

Parameters:

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

-

**sweep_mode** (int or `SweepMode`) ? Sweep mode selection.

-

**repeat** (*int*) – Number of repeats (0-1024).

-

**current_range** (int or `CurrentRange`) ? Source range for current.

-

**base** (*float*) – Base current value.

-

**start_value** (*float*) – Start current value.

-

**stop_value** (*float*) – Stop current value.

-

**steps** (*int*) – Number of steps (2-2048).

-

**voltage_compliance** (*float*) – Voltage compliance value.

-

**bias** (*float*) – Bias value (default 0).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_sample_mode(*mode*, *auto_sampling=True*, *channel=1*)

Create the command string for JM (sample mode).

Parameters:

-

**mode** (int or `SampleMode`) ? Sample mode selection.

-

**auto_sampling** (*bool*) ? Controls auto sampling. With True, each trigger automatically returns measurement data. With False, data is returned only after an explicit request such as `FCH?`. For dual-channel synchronous modes (`PULSED_SYNC`, `SWEEP_SYNC`, etc.), use False so the returned values are the actual measurement results.

-

**channel** (*int*) ? Channel identifier (1=A, 2=B).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_lo_common_relay(*enable*, *lo_relay=None*)

Create the command string for LTL (LO common connection relay).

Parameters:

-

**enable** (*bool*) ? Turn the connection relay on.

-

**lo_relay** (*bool** or **None*) ? Enable the internal analog common relay; None leaves it unchanged. (default: `None`)

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_digital_output(*values*)

Create the command string for DIOS (digital output).

Parameters:

**values** (*int** or **list*) ? Bit values for digital output.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_digital_output_enable(*data*)

Create the command string for DIOE (digital output enable).

Parameters:

**data** (*int*) – Digital output enable data (0-65535).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_conditional_jump(*channel*, *condition*, *destination*)

Create the command string for EXT (conditional jump).

Parameters:

-

**channel** (*int*) ? Channel selector (1=A, 2=B, 3=A|B OR).

-

**condition** (int or `JumpCondition`) ? Jump condition selector.

-

**destination** (*int*) – Jump destination program number (1-20).

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_clear_program(*program_number*, *clear_mode*)

Create the command string for PCEL (program clear).

Parameters:

-

**program_number** (*int*) – Program number (1-20).

-

**clear_mode** (int or `ProgramClearMode`) ? Clear mode selector.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_wait(*wait_mode*, *wait_value*)

Create the command string for WAIT (sequence wait).

Parameters:

-

**wait_mode** (int or `SequenceWaitMode`) ? Wait mode selection (1=wait time, 2=trigger input count).

-

**wait_value** (*float*) ? Wait duration or trigger count.

Return type:

str

 pymeasure.instruments.advantest.advantestR624X.seq_join(**commands*)

Combine multiple sequence command strings using semicolons.

Parameters:

**commands** ? One or more command strings returned by `seq_*` functions.

Return type:

str

Example:

```python
cmd = seq_join(
    seq_voltage_source(1, VoltageRange.FIXED_BEST, 5.0, 0.1),
    seq_enable_source(1),
)
inst.store_highspeed_sequence(1, cmd)

```

### General Information

The R6245/6246 Series are DC voltage/current source and monitor instruments built around source measurement units (SMUs) with 2 isolated channels. They support broad source and measurement ranges, making them suitable for DC characteristics testing across devices from discrete semiconductors, including bipolar transistors, MOSFETs, and GaAsFETs, through ICs and power devices. Higher measurement speed together with synchronized 2-channel measurement allows high-speed, timing-accurate device I/O characterization that was formerly hard to perform. Features including the trigger link function and sequence programming function can automate a series of evaluation tests, so the R6245/6246 can make evaluation work more efficient.

The command set contains 99 commands, and most of them are implemented. The device documentation is written in Japanese, with a very large option surface. This implementation follows 6245S-GPIB-B-FHJ-8335160E01.pdf, available for download from the ADCMT website.

### Examples

### Initialization of the Instrument

```python
from pymeasure.instruments.advantest import AdvantestR6246
from pymeasure.instruments.advantest.advantestR624X import *

smu = AdvantestR6246("GPIB::1")

```

### Simple dual channel synchronous measurement example

Measurement characteristics:

Channel A (MASTER) uses DC voltage source + current measurement. Channel B (SLAVE) uses Pulsed voltage source + current measurement.

Note

For dual-channel synchronous mode (`PULSED_SYNC`), set `auto_sampling=False` when calling `sample_mode()`. If `auto_sampling=True` is used (the default), the automatically output data reports the generated/source value rather than the measurement result.

Warning

`CurrentRange.AUTO` and `AUTO_*` (limited auto) ranges are invalid for pulse measurement or pulse sweep; the instrument reports error 00211. Configure pulsed modes with a fixed range such as `CurrentRange.FIXED_BEST`.

```python
smu = AdvantestR6246("GPIB::1")
smu.reset()                                               # Set default parameters

# Ch A (MASTER): DC voltage source + current measurement
smu.ch_A.voltage_source(source_range=VoltageRange.FIXED_6V,
                        source_value=5,
                        current_compliance=2)
smu.ch_A.measure_current(current_range=CurrentRange.FIXED_BEST)

# Ch B (SLAVE): Pulsed voltage source + current measurement
smu.ch_B.fast_mode_enabled = True
smu.ch_B.sample_hold_mode = SampleHold.MODE_1mS
smu.ch_B.voltage_pulsed_source(source_range=VoltageRange.FIXED_6V,
                               pulse_value=6, base_value=0,
                               current_compliance=2)
smu.ch_B.measure_current(current_range=CurrentRange.FIXED_BEST)
smu.ch_B.set_timing_parameters(hold_time=0, measurement_delay=1e-4,
                           pulsed_width=1e-2, pulsed_period=2e-2)

# PULSED_SYNC with auto_sampling=False (critical for correct readout)
smu.ch_A.set_sample_mode(SampleMode.PULSED_SYNC, auto_sampling=False)

smu.ch_A.enable_source()
smu.ch_B.enable_source()

for i in range(10):
    smu.ch_A.select_for_output()                          # Select channel A (FCH 01?)
    smu.ch_A.trigger()                                    # Trigger (XE 1, syncs both)
    Ic_a = smu.read_measurement()                         # Read channel A measurement

    smu.ch_B.select_for_output()                          # Select channel B (FCH 02?)
    Ic_b = smu.read_measurement()                         # Read channel B measurement
    print(f'Ic_a={Ic_a}, Ic_b={Ic_b}')

smu.standby()                                             # Put channel A & B in standby

```

### Program example for DC measurement

Measurement characteristics:

Function: VSIM - voltage-source/current-measure operation. Trigger voltage is 10V. Current compliance is 0.5A. Measurement delay time is 1ms. Integration time is 1 PLC. Response is Fast.

After operation starts, a trigger command repeats the measurement 10 times, and the results are printed.

```python
smu = AdvantestR6246("GPIB::1")
smu.reset()                                                      # Set default parameters
smu.ch_A.set_sample_mode(SampleMode.ASYNC, False)                     # Asynchronous operation and single shot sampling by trigger and command
smu.ch_A.voltage_source(source_range = VoltageRange.FIXED_BEST,
                        source_value = 10,
                        current_compliance = 0.5)                # compliance of 0.5A
smu.ch_A.measure_current()                                       # Measure current
smu.ch_A.set_timing_parameters(hold_time = 0,                    # 0 sec hold time
                               measurement_delay = 1E-3,         # 1ms delay between measurements
                               pulsed_width = 5E-3,              # 5ms pulse width
                               pulsed_period = 10E-3)            # 10ms pulse period
smu.ch_A.sample_hold_mode = SampleHold.MODE_1PLC                 # Sample at 1 power line cycle
smu.ch_A.fast_mode_enabled = True                                # Set channel response to fast
smu.ch_A.enable_source()                                         # Set channel in operating state
smu.ch_A.select_for_output()                                     # Select channel for measurement output

for i in range(1, 10):
    smu.ch_A.trigger()                                           # Trigger a measurement
    measurement = smu.read_measurement()
    print(f"NO {i} {measurement}")

smu.ch_A.standby()                                               # Put channel A in standby mode

```
