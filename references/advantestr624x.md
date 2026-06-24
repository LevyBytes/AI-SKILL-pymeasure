# Advantestr624X (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Advantest R6245/R6246 DC Voltage/Current Sources/Monitors

### Main Classes

 *class *pymeasure.instruments.advantest.advantestR624X.AdvantestR6245(*adapter*, *name='Advantest R6245 SourceMeter'*, ***kwargs*)

Bases: `AdvantestR624X`

Model class for the Advantest R6245 DC Voltage/Current Source/Monitor.

 ch_A

Channel:

`SMUChannel`

 ch_B

Channel:

`SMUChannel`

 *class *pymeasure.instruments.advantest.advantestR624X.AdvantestR6246(*adapter*, *name='Advantest R6246 SourceMeter'*, ***kwargs*)

Bases: `AdvantestR624X`

Model class for the Advantest R6246 DC Voltage/Current Source/Monitor.

 ch_A

Channel:

`SMUChannel`

 ch_B

Channel:

`SMUChannel`

 *class *pymeasure.instruments.advantest.advantestR624X.AdvantestR624X(*adapter*, *name='R624X Source meter Base Class'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

High-level interface for the Advantest R624X series SourceMeter, covering channel A and B instrument control.

Base class shared by AdvantestR6245 and AdvantestR6246 devices. Create AdvantestR6245 or AdvantestR6246 instances directly instead of instantiating this class, as in the example below:

```python
smu = AdvantestR6246("GPIB::1")
smu.reset()                                                     # Set default parameters
smu.ch_A.current_source(source_range = CurrentRange.FIXED_60mA,
                        source_value = 0,                       # Source current at 0 A
                        voltage_compliance = 10)                # Voltage compliance at 10 V
smu.ch_A.enable_source()                                        # Enables the source output
smu.ch_A.measure_voltage()
smu.ch_A.current_change_source = 5e-3                           # Change to 5mA
print(smu.read_measurement())                                   # Read and print the voltage
smu.ch_A.standby()                                              # Put channel A in standby

```

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** – String command passed to the instrument.

-

**kwargs** – Keyword arguments forwarded to the adapter.

 check_errors()

Inspect the error register and raise an exception when it reports an error.

 enable_source()

Turn on output for channel A and B (`CN`).

Note

If ‘interlock control’ on the ‘SCT’ command is ‘2’ while the clock signal is ‘HI’, the unit does not enter the operating state.

 standby()

Place channel A and B into standby mode (`CL`).

 reset()

Return the instrument to its default settings (`*RST`).

 clear_status_register()

Clear the Standard Event Status Register (SESR) plus related queues, but not output queues (`*CLS`).

 *property *srq_enabled*: Any*

Enable or disable the GPIB SRQ feature with a bool (`S0/S1`).

Type:

bool

The SRQ feature on the GPIB bus supplies hardware handshaking between the instrument and the PC's GPIB controller card. It lets data transfers to the PC be synchronized with instrument state without relying on time delay functions.

 trigger()

Use `XE` to issue the trigger signal, or to start sweep/search measurement across the A channel, B channel, and trigger link.

Note

-

If A channel and B channel are both waiting for a trigger, the trigger is applied to both.

-

If only one of channel A or B is waiting for a trigger, that waiting channel alone is triggered.

-

If A channel and B channel are both waiting for sweep start, sweep start is applied to both.

-

If only one of channel A or B is in the sweep start waiting state, start only that channel.

-

If one channel is waiting for a trigger and the other for sweep start, apply the trigger and sweep start to their respective channels.

-

With trigger link ON on the master unit, drive the *TRG signal on the trigger link bus TRUE.

-

When trigger link is ON and the unit is the master, activate the trigger link.

 stop()

Stop a sweep that was started by the XE command or by the trigger input signal (`SP`).

 set_digital_output(*values*)

Send a 16-bit signal from the rear-panel DIGITAL OUT output terminal (`DIOS`). When multiple values are supplied, output them about every 2ms and keep the last value fixed as final data.

Parameters:

**values** (*int** or **list*) – Bit values for digital out

Note

Digital data reaches the DIGITAL OUT pin only for bits selected by the DIOE command. Unselected bits become alarm output or unused bits, so no digital data is produced for them.

 *property *sweep_delay_time*: Any*

Use `GDLY` to set Ta for sweep delay, or Ta for generation/delay timing, on the master/slave channels in delayed sweep and synchronous pulse measurement operation.

Type:

float

Note

If the sweep delay time violates the required relationship (Ta<Tw and Ta<Td+Tit), an execution error is raised and the value is not set:

Tw: Pulse width Td: Major delay time Tit: Integration time

 *property *operation_mode

Query the operation mode and sweep delay time (`LDS?`).

 query_operation_mode()

Return the operation mode together with the sweep delay time.

Deprecated in version 0.16: Use `operation_mode` instead.

 *property *system_settings

Use `LDS_50?` to query system settings: output data format, common short, power frequency, and SRQ gate settings.

 query_system_settings()

Return the output data format, common short, power frequency, and SRQ gate settings.

Deprecated in version 0.16: Use `system_settings` instead.

 search_measurement_setup(*search_mode*, *occurrence_after_stop*, *command*)

Configure search measurement sense/search channel parameters (`MAR~;NENT`).

Parameters:

-

**search_mode** (int or `SearchMode`) – Search mode indicating binary/linear behavior and the sense/search channel.

-

**occurrence_after_stop** (int or `OccurrenceAfterStop`) – Output behavior used after stopping.

-

**command** (*str*) – Inner command string (e.g. `'FXV 1,20,6,17,2,0'`). Valid prefixes: FXV, FXI, PXV, PXI, WV, WI, PWV, PWI, CMD.

Note

Inside a search context, the same inner command string uses search-specific parameter meanings. Consult the instrument manual for the reinterpretation rules applied to FXV/FXI/PXV/PXI and WV/WI/PWV/PWI.

 search_comparison_setup(*search_mode*, *occurrence_after_stop*, *channel*, *comparison*, *comparison_function*, *upper_limit*, *lower_limit*)

Configure search measurement comparison calculation (`MAR~;CMD~;NENT`).

Parameters:

-

**search_mode** (int or `SearchMode`) – Search mode indicating binary/linear behavior and the sense/search channel.

-

**occurrence_after_stop** (int or `OccurrenceAfterStop`) – Output behavior used after stopping.

-

**channel** (*int*) – Channel number, 1 or 2; the instrument ignores it.

-

**comparison** (int or `ComparisonMode`) – Comparison mode selector.

-

**comparison_function** (int or `ComparisonValueType`) – Comparison value type selector.

-

**upper_limit** (*float*) – Upper comparison limit.

-

**lower_limit** (*float*) – Lower comparison limit.

Note

The instrument reports an error when the lower value exceeds the upper value.

 append_sequence_command(*command*)

Add a command to the sequence currently being recorded.

 init_sequence()

Begin redirecting `write()` calls so they build a sequence program.

 start_sequence(*repeat=1*)

Run the sequence program created with `init_sequence()`.

 end_sequence()

Finish sequence recording begun by `init_sequence()` and store the program.

 sequence_wait(*wait_mode*, *wait_value*)

Wait during sequence program execution (`WAIT`).

Parameters:

-

**wait_mode** (int or `SequenceWaitMode`) – Selects whether wait time (1) or trigger input count (2) is used.

-

**wait_value** (*float*) – Wait time or trigger input count, interpreted according to wait_mode.

This command provides these functions:

>
-

Delay execution of the following program for the requested time.

-

Delay the following program execution until the requested trigger count has arrived.

For either wait mode, wait data 0 disables waiting. When wait mode is “2”, these commands and signals are valid trigger inputs:

>
-

XE (XE 0, XE 1, XE 2)

-

*TRG

-

GET command (group execute trigger)

-

Rear-panel trigger input signal

 start_sequence_program(*start*, *stop*, *repeat*)

Run the sequence program from the start line through the stop line, with the requested repeats (`RU`).

Parameters:

-

**start** (*int*) – Program number to start from, ranging 1 to 100

-

**stop** (*int*) – Program number to stop at, ranging from 1 to 100

-

**repeat** (*int*) – Number of repetitions, from 1 to 100

 store_sequence_command(*line*, *command*)

Store a command string at a specified sequence program line (`ST`).

Parameters:

-

**line** (*int*) – Line number for the memory location

-

**command** (*str*) – Command or commands to store, separated by semicolon (;)

 interrupt_sequence(*action*)

Interrupt the sequence program running through `start_sequence_program()` (`SQSP`).

Parameters:

**action** (`SequenceInterruptionType`) – Specifies sequence interruption setup

 interrupt_sequence_command(*action*)

Interrupt the sequence program.

Deprecated in version 0.16: Use `interrupt_sequence()` instead.

 *property *sequence_program_number*: Any*

Query how many program sequences are stored in sequence memory (`LNUB?`).

Responses start with `#3XXX,line1,line2,...`; `XXX` is the 3-digit stored-program count, followed by line numbers. This property exposes only the integer count.

 query_sequence_program(*line*)

Query the command text stored at a sequence program line (`LST?`).

Parameters:

**line** (*int*) – Line number naming the memory location to read.

Returns:

Commands stored in sequence memory.

Return type:

str

 sequence_program_listing(*line*)

Return the commands stored at a sequence program line.

Deprecated in version 0.16: Use `query_sequence_program()` instead.

 store_highspeed_sequence(*program_number*, *command*)

Store commands under a high-speed sequence program number (`PGST~;END`).

Parameters:

-

**program_number** (*int*) – Program number from 1 to 20.

-

**command** (*str*) – Command string to store; commands are separated by semicolons.

Note

Do not call this method while a standard sequence is being built, meaning between `init_sequence()` and `end_sequence()`, because the standard sequence system will intercept the write.

 conditional_jump(*channel*, *condition*, *destination*)

Configure a conditional jump for a high-speed sequence program (`EXT`).

Parameters:

-

**channel** (*int*) – Selects channel 1=A, 2=B, or 3=A|B OR condition.

-

**condition** (int or `JumpCondition`) – Jump condition selector.

-

**destination** (*int*) – Destination program number for the jump (1 to 20).

Note

-

Conditions 1-4: continue to the next program when the condition is not met.

-

Conditions 7-10: remain at the current program when the condition is not met.

-

Condition 5: cancel conditional jump.

-

Condition 6: perform an unconditional jump; channel data is ignored.

-

The destination must be >= current program number to run.

 enable_highspeed_sequence(*trigger_mode*)

Permit a high-speed sequence program to start (`PGON`).

Parameters:

**trigger_mode** (int or `HighSpeedTriggerMode`) – Trigger mode used for program execution.

Trigger modes:

1.

Continuous: runs all programs sequentially after one trigger.

2.

Step: runs one program for each trigger.

3.

Execution trigger measurement: applies settings first, then waits for a trigger before each measurement.

Note

Before calling this method, store programs in program numbers 1-20 with `store_highspeed_sequence()`. Program numbers with no stored program are skipped.

 disable_highspeed_sequence()

Cancel the high-speed sequence program start/enable state set by `enable_highspeed_sequence()` (`PGOF`).

 clear_highspeed_sequence(*program_number*, *clear_mode*)

Clear one or more programs from high-speed sequence memory (`PCEL`).

Parameters:

-

**program_number** (*int*) – Program number from 1 to 20.

-

**clear_mode** (int or `ProgramClearMode`) – Clear mode selector.

Clear modes:

1.

Clear only the selected program number.

2.

Clear the selected program number plus every later program.

 trigger_output_signal(*trigger_output*, *alarm_output*, *scanner_output*)

Emit trigger, alarm, and scanner (start/stop) signals from GPIB (`OSIG`).

Parameters:

-

**trigger_output** (*int*) – Number selecting the trigger output type

-

**alarm_output** (*int*) – Number selecting the alarm output type

-

**scanner_output** (*int*) – Number selecting the scanner output type

Trigger output:

1.

Send nothing to the trigger output.

2.

Send a negative pulse to the trigger output.

Alarm output:

1.

Finish output with GO and LO.HI both at HI level. (reset)

2.

Finish output by setting GO to LO level.

3.

Drive home output LO to LO level.

4.

End output by moving HI to LO level.

Scanner - (start/stop) output:

1.

Drive the scanner scoot output to HI level. Send a negative pulse to the stop output.

2.

Set the scanner start output low.

3.

Send HI level on the scanner start output and a negative pulse on the stop output.

 set_output_format(*delimiter_format*, *block_delimiter*, *terminator*)

Configure the GPIB output data format and terminator (`FMT`).

Parameters:

-

**delimiter_format** (*int*) – Delimiter format type

-

**block_delimiter** (*int*) – Block delimiter type

-

**terminator** (*int*) – Termination character type

<EOI> (End or Identify) is output at these timings: 1,2: at the same time as LF 4: at the same time as the last output data

When binary format is selected for output data, the terminator is fixed to <EOI> only, so the terminator selection is ignored.

delimiter_format:

>
1.

ASCII format with header

2.

No header, ASCII format

3.

Binary format

block_delimiter:

>
1.

Use the same setting as the terminator.

2.

Use semicolon ;

3.

Use comma ,

terminator:

>
1.

CR, LF<EOI>

2.

LF<EOI>

3.

LF

4.

<EOI>

| 1st character header: |  |
| --- | --- |
| 1. | Normal measurement data |
| 1. | Measurement data during overrange |
| 1. | Compliance (limiter) is working. |
| 1. | Oscillation detection is working. |
| 1. | [Indicates the generated data] |
| 1. | Measurement data recorded when a search measurement error occurs |
| 1. | Measurement data is not saved in the buffer memory. |

| 2nd character header: |  |
| --- | --- |
| 1. | A-channel data for asynchronous operation (A-channel generation data) |
| 1. | B-channel data during asynchronous operation (B channel generation data) |
| 1. | A-channel data used for synchronous, sweeping, delayed sweep, and double synchronous sweep operations. |
| 1. | B-channel data used for synchronous, sweeping, delayed sweep, and double synchronous sweep operations. |

| 3rd character header: |  |
| --- | --- |
| 1. | Current generation, voltage measurement (ISVM) [Current generation] |
| 1. | Voltage generation, current measurement (VSIM) [Voltage generation] |
| 1. | Current generation, current measurement (ISIM) |
| 1. | Voltage generation, voltage measurement (VSVM) |
| 1. | Current generation with external voltage measurement (IS, EXT, VM) |
| 1. | Voltage generation, external current measurement (VS, EXT, IM) |
| 1. | Current generation with external current measurement (IS, EXT. IM) |
| 1. | Voltage generation, external voltage measurement (VS, EXT, VM) |
| 1. | Measurement data is not saved in the buffer memory. |

| 4th character header: |  |
| --- | --- |
| 1. | No operation (fixed to A) |
| 1. | Null operation result |
| 1. | Comparison operation result is GO. |
| 1. | Comparison operation result is LO. |
| 1. | Comparison operation result is HI. |
| 1. | Null operation + comparison operation result is GO. |
| 1. | Null operation + comparison operation result is LO. |
| 1. | Null operation + comparison operation result is HI. |
| 1. | Measurement data is not saved in the buffer memory. |

 *property *service_request_enable_register*: Any*

Control the service request enable register (SRER) as `SRER` `IntFlag` (`*SRE`).

Note

Serial polling does not clear bits other than the RQS bit. When `power_on_clear()` is set, the registers cleared are the status byte enable register, SESER, device operation enable register, channel operation, and the enable register; no SRQ is issued.

 *property *event_status_enable*: Any*

Control the standard event status enable register (`*ESE`).

 *property *power_on_clear*: Any*

Control the power-on clear flag (bool) (`*PSC`).

 *property *device_operation_enable_register*: Any*

Control the device operation output enable register (DOER) (`DOE?`).

 *property *digital_output_enable*: Any*

Control the digital output enable data register (`DIOE`).

 *property *digital_out_enable_data

Read or set the digital output enable data register.

Deprecated in version 0.16: Use `digital_output_enable` instead.

 *property *status_byte_register*: Any*

Read the status byte register and MSS bits without performing a serial poll (`*STB?`).

The Status Byte Register is hierarchical. Except for RQS and MAV, the ERR, DOP, ESB, and COP bits have subordinate status registers. Each status register has a corresponding enable register that determines whether it can output to the Status Byte register. The status byte register also has an enable register, which selects whether a service request SRQ is issued.

Note

`*STB?` can read bit 6 as MSS (logical OR of other bits).

 *property *event_status_register*: Any*

Read the standard event status register (SESR) as `SESR` `IntFlag` (`*ESR?`).

Note

Reading SESR clears it afterward.

 *property *device_operation_register*: Any*

Read the device operations register (DOR) as `DOR` `IntFlag` (`DOC?`).

 *property *error_register*: Any*

Read the error register contents as a 5-digit integer (`ERR?`).

The response uses `UUEEN`: `UU` gives the unit number (00=system, 01=ch A, 02=ch B) and `EEN` gives the error code. Use `check_errors()` to perform structured error checking with messages.

 *property *self_test*: Any*

Query the self-test result (`*TST?`).

Warning

This command can take a long time to finish and is not supported on every model. A VISA timeout error may occur. Consider using a try/except block or raising the adapter timeout before calling it.

 *property *trigger_link_enabled*: Any*

Enable or disable the trigger link function with a bool (`TLNK`).

Type:

bool

 *property *display_enabled*: Any*

Enable or disable the front panel display with a bool (`DISP`).

Type:

bool

 *property *line_frequency*: Any*

Configure the power supply frequency to 50 or 60 Hz (`LF`).

Type:

int

Measurement PLC integration time is one cycle at the selected power supply frequency.

 *property *store_config*: Any*

Select the memory area (0-4) where the configuration is stored (`SAV`).

Type:

int

 *property *load_config*: Any*

Select the memory area (0-4) used to load the configuration (`RCL`).

Type:

int

 set_lo_common_connection_relay(*enable*, *lo_relay=None*)

Set up the `LTL` LO common relay connection linking channels A and B.

Parameters:

-

**enable** (*bool*) – Boolean property controlling whether the connection relay is enabled. Valid values are True and False.

-

**lo_relay** (*bool**, **optional*) – Boolean setting for enabling the internal analog common relay. Use True, False, or None (don’t change lo relay setting). (default: `None`)

 parse_measurement(*measurement*)

Parse a measurement response string into a tuple containing (value, header).

 read_measurement()

Read the most recent triggered measurement value.

 *class *pymeasure.instruments.advantest.advantestR624X.SMUChannel(*parent*, *id*, *voltage_range*, *current_range*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Represent one Advantest R624X SMU channel, either A or B.

 insert_id(*command*)

Replace the placeholder in a command with the channel id.

Subclass this method to customize the behavior, for example to always prepend the channel id.

 clear_measurement_buffer()

Clear the measurement data buffer (`MBC`).

 *property *output_waveform_settings

Query this channel's output waveform settings (`LDS_0x?`).

 query_output_waveform()

Return this channel's output waveform settings.

Deprecated in version 0.16: Use `output_waveform_settings` instead.

 *property *measurement_range_settings

Use `LDS_1x?` to query range and timing details for this channel: range setting, integration interval, hold duration, delay duration, pulse width, and pulse period.

 query_measurement_settings()

Return this channel's measurement range settings.

Deprecated in version 0.16: Use `measurement_range_settings` instead.

 *property *response_settings

Query this channel's response mode, operate mode, and remote sense settings (`LDS_2x?`).

 query_response_settings()

Return this channel's response mode settings.

Deprecated in version 0.16: Use `response_settings` instead.

 *property *data_output_settings

Query this channel's null operation, comparison operation, output data type, and sweep stop condition (`LDS_3x?`).

 query_data_output_settings()

Return this channel's data output settings.

Deprecated in version 0.16: Use `data_output_settings` instead.

 *property *io_settings

Use `LDS_4x?` to query I/O settings for this channel, including analog-input state, trigger-output timing, trigger-input type, scanner control, and interlock behavior.

 query_io_settings()

Return this channel's I/O settings.

Deprecated in version 0.16: Use `io_settings` instead.

 set_output_type(*output_type*, *measurement_type*)

Configure the output method and GPIB output type (`OFM`).

Parameters:

-

**output_type** (int or `OutputType`) – Property controlling the output type

-

**measurement_type** (int or `MeasurementType`) – Property controlling the measurement type

Note

For output data formatting, see `AdvantestR624X.set_output_format()`. DC and pulse measurements always use output method ‘1’ (real-time output). If output method ‘3’ (buffering output) is specified, measured data is not stored in memory.

 *property *analog_input*: Any*

Turn the rear-panel analog input terminal (ANALOG INPUT) ON or OFF (`IAN`).

Type:

int

1.

Turn off the analog input.

2.

Analog input ON, gain x1.

3.

Analog input ON, gain x2.5.

 *property *trigger_output_timing*: Any*

Configure when the rear-panel TRIGGER OUT signal is output (`TOT`).

Type:

`TriggerOutputSignalTiming`

 set_scanner_control(*output*, *interlock*)

Configure the rear-panel SCANNER CONTROL (START, STOP) output signal and INTERLOCK input signal (`SCT`).

Parameters:

-

**output** (*int*) – Property controlling the scanner output

-

**interlock** (*int*) – Property controlling the scanner interlock type

output:

>
1.

Scanner, turn off the control signal output.

2.

Output the scanner control signal at sweep start / stop.

3.

Operate / Standby Scanner, output to the control signal.

interlock:

>
1.

Disable the interlock signal input.

2.

Use stamper behavior when the interlock signal input is HI.

3.

When the interlock signal input is HI, standby is selected; when it is LO, operation is selected.

 *property *trigger_input*: Any*

Configure the trigger input type (`TJM`).

Type:

`TriggerInputType`

| Trigger input types | 1 | 2 | 3 |
| --- | --- | --- | --- |
| *TRG | O | O | X |
| XE 0 | O | O | X |
| XE Channel | O | O | O |
| GET | O | O | X |
| Trigger input signal | O | X | X |

O is usable, X is not usable

Note

The trigger input signal cannot start sweep operation. Start it with the ‘XE’ command; after that, a trigger input signal can advance the sweep.

 *property *fast_mode_enabled*: Any*

Set this channel's response mode to fast or slow with a bool (`FL`).

Type:

bool

 *property *sample_hold_mode*: Any*

Configure the measurement integration time (`MST`).

Type:

`SampleHold`

Note

-

Only valid for pulse measurement and pulse sweep measurement.

-

In sample hold mode, AD transformation occurs immediately before the pulse width falls.

-

Sample hold mode cannot be configured during DC measurement or DC sweep measurement. In sample-and-hold mode, integration time is 100 µs. In 2-channel synchronous operation, when one channel performs pulse generation and the other uses sample-and-hold mode, the DC measurement side also runs in sample-and-hold mode.

-
