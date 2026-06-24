# Teledynet3Afg

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Teledyne; Teledyne T3AFG Arbitrary Waveform Generator.

## Teledyne

### Teledyne

Find Teledyne-specific notes here for the instruments currently implemented. For an instrument missing from this list, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

When the instrument you need is absent here, older models may appear under [LeCroy](https://pymeasure.readthedocs.io/en/latest/api/instruments/lecroy/index.html).

- [Teledyne T3AFG Arbitrary Waveform Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyneT3AFG.html)

Teledyne oscilloscopes share base classes. Some devices can use those classes directly; the confirmed devices are:

-

[`TeledyneMAUI`](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#pymeasure.instruments.teledyne.TeledyneMAUI)

  -

Teledyne LeCroy HDO6xxx series (e.g. HDO6054B)

A device absent from the list may still work adequately with the base class. When adding another device, these base classes reduce the new code required.

- [Teledyne Oscilloscope base classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html)
  - [Teledyne Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#teledyne-oscilloscope)
  - [Teledyne Channel](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#teledyne-channel)
  - [Teledyne MAUI Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#teledyne-maui-oscilloscope)
  - [Teledyne MAUI Channel](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#teledyne-maui-channel)

## Teledyne T3AFG Arbitrary Waveform Generator

### Teledyne T3AFG Arbitrary Waveform Generator

 *class *pymeasure.instruments.teledyne.TeledyneT3AFG(*adapter*, *name='Teledyne T3AFG'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides the Teledyne T3AFG series arbitrary waveform generator interface used to communicate with the instrument.

The initial target is T3AFG80. Lower end models may lack some features, and higher end model features are not covered here yet.

Future improvements (help welcomed):

-

Add more OUTPut controls, such as Load and Polarity.

-

Add more Basic Waveform controls, such as Period.

-

Add frequency ranges per model

-

Add channel coupling control

 ch_1

Channel:

`SignalChannel`

 ch_2

Channel:

`SignalChannel`

 check_errors()

Retrieve every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property get, check for errors and log any found.

This is invoked when `check_get_errors=True` has been configured for that property.

An override of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set, check for errors and log any found.

This is invoked when `check_set_errors=True` has been configured for that property.

An override of this method may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property synchronizes a controller with a device. The Operation Complete query writes ASCII character 1 to the device’s Output Queue after all pending selected device operations are complete.

 *property *id*: Any*

Return the instrument identification.

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read data until, but not including, read_termination, or read the entire read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Fetch binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Bytes to read. Use -1 to read the full read buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Puts the instrument into a safe, stable state.

Return type:

`None`

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 wait_for(*query_delay=None*)

Pause for a period of time. ‘ask’ uses this delay before it reads.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to delay between write and read. `None` means the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, appending write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values to transmit.

-

****kwargs** (**args**,*) – Additional arguments to pass to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Transfer the bytes content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.teledyne.teledyneT3AFG.SignalChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

 *property *amplitude*: Any*

Set the output waveform amplitude in volts peak-to-peak. This has no effect when WVTP is NOISE or DC. The maximum amplitude depends on offset, frequency, and load, and the channel max output amplitude also limits it.(dynamic)

 *property *frequency*: Any*

Set the output waveform frequency in Hertz. This has no effect when WVTP is NOISE or DC.(dynamic)

 *property *max_output_amplitude*: Any*

Set the channel maximum output amplitude in volts peak to peak.(dynamic)

 *property *offset*: Any*

Set the output waveform offset in volts. This has no effect when WVTP is NOISE. Maximum offset depends on amplitude, frequency, and load, and the channel max output amplitude also limits it.(dynamic)

 *property *output_enabled*: Any*

Set whether channel output is enabled (boolean).

 *property *wavetype*: Any*

Set the output waveform type. Allowed values: ‘SINE’; ‘SQUARE’; ‘RAMP’; ‘PULSE’; ‘NOISE’; ‘ARB’; ‘DC’; ‘PRBS’; ‘IQ’.
