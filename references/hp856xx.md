# Hp856Xx (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### HP 8560A / 8561B Spectrum Analyzer

Use base units for all values: time in s (Seconds), frequency in Hz (Hertz), and so on…

### Generic Specific Attributes & Methods

### General

 HP856Xx.preset()

Put the spectrum analyzer into a known preset state.

‘preset’ leaves data registers, trace registers, and stored preselector data unchanged. It also leaves the input and output data buffers uncleared;

 HP856Xx.attenuation

Set input attenuation by decade steps from 10 to 70 db (type ‘int’), or choose ‘AUTO’ or ‘MAN’(ual).

Type: `str`, `int`

```python
instr.attenuation = 'AUTO'
instr.attenuation = 60

```

 HP856Xx.amplitude_unit

Select the amplitude unit from string values ‘DBM’, ‘DBMV’, ‘DBUV’, ‘V’, ‘W’, ‘AUTO’, ‘MAN’, or from enum `AmplitudeUnits`.

Type: `str`

```python
instr.amplitude_unit = 'dBmV'
instr.amplitude_unit = AmplitudeUnits.dBmV

```

 HP856Xx.trigger_mode

Set trigger mode. A sweep starts only when the selected trigger condition is satisfied. Available values are described by `TriggerMode`. For any non-free-run trigger mode, a “T” is shown at the left edge of the display.

 HP856Xx.detector_mode

Choose the IF detector for measurement acquisition. In coupled operation the spectrum analyzer normally selects the suitable detector mode. The four detector modes are normal, positive, negative, and sample.

Type: `str`

Accepts a detector mode value, either from `DetectionModes` or one of ‘NEG’, ‘NRM’, ‘POS’, ‘SMP’.

```python
instr.detector_mode = DetectionModes.SMP
instr.detector_mode = 'NEG'

if instr.detector_mode == DetectionModes.SMP:
    pass

```

 HP856Xx.coupling

Set the spectrum analyzer input coupling. AC coupling shields the analyzer input from harmful dc signals, but it limits the lower frequency range to 100 kHz even though the analyzer can tune down to 0 Hz when signal attenuation is applied.

Type: `str`

Accepts a coupling mode value from `CouplingMode`, or the literal ‘AC’ / ‘DC’.

```python
instr.coupling = 'AC'
instr.coupling = CouplingMode.DC

if instr.coupling == CouplingMode.DC:
    pass

```

 HP856Xx.set_auto_couple()

Put center frequency step-size, sweep time, input attenuation, resolution bandwidth, and video bandwidth back into coupled mode.

These functions may be recoupled one by one or together. The spectrum analyzer selects suitable values for them. Video bandwidth and resolution bandwidth follow the coupled ratios kept in `resolution_bandwidth_to_span_ratio` and `video_bandwidth_to_resolution_bandwidth`. If ratios have not been selected, the default ratios are 1.0 and 0.011, respectively.

 HP856Xx.set_linear_scale()

Switch the spectrum analyzer display to linear amplitude scale.

Values measured on a linear scale can be reported in any unit.

 HP856Xx.logarithmic_scale

Set or query the logarithmic amplitude scale. In linear mode, querying ‘logarithmic_scale’ returns “0”. Allowed values are 0, 1, 2, 5, 10.

Type: `int`

```python
if instr.logarithmic_scale:
    pass

# set the scale to 10 db per division
instr.logarithmic_scale = 10

```

 HP856Xx.threshold

Set the lower amplitude limit and clip data at that level. The default value is -90 dBm. See also - `marker_threshold`, which leaves data below its threshold intact.

Type: `str, float` range -200 to 30

Note

In max-hold mode, raising the threshold above existing trace points permanently removes the trace data below that threshold.

 HP856Xx.set_title(*string*)

Write character data into the display title area at the upper-right corner.

A title may contain as many as two rows with sixteen characters per row. Carriage return and line feed characters are not permitted.

 HP856Xx.status

Return the decimal value for the set bits in the status byte; see the RQS and SRQ commands. STB behaves like a serial poll command. RQS and its related bits clear the same way they would after a serial poll command.

 HP856Xx.check_done()

Wait until every command entered before :meth:’check_done’ in the command string has finished. Sending `trigger_sweep()` before ‘check_done’ makes the spectrum analyzer finish a complete sweep before the program proceeds. With very long sweep times, the adapter may raise a timeout error before the spectrum analyzer finishes, depending on the timeout.

```python
instr.trigger_sweep()

# wait for a full sweep and than 'do_something'
instr.check_done()
do_something()

```

 HP856Xx.request_service(*input*)

Generate a service request for testing. This command lets a service-request handling program be exercised, but it can trigger the request only after masking is enabled with `request_service_conditions`.

Parameters:

**input** (`StatusRegister`) – Bit values used to simulate a service request

 HP856Xx.errors

Return current errors as a list of `ErrorCode` values. An empty list indicates no errors. Reading ‘errors’ clears all HP-IB errors. Query for error data immediately after checking errors for best results.

Type: `ErrorCode`

```python
errors = instr.errors
if len(errors) > 0:
    print(errors[0].code)

for error in errors:
    print(error)

if ErrorCode(112) in errors:
    print("yeah")

```

Example output produced by this python snippet:

```python
112
ErrorCode("??CMD?? - Unrecognized command")
ErrorCode("NOP NUM - Command cannot have numeric units")
yeah

```

 HP856Xx.save_state(*inp*)

Store the instrument state currently shown on the display into the specified state register.

Parameters:

-

**inp** – State selection to recall: storage slot 0 … 9, ‘LAST’, or ‘PWRON’

-

**inp** – str, int

```python
instr.preset()
instr.center_frequency = 300e6
instr.span = 20e6
instr.save_state("PWRON")

```

 HP856Xx.recall_state(*inp*)

Recall a previously saved instrument state onto the display. See `save_state()`.

Parameters:

-

**inp** – State selection to recall: storage slot 0 … 9, ‘LAST’, or ‘PWRON’

-

**inp** – str, int

```python
instr.save_state(7)
instr.preset()
instr.recall_state(7)

```

 HP856Xx.request_service_conditions

Set the bit mask that determines which service requests are allowed to interrupt a program sequence.

```python
instr.request_service_conditions = StatusRegister.ERROR_PRESENT | StatusRegister.TRIGGER

print(instr.request_service_conditions)
StatusRegister.ERROR_PRESENT|TRIGGER

```

 HP856Xx.set_maximum_hold* = <function HP856Xx.set_maximum_hold>*

 HP856Xx.set_minimum_hold* = <function HP856Xx.set_minimum_hold>*

 HP856Xx.reference_level_calibration

Set or read remote reference-level calibration. To calibrate the reference level, route the 300 MHz calibration signal to the RF input. Use center frequency 300 MHz, frequency span 20 MHz, and reference level -10 dBm. Run the RLCAL command to shift the input signal to the reference level. Calibration is correct when the signal peak is directly on the reference-level line. The resulting value can be stored in analyzer EEROM only from the front panel. Querying the RLCAL command returns the current value.

Type: `float`

```python
# connect cal signal to rf input
instr.preset()
instr.amplitude_unit = AmplitudeUnits.DBM
instr.center_frequency = 300e6
instr.span = 100e3
instr.reference_level = 0
instr.trigger_sweep()

instr.peak_search(PeakSearchMode.High)
level = instr.marker_amplitude
rlcal = instr.reference_level_calibration - int((level + 10) / 0.17)
instr.reference_level_calibration = rlcal

```

 HP856Xx.reference_offset

Apply an offset to all amplitude readouts, such as reference level and marker amplitude. The offset is measured in dB no matter which scale or units are selected. Use it to compensate for accessory gain or loss at the analyzer input. When enabled, the display shows an “R” at the left edge.

Type: `int`

 HP856Xx.reference_level

Set the reference level, or the range level while normalized mode is active. Range level behaves like reference level. The top horizontal graticule line represents the reference level. For best measurement accuracy, position the signal peak of interest on that line. Because the spectrum analyzer input attenuator is coupled to reference level, it adjusts automatically to avoid input-signal compression. See also `amplitude_unit`. Minimum reference level is -120.0 dBm or 2.2 uV.

Type: `float`

 HP856Xx.display_line

Set the horizontal display line used for visual reference or computation. The default value is 0 dBm.

Type: `float`

Accepts a value expressed in the unit of `amplitude_unit`.

```python
instr.display_line = -10

if instr.display_line == 0:
    pass

```

 HP856Xx.protect_state_enabled

Enable or disable protection against writing new data to state or trace registers. When set to ‘True’, the registers are “locked”; existing data can still be recalled, but it cannot be erased or overwritten. To unlock the registers for new storage, set ‘protect_state_enabled’ off by passing ‘False’.

Type: `bool`

 HP856Xx.mixer_level

Set the maximum signal level permitted at the input mixer. The attenuator changes automatically so this level is not exceeded for signals below the reference level. From -80 to -10 DB.

Type: `int`

 HP856Xx.frequency_counter_mode_enabled

Enable frequency counter mode for the active marker frequency, or for the frequency difference between two markers. If there is no active marker, ‘frequency_counter_mode_enabled’ creates one at the trace center and counts that marker frequency. The frequency counter improves frequency readout accuracy by stopping at the marker, counting, and then resuming the sweep. Use ‘frequency_counter_resolution’ to set the counter resolution. Use ‘marker_frequency’ to read back the counter value.

```python
instr.frequency_counter_mode_enabled = True

```

 HP856Xx.frequency_counter_resolution

Set the frequency counter resolution. See the ‘frequency_counter_mode’ command. The default value is 10 kHz.

Type `int`

>

```python
# activate frequency counter mode
instr.frequency_counter_mode = True

# adjust resolution to 1 Hz
instr.frequency_counter_resolution = 1

if instr.frequency_counter_resolution:
    pass

```

 HP856Xx.adjust_all()

Run the local oscillator (LO) and intermediate frequency (IF) alignment routines. These match the routines performed when the analyzer is switched on. Commands after ‘adjust_all’ wait until the alignment routines are complete.

 HP856Xx.adjust_if

Enable or disable automatic IF adjustment. This function is normally on. Because the IF is adjusted continuously, the IF alignment routine rarely needs to be run. When IF adjustment is inactive, an “A” appears on the left side of the display.

-

“FULL” performs IF adjustment across all IF settings.

-

“CURR” performs IF adjustment only for the IF settings currently on display.

-

False disables continuous IF adjustment.

-

True enables continuous IF adjustment again.

Type: `bool, str`

 HP856Xx.hold()

Hold the active function at its present value.

No action occurs when there is no active function.

 HP856Xx.annotation_enabled

Turn display annotation on or off.

Type: `bool`

 HP856Xx.set_crt_adjustment_pattern()

Show a CRT adjustment pattern, as in Figure 5-3. Align the display using X POSN, Y POSN, and TRACE ALIGN adjustments on the rear panel. X POSN and Y POSN move the display horizontally and vertically, respectively. TRACE ALIGN corrects tilt. Run `preset()` to clear the pattern from the screen.

 HP856Xx.display_parameters

Return a tuple containing the lower left (P1) and upper right (P2) vertices of the display window.

Type: `tuple`

```python
repr(instr.display_parameters)
(72, 16, 712, 766)

```

 HP856Xx.firmware_revision

Return the firmware revision date code for the spectrum analyzer.

Type: `datetime.date`

 HP856Xx.graticule_enabled

Turn the display graticule on or off.

Type: `bool`

```python
instr.graticule = True

if instr.graticule:
    pass

```

 HP856Xx.serial_number

Return the serial number of the spectrum analyzer.

 HP856Xx.id

Return the device identification string, including software and hardware revision, e.g. HP8560A,002, H03.

Type: `str`

```python
print(instr.id)
HP8560A,002,H02

```

 HP856Xx.elapsed_time

Return total analyzer operating time in hours. Only Hewlett-Packard can reset this value.

Type: `int`

```python
print(elapsed_time)
1998

```

### Demodulation

 HP856Xx.demodulation_mode

Set the spectrum analyzer demodulation mode to AM, FM, or off. Put a marker on the target signal, then set `demodulation_mode`; demodulation uses that signal. If no marker is present, `demodulation_mode` places one at the trace center and demodulates the frequency at that marker position. Adjust listening with the volume and squelch controls.

Type: `str`

Accepts a demodulation mode value from `DemodulationMode`, or one of ‘OFF’, ‘AM’, ‘FM’.

```python
instr.demodulation_mode = 'AC'
instr.demodulation_mode = DemodulationMode.AM

if instr.demodulation_mode == DemodulationMode.FM:
    instr.demodulation_mode = Demodulation.OFF

```

 HP856Xx.demodulation_agc_enabled

Set demodulation automatic gain control (AGC). During AM demodulation, AGC keeps speaker volume comparatively steady. It is available only for AM demodulation when the frequency span is greater than 0 Hz.

Type: `bool`

```python
instr.demodulation_agc = True

if instr.demodulation_agc:
    instr.demodulation_agc = False

```

 HP856Xx.demodulation_time

Set how long the sweep stops at the marker while demodulating a signal. The default value is 1 second. If the frequency span equals 0 Hz, demodulation continues except between sweeps. For uninterrupted demodulation, use frequency span 0 Hz with trigger mode set to single sweep (see TM). Minimum 100 ms to maximum 60 s.

Type: `float`

```python
# set the demodulation time to 1.2 seconds
instr.demodulation_time = 1.2

if instr.demodulation_time == 10:
    pass

```

 HP856Xx.squelch

Set the demodulation squelch level. When enabled, the display shows a dashed line for the squelch level. Demodulation requires an active marker above that line. See the `demodulation_mode` command. The default value is -120 dBm.

Type: `str,int`

```python
instr.preset()
instr.start_frequency = 88e6
instr.stop_frequency = 108e6

instr.peak_search(PeakSearchMode.High)
instr.demodulation_time = 10

instr.squelch = -60
instr.demodulation_mode = DemodulationMode.FM

```

### Frequency

 HP856Xx.start_frequency

Set the start frequency and put the spectrum analyzer in start-frequency/ stop-frequency mode. If start frequency is higher than stop frequency, stop frequency is raised to start frequency plus 100 Hz. Changes to start frequency also update center frequency and span.

Type: `float`

```python
instr.start_frequency = 300.5e6
if instr.start_frequency == 200e3:
    print("Correct frequency")

```

(dynamic)

 HP856Xx.stop_frequency

Set the stop frequency and put the spectrum analyzer in start-frequency/ stop-frequency mode. If stop frequency is below start frequency, start frequency is reduced to stop frequency minus 100 Hz. Changes to stop frequency also update center frequency and span.

Type: `float`

```python
instr.stop_frequency = 300.5e6
if instr.stop_frequency == 200e3:
    print("Correct frequency")

```

(dynamic)

 HP856Xx.center_frequency

Set the center frequency in hertz and switch the spectrum analyzer to center frequency / span mode.

Span stays fixed; start and stop frequencies move when center frequency changes.

Type: `float`

```python
instr.center_frequency = 300.5e6
if instr.center_frequency == 200e3:
    print("Correct frequency")

```

(dynamic)

 HP856Xx.frequency_offset

Set an offset added to displayed absolute-frequency values, including marker-frequency values.

The offset leaves the sweep frequency range unchanged and does not alter relative frequency readouts. When enabled, an “F” is shown on the left side of the display. It changes all of the following frequency measurements.

Type: `float`

```python
instr.frequency_offset = 2e6
if instr.frequency_offset == 2e6:
    print("Correct frequency")

```

(dynamic)

 HP856Xx.frequency_reference_source

Set the frequency reference source. Use the internal frequency reference (INT), or provide an external reference (EXT). The external reference must be 10 MHz (+100 Hz) with minimum amplitude 0 dBm. Connect it to J9 (10 MHz REF IN/OUT) on the rear panel. In external mode, an “X” appears at the left edge of the display.

Type: `str`

Accepts an element of `FrequencyReference`, or the literal ‘INT’ or ‘EXT’.

```python
instr.frequency_reference_source = 'INT'
instr.frequency_reference_source = FrequencyReference.EXT

if instr.frequency_reference_source == FrequencyReference.INT:
    instr.frequency_reference_source = FrequencyReference.EXT

```

 HP856Xx.span

Set the frequency span. Changing frequency span leaves the center frequency unchanged while start and stop frequencies move. A frequency span of 0 Hz effectively gives an amplitude-versus-time display mode for signal viewing, which is useful for modulation. Querying SP leaves the analyzer in center frequency /span mode.

 HP856Xx.set_full_span()

Set the spectrum analyzer to the instrument-defined full frequency span.

Full span is 2.9 GHz on the HP 8560A and 6.5 GHz on the HP 8561B.

 HP856Xx.frequency_display_enabled

Return whether the frequency-related annotations are displayed. It returns ‘False’ when none are visible and ‘True’ otherwise. This covers start and stop frequencies, center frequency, frequency span, marker readouts, center frequency step-size, and signal identification to center frequency. Query the spectrum analyzer to retrieve the frequency data.

Type: `bool`

```python
if instr.frequency_display:
    print("Frequencies get displayed")

```

### Resolution Bandwidth

 HP856Xx.resolution_bandwidth

Set resolution bandwidth. This control is normally coupled and selected from the ratio set by the RBR command. If no ratio has been chosen, the default ratio is 0.011. The bandwidth can also be selected manually over 10 Hz to 2 MHz.

Type: `str, dec`

 HP856Xx.resolution_bandwidth_to_span_ratio

Set the coupling ratio between resolution bandwidth and frequency span. When frequency span changes, resolution bandwidth changes to meet the chosen ratio. The valid ratio range is 0.002 to 0.10. Parameters “UP” and “DN” move the ratio through a 1, 2, 5 sequence. The default ratio is 0.011.

### Video

 HP856Xx.video_trigger_level

Set the video trigger level used when trigger mode is VIDEO; see the `trigger_mode` command. The display shows a dashed line at this level. The default value is 0 dBm. Range -220 to 30.

Type: `float`

 HP856Xx.video_bandwidth_to_resolution_bandwidth

Set the coupling ratio between video bandwidth and resolution bandwidth. When resolution bandwidth changes, video bandwidth changes to meet that ratio. Valid ratios run from 0.003 to 3 using a 1, 3, 10 progression. The default ratio is 1. Selecting a new ratio changes video bandwidth to satisfy it; resolution bandwidth keeps its current value.

 HP856Xx.video_bandwidth

Set video bandwidth. This control is normally coupled and chosen from the ratio set by the VBR command; if none is selected, default ratio 1.0 applies. Video bandwidth filters, or smooths, post-detected video information. Manual selection is also available over 1 Hz to 3 MHz. If requested video bandwidth falls below 300 Hz while resolution bandwidth is at least 300 Hz, the IF detector switches to sample mode. For the same total measurement time, lowering video bandwidth or increasing video averages generally smooths the trace by a similar amount. When video averages exceed 25, video bandwidth at one-third or less of resolution bandwidth is preferred. With very high averaging and video bandwidth equal to resolution bandwidth, internal math limits can produce about 0.4 dB noise overresponse on the logarithmic scale. Narrower video bandwidths make that overresponse negligible, less than 0.1 dB.

Type: `int`

 HP856Xx.video_average

Enable or configure video averaging. Video averaging smooths the displayed trace without requiring a narrow bandwidth. ‘video_average’ puts the IF detector in sample mode (see the DET command) and smooths by averaging successive traces together. The detector mode can still be changed during video averaging. This feature works only on trace A, and trace A must be in clear-write mode before ‘video_average’ can run. After ‘video_average’ runs, the analyzer screen shows the number of averaged sweeps at the top. Video averaging can reveal changes across the whole trace much faster than narrow video filters. Narrow video filters require long sweep times, which may be undesirable. Although video averaging uses more sweeps, those sweeps are faster; in some cases it can smooth a trace as quickly as a video filter.

Type: `str, int`

### FFT & Measurements

 HP856Xx.create_fft_trace_window(*trace*, *window_mode*)

Create a trace-window array for the fast Fourier transform (FFT) function.

The trace-window function builds a trace array using one of three built-in algorithms: UNIFORM, HANNING, or FLATTOP. With the FFT command, these algorithms produce passband shapes that trade off amplitude uncertainty, sensitivity, and frequency resolution. See the FFT command description for details.

Parameters:

-

**trace** (*str*) – Trace selection, either from `Trace` or ‘TRA’ for Trace A or ‘TRB’ for Trace B

-

**window_mode** (*str*) – Window selection, either from `WindowType` or ‘HANNING’, ‘FLATTOP’ or ‘UNIFORM’

 HP856Xx.get_power_bandwidth(*trace*, *percent*)

Measure total power across all signal responses in a trace array, then calculate the bandwidth corresponding to a requested percentage of that total power. For example, specifying 100% makes the power bandwidth equal the current frequency span. Specifying 50% removes trace elements from both array ends until the remaining trace elements contain half of the computed total power. The controller receives the frequency span for those remaining trace elements as the power bandwidth.

Parameters:

-

**trace** (*str*) – Trace selection, either from `Trace` or ‘TRA’ for Trace A or ‘TRB’ for Trace B

-

**percent** (*float*) – Percentage of total power, 0 … 100 %

```python
# reset spectrum analyzer
instr.preset()

# set to single sweep mode
instr.sweep_single()

instr.center_frequency = 300e6
instr.span = 1e6

instr.maximum_hold()

instr.trigger_sweep()

if instr.done:
    pbw = instr.power_bandwidth(Trace.A, 99.0)
    print("The power bandwidth at 99 percent is %f kHz" % (pbw / 1e3))

```

 HP856Xx.do_fft(*source*, *destination*, *window*)

Compute and display a discrete Fourier transform.
