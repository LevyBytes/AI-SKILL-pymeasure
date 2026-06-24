# Keysightdsox1102G, Keysightpna

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Keysight DSOX1102G Oscilloscope; Keysight PNA Vector Network Analyzers.

## Keysight DSOX1102G Oscilloscope

### Keysight DSOX1102G Oscilloscope

 *class *pymeasure.instruments.keysight.KeysightDSOX1102G(*adapter*, *name='Keysight DSOX1102G Oscilloscope'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Interface for the Keysight DSOX1102G Oscilloscope used to communicate with and control the instrument.

For direct scope control through the lower-level methods, consult the Keysight DSOX1102G Oscilloscope Programmer’s Guide.

```python
scope = KeysightDSOX1102G(resource)
scope.autoscale()
ch1_data_array, ch1_preamble = scope.download_data(source="channel1", points=2000)
# ...
scope.shutdown()

```

Known issues:

-

Completion reporting can occur before digitize itself has finished. Commands sent immediately after digitize may produce VI_ERROR_TMO (timeout). Current fix: when necessary, wait between digitize and the next command sent to the scope.

 *property *acquisition_mode*: Any*

String parameter choosing acquisition mode; valid values are “realtime” or “segmented”.

 *property *acquisition_type*: Any*

String parameter selecting acquisition type; accepted values are “normal”, “average”, “hresolution”, or “peak”.

 autoscale()

Autoscale displayed channels.

 clear_status()

Clear device status.

 default_setup()

Default setup; some user settings, such as preferences, are left as they were.

 digitize(*source*)

Acquire waveforms using the settings configured by the :ACQuire commands. Keep a delay after digitize before issuing more commands, because timeout can occur before digitize finishes. :type source: `str` :param source: “channel1”, “channel2”, “function”, “math”, “fft”, “abus”, or “ext”.

 download_data(*source*, *points=62500*)

Return oscilloscope data for the selected source. The result contains a np.ndarray of data values without a temporal axis, plus a dict waveform preamble that can be used to construct the matching time values for each data point.

For a valid acquisition, the multimeter is stopped.

Parameters:

-

**source** – measurement source; allowed values are “channel1”, “channel2”, “function”, “fft”, “wmemory1”, “wmemory2”, or “ext”.

-

**points** – integer count of points to acquire. The oscilloscope can return fewer points than requested; that behavior is not a library problem. Valid values are 100, 250, 500, and 1000; larger choices are 2000, 5000, 10000, 20000, 50000, or 62500. (default: `62500`)

Return data_ndarray, waveform_preamble_dict:

For the dict layout, see the waveform_preamble property.

 download_image(*format_='png'*, *color_palette='color'*)

Return an oscilloscope screen image as a bytearray in the requested file format.

Parameters:

-

**format** – “bmp”, “bmp8bit”, or “png”

-

**color_palette** – “color” or “grayscale” (default: `'color'`)

 factory_reset()

Factory default setup; no user settings are kept unchanged.

 run()

Starts repetitive acquisitions.

Equivalent to pressing the Run key on the front panel.

 single()

Makes the instrument capture one trigger of data; equivalent to pressing the Single key on the front panel.

 stop()

Halts acquisition; equivalent to pressing the Stop key on the front panel.

 *property *system_setup

String parameter for configuring the oscilloscope. It must use IEEE 488.2 format. Recommended use is to set only a string that this command previously returned.

 *property *timebase

Read the timebase setup as a dict with these keys: - “REF”: screen position of the timebase reference (str) - “MAIN:RANG”: full-scale timebase range (float) - “POS”: interval from trigger to reference point (float) - “MODE”: mode (str)

 *property *timebase_mode*: Any*

String parameter selecting the current time base; valid values are “main”, “window”, “xy”, or “roll”.

 *property *timebase_offset*: Any*

Float parameter setting the seconds between the trigger event and the reference position, which is at the center of screen by default.

 *property *timebase_range*: Any*

Float parameter setting the main window full-scale horizontal time in seconds.

 *property *timebase_scale*: Any*

Float parameter setting the main window horizontal scale, in seconds per division.

 timebase_setup(*mode=None*, *offset=None*, *horizontal_range=None*, *scale=None*)

Configure the timebase. Parameters that are not provided stay unchanged. Changing one parameter can affect others. Consult the oscilloscope documentation and, when needed, make several consecutive channel_setup calls.

Parameters:

-

**mode** – Timebase mode; valid values are “main”, “window”, “xy”, or “roll”. (default: `None`)

-

**offset** – Seconds of offset between the trigger and the screen center. (default: `None`)

-

**horizontal_range** – Full-scale range, in seconds. (default: `None`)

-

**scale** – Seconds per division. (default: `None`)

 *property *waveform_data

Return the sampled-data binary block sent in IEEE 488.2 arbitrary block data format.

 *property *waveform_format*: Any*

String parameter controlling the format used when the oscilloscope sends data. Valid values are “ascii”, “word” or “byte”. Words use big endian transmission by default.

 *property *waveform_points*: Any*

Integer parameter setting how many waveform points waveform_data transfers. Allowed values are 100, 250, 500, and 1000; then 2 000, 5 000, 10 000, 20 000, 50 000, and 62 500.

Note that the oscilloscope may return fewer than the requested nb of points.

 *property *waveform_points_mode*: Any*

String parameter selecting the data record transferred by waveform_data. Valid values are “normal”, “maximum”, or “raw”.

 *property *waveform_preamble

Return preamble information for the selected waveform source as a dict. Keys include “format” for byte, word, or ascii (str); “type” for normal, peak detect, or average (str); “points” for nb of data points transferred (int); “count”, which is always 1 (int); “xincrement” for time between data points (float); “xorigin” for first memory data point (float); “xreference” for the data point associated with xorigin (int); “yincrement” for voltage between data points (float); “yorigin” for voltage at screen center (float); and “yreference” for the data point associated with yorigin (int).

 *property *waveform_source*: Any*

String parameter selecting which analog channel, function, or reference waveform the waveform methods use as their source. Valid values are “channel1”, “channel2”, “function”, “fft”, “wmemory1”, “wmemory2”, or “ext”.

## Keysight PNA Vector Network Analyzers

### Keysight PNA Vector Network Analyzers

 *class *pymeasure.instruments.keysight.KeysightPNA(*adapter*, *name='Keysight PNA'*, *data_format='real64'*, *byte_order_swapped=True*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for a Keysight PNA vector network analyzer.

Parameters:

-

**data_format** (*str*) – set `data_format` only to `ascii`, `real32`, or `real64`.

-

**byte_order_swapped** (*bool*) – set `byte_order_swapped` for `real32` or `real64` data formatting.

```python
pna = KeysightPNA("GPIB0::16::INSTR",
                  timeout=5000,
                  )

pna.load_state("D:/States/MyState.csa")
pna.adapter.connection.timeout = 20000  # set a new timeout to 20 sec
pna.ch_1.single()  # execute a single trigger of channel 1
pna.complete  # wait till the sweep has finished
x_data = pna.ch_1.tr_1.x_data  # get the X data of trace 1 in channel 1
y_data = pna.ch_2.tr_5.y_data  # get the Y data of trace 5 in channel 2
y_complex = pna.ch_2.tr_5.y_data_complex  # get the complex Y data of trace 5 in channel 2
pna.ch_1.tr_1.mkr_1.enabled = True  # Activate marker 1 on trace 1 in channel 1
pna.ch_1.tr_1.mkr_1.x = 123e6  # Set marker 1 to 123 MHz
mkr_y = pna.ch_1.tr_1.mkr_1.y  # Read the marker 1 y data

```

Workflow:

-

Configure channels/measurements on the PNA directly.

-

Calibrate the PNA

-

Save the current state as a csa file

-

Run single triggers across the different channels.

-

Access measurement data by channel number and trace number.

 abort()

Stop all sweeps.

Be aware that the configured trigger restarts the sweeps.

 *property *byte_order_swapped*: Any*

Enable or disable swapped byte order during data transfer (bool).

Some computers receive analyzer data in reverse order. This property only applies when `data_format` is `real32` or `real64`. With `data_format` set to `ascii`, `byte_order_swapped` has no effect.

-

`True`: Use with IBM compatible computers.

-

`False`: Use when the controller is anything other than an IBM compatible computers

or when VEE, LabView, or T&M Tool kit is being used.

 *property *data_format*: Any*

Control `data_format`, limited strictly to `ascii`, `real32`, or `real64`.

-

`ascii` is slow; choose it only when small amounts data must be transferred.

-

`real32` works best for large measurement-data transfers. It may introduce rounding errors in frequency data.

-

`real64` is slower than `real32` and provides more significant digits. Accurate frequency data representation requires it.

On the PNA, measurement data is kept as 32 bit and frequencies as 64 bit. Use `real32` for data and `real64` for frequencies so precision is not lost while data transfer stays as fast as possible.

Note

Running [`reset()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.reset) changes `data_format` back to `ascii`.

 load_state(*file_name*)

Load an instrument state from a file.

Parameters:

**file_name** (*str*) – e.g. `D:/my_pna_state.csa`

 *property *measurement_channels*: Any*

Return the channel numbers currently in use (list of int).

 *property *options*: Any*

Get the device options installed.

 *property *output_enabled*: Any*

Control whether source RF power output is enabled (bool).

 reset()

Reset the instrument.

 update_channels()

Refresh the PNA driver channel instances so they match the current channel configuration.

 *class *pymeasure.instruments.keysight.keysightPNA.MeasurementChannel(**args*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for a Keysight PNA measurement channel.

 continuous()

Put the channel in CONTINUOUS mode.

 hold()

Put the channel in HOLD mode.

 initiate()

Initiate an immidiate trigger.

Note

This command requires the trigger source to be MANUAL. Each `initiate()` execution sends one trigger signal.

 *property *measurements*: Any*

Return the channel's measurement trace numbers (list of int).

 *property *number_of_points*: Any*

Return the channel point count (int).

 single()

Trigger a single sweep.

 update_traces()

Refresh the channel trace instances so they match the current trace configuration.

 *class *pymeasure.instruments.keysight.keysightPNA.Trace(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for a Keysight PNA measurement trace.

 *property *parameter*: Any*

Return the trace measurement parameter (str).

 read_buffer(*data_format='ascii'*)

Read the PNA data buffer.

Parameters:

**data_format** – str, limited strictly to `ascii`, `real32`, or `real64` (default: `'ascii'`)

Returns:

ndarray

 *property *x_data

Return trace X data (ndarray).

Array element data type matches the currently selected `data_format`.

 *property *x_unit*: Any*

Return the trace X unit (str).

Returns:

`FREQ`, `POW`, `PHAS`, `DC`, `POIN` or `DEF`

 *property *y_data

Return trace Y data in the displayed format (ndarray).

Array element data type matches the currently selected `data_format`. This method returns data from access point 2. See PNA help for more detail about the data access map.

 *property *y_data_complex

Return complex trace Y data (2D ndarray).

Array element data type matches the currently selected `data_format`. This method returns data from access point 1. See PNA help for more detail about the data access map.

 *property *y_unit*: Any*

Return the trace Y unit (str).

Returns:

Allowed values, in order, are `HZ`, `SEC`, `MIN`, `HOUR`, `DAY`; then `DB`, `DBM`, `DBMV`, `WATT`, `FAR`, `HENR`, `OHM`, `MHO`, `SIEM`, `VOLT`; then `DEGR`, `RAD`, `MET`, `DPHZ`, `UNIT`, `NON`, `TNOR`, `NTEM`, `KELV`, `CENT`, `FAHR`; then `FEET`, `INCH`, `DBMAAMP`, `VOLTA`, `DBUV`, `PERC`, `DMVR`, `DUVR`, `DMAR`, `WPHZ`, `VRO`; then `ARO`, `DBC`, `DVP`, `DCP`, `DBP`, `HZP`, `PRH`, `VPH`, `DBV` or `DEF`

 *class *pymeasure.instruments.keysight.keysightPNA.Marker(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for a marker on a measurement trace.

 *property *enabled*: Any*

Control marker status (bool).

 *property *is_discrete*: Any*

Control marker discrete status (bool).

-

`True`: The marker moves to the nearest actual data point.

-

`False`: Data is interpolated between data points.

 *property *x*: Any*

Control the marker's X value (float).

 *property *y*: Any*

Return the marker's Y value ([float, float]).
