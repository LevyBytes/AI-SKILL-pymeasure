# Ah2700A, Ah2500A

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Coverage includes: Andeen Hagerling AH2700A capacitance bridge; Andeen Hagerling; Andeen Hagerling AH2500A capacitance bridge.

## Andeen Hagerling AH2700A capacitance bridge

### Andeen Hagerling AH2700A capacitance bridge

 Class constructor: *pymeasure.instruments.andeenhagerling.AH2700A* with *adapter*, *name='Andeen Hagerling 2700A Precision Capacitance Bridge'*, *timeout=5000*, and ***kwargs*.

Base class: [`AH2500A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/andeenhagerling/ah2500a.html#pymeasure.instruments.andeenhagerling.AH2500A)

Implementation for the Andeen Hagerling 2700A Precision Capacitance Bridge.

 *property *caplossvolt*: Any*

Fetch one capacitance/loss measurement; return capacitance in pF, loss in nS, and measurement voltage as the third value.

 check_errors()

Read every instrument error and write each one to the log.

Returns:

`list` – List of error entries.

 check_get_errors()

After a property get operation, check for errors and log any found.

Runs when that property has `check_get_errors=True` configured.

Overriders may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property set operation, check for errors and log any found.

Runs when that property has `check_set_errors=True` configured.

Overriders may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clears the instrument status byte

Return type:

`None`

 *property *complete

Get the synchronization bit.

This property supports controller/device synchronization. The Operation Complete query writes an ASCII character 1 to the device's Output Queue once all pending selected device operations have finished.

 *property *config*: Any*

Get the configuration

 *property *frequency*: Any*

Set the measurement test frequency. Values from 50 through 20000 Hz are allowed, and the device chooses the nearest available frequency to the supplied value.

 *property *id*: Any*

Get the instrument identification

 *property *next_error

Return the instrument's next error as a tuple containing code and message.

 *property *options

Get the device options installed.

 read(***kwargs*)

Read until just before read_termination, or read the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Read device data as binary values.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) - Number of bytes to read; -1 means read the entire read buffer.

-

**kwargs** - Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Resets the instrument.

 shutdown()

Put the instrument into a stable, safe state.

Return type:

`None`

 *property *status

Return the status byte together with the Master Summary Status bit.

 trigger()

Start a new measurement without blocking or waiting for the return value.

 triggered_caplossvolt()

Read the measurement value after the trigger function has triggered the device.

 *property *vhighest*: Any*

Set the maximum RMS value for the measurement voltage. Up to 15 V is allowed, and the device chooses the best-fitting range below the supplied value.

 wait_for(*query_delay=None*)

Pause for a period of time; `ask` uses this delay before reading.

Parameters:

**query_delay** (`Optional`[`float`]) - Delay between writing and reading, measured in seconds. None uses the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Write a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) - Command string sent to the instrument.

-

**kwargs** - Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) - Values to transmit.

-

****kwargs** (**args**,*) - Additional arguments passed to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Write byte content to the instrument.

Return type:

`None`

## Andeen Hagerling

### Andeen Hagerling

This section gives targeted documentation for the implemented Andeen Hagerling instruments. For an instrument that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Andeen Hagerling AH2500A capacitance bridge](https://pymeasure.readthedocs.io/en/latest/api/instruments/andeenhagerling/ah2500a.html)
  - [`AH2500A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/andeenhagerling/ah2500a.html#pymeasure.instruments.andeenhagerling.AH2500A)

- [Andeen Hagerling AH2700A capacitance bridge](https://pymeasure.readthedocs.io/en/latest/api/instruments/andeenhagerling/ah2700a.html)
  - [`AH2700A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/andeenhagerling/ah2700a.html#pymeasure.instruments.andeenhagerling.AH2700A)

## Andeen Hagerling AH2500A capacitance bridge

### Andeen Hagerling AH2500A capacitance bridge

 Class constructor: *pymeasure.instruments.andeenhagerling.AH2500A* with *adapter*, *name=None*, *timeout=3000*, *write_termination='\n'*, *read_termination='\n'*, and ***kwargs*.

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Implementation for the Andeen Hagerling 2500A Precision Capacitance Bridge.

 *property *caplossvolt*: Any*

Fetch one capacitance/loss measurement; return capacitance in pF, loss in nS, and measurement voltage as the third value.

 *property *config*: Any*

Get the configuration.

 trigger()

Start a new measurement without blocking or waiting for the return value.

 triggered_caplossvolt()

Read the measurement value after the trigger function has triggered the device.

 *property *vhighest*: Any*

Set the maximum RMS value for the measurement voltage. Up to 15 V is allowed, and the device chooses the best-fitting range below the supplied value.
