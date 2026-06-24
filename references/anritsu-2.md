# Anritsums464Xb, Anritsums9740A

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Includes: Anritsu MS464xB Vector Network Analyzer; Anritsu MS9740A Optical Spectrum Analyzer.

## Anritsu MS464xB Vector Network Analyzer

### Anritsu MS464xB Vector Network Analyzer

 *class *pymeasure.instruments.anritsu.AnritsuMS4642B(*adapter*, *name='Anritsu MS464xB Vector Network Analyzer'*, *active_channels=16*, *installed_ports=4*, *traces_per_channel=None*, ***kwargs*)

Bases: `AnritsuMS464xB`

Class for the Anritsu MS4642B Vector Network Analyzer (VNA).

This VNA belongs to the `AnritsuMS464xB` instrument family and spans 10 MHz to 20 GHz; use that base class for documentation.

 *class *pymeasure.instruments.anritsu.AnritsuMS4644B(*adapter*, *name='Anritsu MS464xB Vector Network Analyzer'*, *active_channels=16*, *installed_ports=4*, *traces_per_channel=None*, ***kwargs*)

Bases: `AnritsuMS464xB`

Class for the Anritsu MS4644B Vector Network Analyzer (VNA).

This VNA belongs to the `AnritsuMS464xB` instrument family and spans 10 MHz to 40 GHz; use that base class for documentation.

 *class *pymeasure.instruments.anritsu.AnritsuMS4645B(*adapter*, *name='Anritsu MS464xB Vector Network Analyzer'*, *active_channels=16*, *installed_ports=4*, *traces_per_channel=None*, ***kwargs*)

Bases: `AnritsuMS464xB`

Class for the Anritsu MS4645B Vector Network Analyzer (VNA).

This VNA belongs to the `AnritsuMS464xB` instrument family and spans 10 MHz to 50 GHz; use that base class for documentation.

 *class *pymeasure.instruments.anritsu.AnritsuMS4647B(*adapter*, *name='Anritsu MS464xB Vector Network Analyzer'*, *active_channels=16*, *installed_ports=4*, *traces_per_channel=None*, ***kwargs*)

Bases: `AnritsuMS464xB`

Class for the Anritsu MS4647B Vector Network Analyzer (VNA).

This VNA belongs to the `AnritsuMS464xB` instrument family and spans 10 MHz to 70 GHz; use that base class for documentation.

 *class *pymeasure.instruments.anritsu.AnritsuMS464xB(*adapter*, *name='Anritsu MS464xB Vector Network Analyzer'*, *active_channels=16*, *installed_ports=4*, *traces_per_channel=None*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the Anritsu MS464xB Vector Network Analyzer (VNA) series.

The family contains MS4642B, MS4644B, MS4645B, and MS4647B; their corresponding classes (`AnritsuMS4642B`, `AnritsuMS4644B`, `AnritsuMS4645B`, `AnritsuMS4647B`) vary only by available frequency range.

Depending on instrument configuration, the object can expose as many as 16 `MeasurementChannel` instances through the channels dict or directly as ch_ + the channel number.

Parameters:

-

**active_channels** (*int** (**1-16**) or **str** (**"auto"**)*) - sets how many channels are active (default=16); when active_channels is "auto", the instrument is queried for the active-channel count. (default: `16`)

-

**installed_ports** (*int** (**1-4**) or **str** (**"auto"**)*) - sets how many ports are installed (default=4); with "auto", the instrument is queried for the port count. (default: `4`)

-

**traces_per_channel** (*int** (**1-16**) or **str** (**"auto"**) or **None*) - sets the assumed traces per channel (between 1 and 16); when omitted, the maximum is assumed; with "auto", the instrument is queried for each channel's trace count. (default: `None`)

 *property *active_channel*: Any*

Control the active channel.

 *property *bandwidth_enhancer_enabled*: Any*

Set the IF bandwidth enhancer state.

 *property *binary_data_byte_order*: Any*

Set the byte order used for binary numeric I/O data.

valid values are:

| value | description |
| --- | --- |
| NORM | Most significant byte (MSB) comes first |
| SWAP | Least significant byte (LSB) comes first |

 check_errors()

Retrieve all instrument errors.

Returns:

`list`[`list`[`Union`[`str`, `float`]]] - list containing the error entries

 copy_data_file(*from_filename*, *to_filename*)

Copy a file stored on the VNA HDD.

Parameters:

-

**from_filename** (*str*) - complete filename including pat

-

**to_filename** (*str*) - complete filename including path

 create_directory(*dir_name*)

Make a directory on the VNA HDD.

Parameters:

**dir_name** (*str*) – directory name

 *property *data_drawing_enabled*: Any*

Set whether data drawing is enabled (True) or disabled (False).

 *property *datablock_header_format*: Any*

Set how the arbitrary block header is formed for output data.

Valid values are:

| value | description |
| --- | --- |
| 0 | Send a block header whose length is arbitrary. |
| 1 | Use an 11-character fixed-length block header. |
| 2 | Send no block header. Not IEEE 488.2 compliant. |

 *property *datablock_numeric_format*: Any*

Set the numeric I/O data representation format.

Valid values are:

| value | description |
| --- | --- |
| ASCII | ASCII floating-point notation using a 20- or 21-character number. |
| 8byte | Binary floating-point representation using 8 bytes and limited to 64 bits. |
| 4byte | Floating-point representation using 4 bytes. |

 *property *datafile_frequency_unit*: Any*

Set the frequency unit shown in a SNP data file.

Accepted values: HZ, KHZ, MHZ, GHZ.

 *property *datafile_include_heading*: Any*

Set whether data files include a heading.

 *property *datafile_parameter_format*: Any*

Set the parameter format shown in a SNP data file.

Valid values are:

| value | description |
| --- | --- |
| LINPH | Linear and Phase. |
| LOGPH | Log and Phase. |
| REIM | Real and Imaginary Numbers. |

 delete_data_file(*filename*)

Remove a file from the VNA HDD.

Parameters:

**filename** (*str*) – full filename including path

 delete_directory(*dir_name*)

Remove a directory from the VNA HDD.

Parameters:

**dir_name** (*str*) – directory name

 *property *display_layout*: Any*

Set the channel display arrangement using Row-by-Column format.

Accepted values are: R1C1, R1C2, R2C1, R1C3, R3C1, R2C2C1. Additional accepted values are R2C1C2, C2R2R1, C2R1R2, R1C4, R4C1, R2C2. The remaining accepted values are R2C3, R3C2, R2C4, R4C2, R3C3, R5C2, R2C5, R4C3, R3C4, R4C4. The number after R gives the row count, and the number after C gives the column count; for example, R2C2 creates a 2-by-2 layout. Options containing two C's or two R's create asymmetric layouts; for example, R2C1C2 creates 1 channel on the top row and two channels side-by-side on the bottom row.

 *property *event_status_enable_bits*: Any*

Set the Standard Event Status Enable Register bits.

Use `query_event_status_register()` to query the register. Valid values are between 0 and 255. See the instrument manual for the bit definitions.

 *property *external_trigger_delay*: Any*

Set the external trigger delay time in seconds.

Allowed values run from 0 [s] to 10 [s] with 1e-9 [s] steps (i.e. 1 ns).

 *property *external_trigger_edge*: Any*

Set the external trigger edge type.

Use POS for a positive/leading edge, or NEG for a negative/trailing edge.

 *property *external_trigger_handshake*: Any*

Set the external trigger handshake status.

 *property *external_trigger_type*: Any*

Set which trigger type is associated with the external trigger.

Accepted values: POIN (for point), SWE (for sweep), CHAN (for channel), and ALL.

 *property *hold_function_all_channels*: Any*

Set the hold function for all channels.

Valid values are:

| value | description |
| --- | --- |
| CONT | Run continuous sweeps on all channels |
| HOLD | Keep the sweep held on all channels |
| SING | Run one sweep, then hold all channels |

 load_data_file(*filename*)

Load a data file from the VNA HDD into VNA memory.

Parameters:

**filename** (*str*) – full filename including path

 load_data_file_to_memory(*filename*)

Load a data file into a memory trace.

Parameters:

**filename** (*str*) – full filename including path

 *property *manual_trigger_type*: Any*

Set which trigger type is associated with the manual trigger.

Accepted values: POIN (for point), SWE (for sweep), CHAN (for channel), and ALL.

 *property *max_number_of_points*: Any*

Set the maximum sweep-point count the instrument can measure.

Changing this value reboots the instrument. Valid values are 25000 and 100000. With 25000 points selected, the instrument supports 16 channels with 16 traces each; with 100000 selected, it supports 1 channel with 16 traces.

 *property *number_of_channels*: Any*

Set how many channels are displayed and therefore accessible.

In 25000 points mode, the channel count may be 1, 2, 3, 4, 6, 8, 9, 10, 12, or 16; in 100000 points mode, only 1 channel is supported. If the provided value is invalid for the current mode, the instrument selects the next higher channel number.

 *property *number_of_ports*: Any*

Return the number of instrument test ports.

 query_event_status_register()

Query the Standard Event Status Register value.

Querying this value clears the register. See the instrument manual for what the returned value means.

 read_datafile(*channel*, *sweep_points*, *datafile_freq*, *datafile_par*, *filename*)

Read a data file from the VNA.

Parameters:

-

**channel** (*int*) – Channel Index

-

**sweep_points** (*int*) - integer number of sweep points

-

**datafile_freq** (*DataFileFrequencyUnits*) – Data file frequency unit

-

**datafile_par** (*DataFileParameter*) – Data file parameter format

-

**filename** (*str*) - full path for the file to be saved

 *property *remote_trigger_type*: Any*

Set which trigger type is associated with the remote trigger.

Accepted values: POIN (for point), SWE (for sweep), CHAN (for channel), and ALL.

 return_to_local()

Put the instrument back into local operation.

 *property *service_request_enable_bits*: Any*

Set the Service Request Enable Register bits.

Valid values are between 0 and 255; setting 0 resets the register. See the instrument manual for the bit definitions.

 store_image(*filename*)

Capture a screenshot into the specified file.

Parameters:

**filename** (*str*) – full filename including path

 trigger()

Start a continuous sweep from the remote interface.

 trigger_continuous()

Start a continuous sweep from the remote interface.

 trigger_single()

Start a synchronized single sweep from the remote interface.

 *property *trigger_source*: Any*

Set the triggering source for sweeps or measurements.

Valid values are:

| value | description |
| --- | --- |
| AUTO | Automatic triggering |
| MAN | Manual triggering |
| EXTT | Use rear panel BNC triggering through the GPIB parser |
| EXT | External triggering port |
| REM | Remote triggering |

 update_channels(*number_of_channels=None*, ***kwargs*)

Create or remove channels so the channel set matches the actual channel count.

Parameters:

**number_of_channels** (*int*) - optional; when supplied, sets the desired number of channels.

 *class *pymeasure.instruments.anritsu.anritsuMS464xB.MeasurementChannel(**args*, *frequency_range=None*, *traces=None*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Represents one channel of Anritsu MS464xB VNA.

Contains 4 `Port` instances (reachable through the ports dict or directly as pt_ + the port number) and up to 16 `Trace` instances (reachable through the traces dict or directly as tr_ + the trace number).

Parameters:

-

**frequency_range** (*list** of **floats*) - specifies the number of installed ports (default=4). (default: `None`)

-

**traces** (*int** (**1-16**) or **str** (**"auto"**) or **None*) - sets the assumed trace count for the channel (between 1 and 16); if omitted, the maximum number is assumed; with "auto", the instrument is queried for the trace count. (default: `None`)

 activate()

Make the indicated channel the active channel.

 *property *active_trace*: Any*

Make the indicated channel's chosen trace active.

 *property *application_type*: Any*

Set the application type for the specified channel.

Accepted values: TRAN (for transmission/reflection), NFIG (for noise figure measurement), PULS (for PulseView).

 *property *average_count*: Any*

Set the averaging count for the indicated channel.

Requires the channel to be on. Accepted range: 1 through 1024.

 *property *average_sweep_count*: Any*

Return the averaging sweep count for the indicated channel.

 *property *average_type*: Any*

Set the averaging type for the indicated channel.

Accepted values are POIN (point-by-point) or SWE (sweep-by-sweep)

 *property *averaging_enabled*: Any*

Set whether averaging is turned on for the indicated channel.

 *property *bandwidth*: Any*

Set the IF bandwidth for the indicated channel.

Allowed range: 1 [Hz] through 1E6 [Hz] (i.e. 1 MHz). From the available options (1, 3, 10 ... 1E5, 3E5, 1E6), the system selects the nearest IF bandwidth automatically.

 *property *calibration_enabled*: Any*

Set whether RF correction (calibration) is enabled for the indicated channel.

 check_errors()

Read every instrument error and write it to the log.

Returns:

List of error entries.

 clear_average_count()

Clear the indicated channel's averaging sweep count and restart it.

 *property *cw_mode_enabled*: Any*

Set the CW sweep mode state for the indicated channel.

 *property *cw_number_of_points*: Any*

Set the indicated channel's point count for CW sweep mode.

Valid values are between 1 and 25000 or 100000, according to the maximum points setting.

 *property *display_layout*: Any*

Set the trace display arrangement for the indicated channel using Row-by-Column format.

Accepted values are: R1C1, R1C2, R2C1, R1C3, R3C1, R2C2C1. Additional accepted values are R2C1C2, C2R2R1, C2R1R2, R1C4, R4C1, R2C2. The remaining accepted values are R2C3, R3C2, R2C4, R4C2, R3C3, R5C2, R2C5, R4C3, R3C4, R4C4. The number after R gives the row count, and the number after C gives the column count; for example, R2C2 creates a 2-by-2 layout. Options containing two C's or two R's create asymmetric layouts; for example, R2C1C2 creates 1 trace on the top row and two traces side-by-side on the bottom row.

 *property *frequency_CW*: Any*

Set the indicated channel's CW frequency in hertz.

Allowed range: 1E7 [Hz] (i.e. 10 MHz) through 4E10 [Hz] (i.e. 40 GHz). (dynamic)

 *property *frequency_center*: Any*

Set the indicated channel's sweep-range center value in hertz.

Allowed range: 1E7 [Hz] (i.e. 10 MHz) through 4E10 [Hz] (i.e. 40 GHz). (dynamic)

 *property *frequency_span*: Any*

Set the indicated channel's sweep-range span value in hertz.

Allowed range: 2 [Hz] through 4E10 [Hz] (i.e. 40 GHz). (dynamic)

 *property *frequency_start*: Any*

Set the indicated channel's sweep-range start value in hertz.

Allowed range: 1E7 [Hz] (i.e. 10 MHz) through 4E10 [Hz] (i.e. 40 GHz). (dynamic)

 *property *frequency_stop*: Any*

Set the indicated channel's sweep-range stop value in hertz.

Allowed range: 1E7 [Hz] (i.e. 10 MHz) through 4E10 [Hz] (i.e. 40 GHz). (dynamic)

 *property *hold_function*: Any*

Set the hold function for the specified channel.

valid values are:

| value | description |
| --- | --- |
| CONT | Run continuous sweeps on all channels |
| HOLD | Keep the sweep held on all channels |
| SING | Run one sweep, then hold all channels |

 *property *number_of_points*: Any*

Set the measurement-point count for a frequency sweep on the indicated channel.

Valid values are between 1 and 25000 or 100000, according to the maximum points setting.

 *property *number_of_traces*: Any*

Set the trace count on the specified channel

Valid values are between 1 and 16.

 *property *sweep_mode*: Any*

Set the Spectrum Analysis sweep mode for the indicated channel.

Accepted options: VNA (a VNA-like mode; the instrument measures only at points from the frequency list) or CLAS (classical mode; the instrument scans all frequencies in the range).

 *property *sweep_time*: Any*

Set the sweep time for the indicated channel.

Valid values are between 2 and 100000.

 *property *sweep_type*: Any*

Set the sweep type for the indicated channel.

Valid options are:

| value | description |
| --- | --- |
| LIN | Frequency-based linear sweep |
| LOG | Frequency-based logarithmic sweep |
| FSEGM | Segment-based sweep using frequency-based segments |
| ISEGM | Index-based sweep using frequency-based segments |
| POW | Power-based sweep using either a CW frequency or swept-frequency |
| MFGC | Multiple frequency gain compression |

 update_frequency_range(*frequency_range*)

Refresh the values-attribute on the frequency-related dynamic properties.

Parameters:

**frequency_range** (*list*) - frequency range the instrument is capable of.

 update_traces(*number_of_traces=None*)

Create or remove traces so the trace set matches the actual trace count.

Parameters:

**number_of_traces** (*int*) - optional; when supplied, sets the desired number of traces.

 *class *pymeasure.instruments.anritsu.anritsuMS464xB.Trace(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Represents a trace inside a `MeasurementChannel` of the Anritsu MS464xB VNA.

 activate()

Make the indicated trace active.

 *property *measurement_parameter*: Any*

Set the measurement parameter for the indicated trace.

Accepted values include any 4-port S-parameter, such as S11, S12, or S41, or one item from this list:

| value | description |
| --- | --- |
| Sxx | S-parameters (1-4 for both x) |
| MIX | Response Mixed Mode |
| NFIG | Noise Figure trace response (available only with option 41 or 48) |
| NPOW | Noise Power trace response (available only with option 41 or 48) |
| NTEMP | Noise Temperature trace response (available only with option 41 or 48) |
| AGA | Noise Figure Available Gain trace response (available only with option 48) |
| IGA | Noise Figure Insertion Gain trace response (available only with option 48) |

 *class *pymeasure.instruments.anritsu.anritsuMS464xB.Port(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Represents a port inside a `MeasurementChannel` of the Anritsu MS464xB VNA.

 *property *power_level*: Any*

Set the indicated port's power level (in dBm) on the indicated channel.

## Anritsu MS9740A Optical Spectrum Analyzer

### Anritsu MS9740A Optical Spectrum Analyzer

Class constructor: pymeasure.instruments.anritsu.AnritsuMS9740A(adapter, **kwargs).
Default name: 'Anritsu MS9740A Optical Spectrum Analyzer'.

Bases: [`AnritsuMS9710C`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS9710C.html#pymeasure.instruments.anritsu.AnritsuMS9710C)

Instrument class for the Anritsu MS9740A Optical Spectrum Analyzer.

 *property *average_sweep*: Any*

Set how many averages to make on a sweep (1-1000), where 1 means one single (non-averaged) sweep

 *property *data_memory_select*: Any*

Control Memory Data Select.

 repeat_sweep(*n=20*, *delay=0.5*)

Run a single sweep and wait until it completes.

 *property *resolution*: Any*

Control Resolution (nm)

 *property *resolution_vbw*: Any*

Control Video Bandwidth Resolution

 *property *sampling_points*: Any*

Control number of sampling points
