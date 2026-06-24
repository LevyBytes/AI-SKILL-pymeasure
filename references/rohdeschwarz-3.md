# Fsseries, Hmp

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: R&S FS Series spectrum analyzer; R&S HMP4040 Power Supply.

## R&S FS Series spectrum analyzer

### R&S FS Series spectrum analyzer

### Connecting to an R&S FSL via network

After network attachment, read the instrument IP from the front-panel UI: choose “Setup”, then “General Settings” -> “Network Address”.

Use that address in a connection call such as this:

```python
from pymeasure.instruments.rohdeschwarz import FSL
fsl = FSL("TCPIP::192.168.1.123::INSTR")

```

### Getting and setting parameters

The driver exposes most settings as properties, so the same attribute-style access handles reads and writes. Bare numeric inputs are interpreted in base units (s, Hz, dB, …). Values may also include a unit suffix, for example `"1.5 GHz"` or `"1.5GHz"`. Reads always return numbers.

```python
# Getting the current center frequency
fsl.freq_center

9000000000.0

```

```python
# Changing it to 10 MHz by providing the numerical value
fsl.freq_center = 10e6

```

```python
# Verifying:
fsl.freq_center

10000000.0

```

```python
# Changing it to 9 GHz by providing a string and verifying the result
fsl.freq_center = '9GHz'
fsl.freq_center

9000000000.0

```

```python
# Setting the span to maximum
fsl.freq_span = '7 GHz'

```

### Reading a trace

Read the trace that is currently selected.

```python
x, y = fsl.read_trace()

```

### Markers

Markers use a separate class. Instantiate one with:

```python
m1 = fsl.create_marker()

```

Set peak exursion:

```python
m1.peak_excursion = 3

```

Move the marker to an exact position:

```python
m1.x = 10e9

```

Search leftward for the next peak, then read its level:

```python
m1.to_next_peak('left')
m1.y

-34.9349060059

```

### Delta markers

Set the appropriate keyword to create a delta marker.

```python
d2 = fsl.create_marker(is_delta_marker=True)
d2.name

'DELT2'

```

### Example program

The following short script records a signal peak.

```python
m1 = fsl.create_marker() # create marker 1

# Set standard settings, set to full span
fsl.continuous_sweep = False
fsl.freq_span = '18 GHz'
fsl.res_bandwidth = "AUTO"
fsl.video_bandwidth = "AUTO"
fsl.sweep_time = "AUTO"

# Perform a sweep on full span, set the marker to the peak and some to that marker
fsl.single_sweep()
m1.to_peak()
m1.zoom('20 MHz')

# take data from the zoomed-in region
fsl.single_sweep()
x, y = fsl.read_trace()

```

 *class *pymeasure.instruments.rohdeschwarz.fsseries.FSSeries(*adapter*, *name='Rohde&Schwarz FS series instrument'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models a Rohde&Schwarz FS Series spectrum analyzer, including FSL and FSW.

Settable physical quantities accept either a value-with-unit string such as “1.2 GHz” or a float expressed in base units (Hz, dBm, etc.).

 *property *attenuation*: Any*

Control attenuation in dB.

 continue_single_sweep()

Resume using a synchronized single sweep.

 *property *continuous_sweep_enabled*: Any*

Choose continuous sweep with True, or single sweep with False.

 create_marker(*num=1*, *is_delta_marker=False*)

Create a marker.

Parameters:

-

**num** – The marker number (1-4) (default: `1`)

-

**is_delta_marker** – Set to True when the marker should be a delta marker; False is the default. (default: `False`)

Returns:

The marker object.

 *property *freq_center*: Any*

Control center frequency in Hz.

 *property *freq_span*: Any*

Control frequency span in Hz.

 *property *freq_start*: Any*

Control start frequency in Hz.

 *property *freq_stop*: Any*

Control stop frequency in Hz.

 *property *res_bandwidth*: Any*

Set or read resolution bandwidth in Hz; ‘AUTO’ is also accepted.

 single_sweep()

Run one synchronized sweep.

 *property *sweep_time*: Any*

Set or read sweep time in s; ‘AUTO’ is also accepted.

 *property *trace_mode*: Any*

Set or read trace mode: ‘WRIT’ means Write, ‘MAXH’ means Max Hold, ‘MINH’ means Min Hold, ‘AVER’ means Average, and ‘VIEW’ means View.

 *property *video_bandwidth*: Any*

Set or read video bandwidth in Hz; ‘AUTO’ is also accepted.

 *class *pymeasure.instruments.rohdeschwarz.fsseries.FSL(*adapter*, *name='Rohde&Schwarz FSL'*, ***kwargs*)

Bases: `FSSeries`

Models a Rohde&Schwarz FSL spectrum analyzer.

Settable physical quantities accept either a value-with-unit string such as “1.2 GHz” or a float expressed in base units (Hz, dBm, etc.).

 read_trace(*n_trace=1*)

Read trace data.

Parameters:

**n_trace** – Trace selector, numbered 1-6; the default is 1. (default: `1`)

Returns:

Trace data as a 2d numpy array, [[frequency], [amplitude]].

 *class *pymeasure.instruments.rohdeschwarz.fsseries.FSW(*adapter*, *name='Rohde&Schwarz FSW'*, ***kwargs*)

Bases: `FSSeries`

Models a Rohde&Schwarz FSW spectrum analyzer.

Settable physical quantities accept either a value-with-unit string such as “1.2 GHz” or a float expressed in base units (Hz, dBm, etc.).

 *property *activate_channel

Set or read the active channel name. Note: the channel must already be open on the device!

Returns:

active channel name

Return type:

string

 *property *active_channel

Read or set the active channel name. Note: the channel must already be open on the device!

Returns:

active channel name

Return type:

string

 auto_all()

Adjust all determinable settings automatically.

 auto_freq()

Adjust center frequency automatically.

 auto_level()

Adjust reference level automatically.

 *property *available_channels*: Any*

Return the names of open channels with their matching types.

 create_channel(*channel_type*, *channel_name*)

Create a new channel.

Parameters:

-

**channel_type** – Channel type to create, for example “PNOISE” or “SANALYZER”.

-

**channel_name** – Name assigned to the channel being added.

 delete_channel(*channel_name*)

Deletes an active channel.

 *property *nominal_level*: Any*

Set or read the instrument nominal level.

 read_trace(*n_trace=1*)

Read data from the active trace.

Parameters:

**n_trace** – Trace selector, numbered 1-6; the default is 1. (default: `1`)

Returns:

Trace data as a 2d numpy array, [[frequency], [amplitude]].

 rename_channel(*current_name*, *new_name*)

Rename `current_name` to `new_name` for a channel.

Parameters:

-

**current_name** – Channel selected for renaming.

-

**new_name** – Replacement channel name.

 select_channel(*channel_name*)

Select an open channel

Parameters:

**channel_name** – Channel selected for use.

 *property *split_view*: Any*

Set or read device viewmode: True selects split view, and False selects single channel view.

## R&S HMP4040 Power Supply

### R&S HMP4040 Power Supply

 *class *pymeasure.instruments.rohdeschwarz.hmp.HMP4040(*adapter*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models a Rohde&Schwarz HMP4040 power supply.

 beep()

Make the instrument emit one beep.

 clear_sequence(*channel*)

Erase the selected channel sequence.

 *property *control_method*: Any*

Select manual front panel (‘LOC’), remote (‘REM’), manual/remote control(‘MIX’), or locked front panel control (‘RWL’).

 *property *current*: Any*

Set or read output current in A; the instrument type determines the range.

 *property *current_step*: Any*

Control current step in A.

 current_to_max()

Drive the selected channel current to its maximum value.

 current_to_min()

Drive the selected channel current to its minimum value.

 load_sequence(*slot*)

Load a stored waveform from internal memory, using slot 1, 2 or 3.

 *property *max_current*: Any*

Get maximum current in A.

 *property *max_voltage*: Any*

Get maximum voltage in V.

 *property *measured_current*: Any*

Get current in A.

 *property *measured_voltage*: Any*

Get voltage in V.

 *property *min_current*: Any*

Get minimum current in A.

 *property *min_voltage*: Any*

Get minimum voltage in V.

 *property *output_enabled*: Any*

Set output on/off or read the output status.

 *property *repetitions*: Any*

Set the repetition count (0…255). Entering 0 repeats the sequence indefinitely.

 save_sequence(*slot*)

Store the sequence from the sequence property in internal memory, slot 1, 2 or 3.

 *property *selected_channel*: Any*

Control the selected channel.

 *property *selected_channel_active*: Any*

Set the selected channel active/inactive, or read its status.

 *property *sequence*: Any*

Define the sequence as triplets of voltage (V), current (A), and dwell time (s).

 set_channel_state(*channel*, *state*)

Change the channel state to active or inactive.

Parameters:

-

**channel** (*int*) – Channel number whose state will be set.

-

**state** (*bool*) – Channel state: True means active, False means inactive.

 start_sequence(*channel*)

Start the selected channel sequence.

 step_current_down()

Decreases current by one step.

 step_current_up()

Increase current by one step.

 step_voltage_down()

Decrease voltage by one step.

 step_voltage_up()

Increase voltage by one step.

 stop_sequence(*channel*)

Stop the sequence from the selected channel's sequence property.

 transfer_sequence(*channel*)

Transfer the sequence property contents to the selected channel.

 *property *version*: Any*

Read the SCPI version matched by the instrument’s command set.

 *property *voltage*: Any*

Set or read output voltage in V, with a 0.001 V increment.

 *property *voltage_and_current*: Any*

Set or read output voltage (V) together with current (A).

 *property *voltage_step*: Any*

Set or read voltage step in V; the default is 1 V.

 voltage_to_max()

Drive the selected channel voltage to its maximum value.

 voltage_to_min()

Drive the selected channel voltage to its minimum value.
