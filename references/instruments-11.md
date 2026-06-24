# Santec, Thorlabs, Fluke

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Santec; Santec TSL-570 Tunable Laser; Santec TSL-550 Tunable Laser; Santec TSL-500 Series Tunable Laser; Thorlabs; Thorlabs Pro 8000 modular laser driver; Thorlabs PM100USB Powermeter; Thorlabs MBX Series Modulator Bias Controllers; Fluke; Fluke 7341 Temperature bath.

## Santec

### Santec

Implemented Santec instruments are covered in this section. For a missing model, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Santec TSL-500 Series Tunable Laser](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl500series.html)
  - [`TSL500Series`](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl500series.html#pymeasure.instruments.santec.tsl500series.TSL500Series)

- [Santec TSL-570 Tunable Laser](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl570.html)
  - [`TSL570`](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl570.html#pymeasure.instruments.santec.tsl570.TSL570)

- [Santec TSL-550 Tunable Laser](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl550.html)
  - [`TSL550`](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl550.html#pymeasure.instruments.santec.tsl550.TSL550)

## Santec TSL-570 Tunable Laser

### Santec TSL-570 Tunable Laser

 *class *pymeasure.instruments.santec.tsl570.TSL570(*adapter*, *name='Santec TSL-570'*, ***kwargs*)

Bases: [`TSL500Series`](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl500series.html#pymeasure.instruments.santec.tsl500series.TSL500Series)

Provides a high-level control interface for the Santec TSL-570 Tunable Laser.

Except where noted, `TSL570.command_set` selects the wavelength and optical-frequency units.

 check_errors()

Collect every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect for errors and write them to the log.

Invoked for a property when `check_get_errors=True` is enabled.

Overriding this method can include raising an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property write, inspect for errors and write them to the log.

Invoked for a property when `check_set_errors=True` is enabled.

Overriding this method can include raising an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *command_set*: Any*

Select the command set: “Legacy” or “SCPI”.

Except where noted, Legacy commands express wavelength in nm and optical frequency in THz; SCPI commands use m for wavelength and Hz for optical frequency.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to coordinate controller and device timing. The Operation Complete query writes ASCII character 1 to the device's Output Queue once every pending selected device operation is done.

 *property *frequency_max*: Any*

Return the maximum frequency allowed in the configurable sweep range for the current sweep speed.

 *property *frequency_min*: Any*

Return the minimum frequency allowed in the configurable sweep range for the current sweep speed.

 *property *frequency_setpoint*: Any*

Control the output frequency.

 *property *frequency_start*: Any*

Control the sweep start frequency.

 *property *frequency_step*: Any*

Set the frequency increment used by step sweep mode.

 *property *frequency_stop*: Any*

Control the sweep stop frequency.

 *property *id*: Any*

Return the instrument identification.

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *output_enabled*: Any*

Enable or disable output (bool).

 *property *power*: Any*

Measure monitored optical power; units follow `power_unit`.

 *property *power_setpoint*: Any*

Set output optical power; units follow `power_unit`.

 *property *power_unit*: Any*

Select the power unit (str, ‘dBm’ or ‘mW’).

 read(***kwargs*)

Read until read_termination is encountered, excluding it, or return the whole read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes requested. Use -1 to consume the whole read buffer.

-

**kwargs** – Adapter keyword arguments.

Returns bytes:

Instrument response bytes, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Put the instrument in a safe, stable condition.

Return type:

`None`

 start_repeat()

Start repeated wavelength sweeps.

 start_sweep()

Start a single wavelength sweep.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 stop_sweep()

Stop the wavelength sweep.

 *property *sweep_count*: Any*

Return how many sweeps have completed so far.

 *property *sweep_cycles*: Any*

Set the sweep repetition count.

 *property *sweep_delay*: Any*

Set the delay between consecutive scans, in s (float strictly in range 0 to 999.9).

 *property *sweep_dwell*: Any*

Set the step-to-step delay in step sweep mode, in s.

Wavelength tuning time is not included. (float strictly in range 0 to 999.9)

 *property *sweep_mode*: Any*

Set the sweep mode using a `SweepMode` enum.

 *property *sweep_pattern*: SweepPattern*

Set the sweep pattern using a SweepPattern enum.

 *property *sweep_routing*: SweepRouting*

Set the sweep routing using a SweepRouting enum.

 *property *sweep_speed*: Any*

Set sweep speed. Unit: nm/s. Accepted int choices: 1, 2, 5, 10, 20, 50, 100, 200.

 *property *sweep_status*: Any*

Return current sweep status as a `SweepStatus` enum.

 wait_for(*query_delay=None*)

Pause for a duration. ‘ask’ uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 *property *wavelength_max*: Any*

Return the maximum wavelength allowed in the configurable sweep range for the current sweep speed.

 *property *wavelength_min*: Any*

Return the minimum wavelength allowed in the configurable sweep range for the current sweep speed.

 *property *wavelength_setpoint*: Any*

Control the output wavelength.

 *property *wavelength_start*: Any*

Control the sweep start wavelength.

 *property *wavelength_step*: Any*

Set the wavelength increment used by step sweep mode.

 *property *wavelength_stop*: Any*

Control the sweep stop wavelength.

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string to send to the instrument

-

**kwargs** – Adapter keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values sent to the device.

-

****kwargs** (**args**,*) – Additional arguments passed to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

## Santec TSL-550 Tunable Laser

### Santec TSL-550 Tunable Laser

 *class *pymeasure.instruments.santec.tsl550.TSL550(*adapter*, *name='Santec TSL-550'*, ***kwargs*)

Bases: [`TSL500Series`](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl500series.html#pymeasure.instruments.santec.tsl500series.TSL500Series)

Provides a high-level control interface for the Santec TSL-550 Tunable Laser.

Except where noted, wavelength values use nm and optical-frequency values use THz.

 check_errors()

Collect every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect for errors and write them to the log.

Invoked for a property when `check_get_errors=True` is enabled.

Overriding this method can include raising an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property write, inspect for errors and write them to the log.

Invoked for a property when `check_set_errors=True` is enabled.

Overriding this method can include raising an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to coordinate controller and device timing. The Operation Complete query writes ASCII character 1 to the device's Output Queue once every pending selected device operation is done.

 *property *frequency_setpoint*: Any*

Control the output frequency.

 *property *frequency_start*: Any*

Control the sweep start frequency.

 *property *frequency_step*: Any*

Set the frequency increment used by step sweep mode.

 *property *frequency_stop*: Any*

Control the sweep stop frequency.

 *property *id*: Any*

Return the instrument identification.

 *property *laser_enabled*: Any*

Enable or disable the laser diode (bool).

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *output_enabled*: Any*

Open or close the internal-shutter output path (bool).

 *property *power*: Any*

Measure monitored optical power; units follow `power_unit`.

 *property *power_setpoint*: Any*

Set output optical power; units follow `power_unit`.

 *property *power_unit*: Any*

Select the power unit (str, ‘dBm’ or ‘mW’).

 read(***kwargs*)

Read until read_termination is encountered, excluding it, or return the whole read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes requested. Use -1 to consume the whole read buffer.

-

**kwargs** – Adapter keyword arguments.

Returns bytes:

Instrument response bytes, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Put the instrument in a safe, stable condition.

Return type:

`None`

 start_repeat()

Start repeated wavelength sweeps.

 start_sweep()

Start a single wavelength sweep.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 stop_sweep()

Stop the wavelength sweep.

 *property *sweep_count*: Any*

Return how many sweeps have completed so far.

 *property *sweep_cycles*: Any*

Set the sweep repetition count.

 *property *sweep_delay*: Any*

Set the delay between consecutive scans, in s (float strictly in range 0 to 999.9).

 *property *sweep_dwell*: Any*

Set the step-to-step delay in step sweep mode, in s.

Wavelength tuning time is not included. (float strictly in range 0 to 999.9)

 *property *sweep_mode*: Any*

Set the sweep mode using a `SweepMode` enum.

 *property *sweep_pattern*: SweepPattern*

Set the sweep pattern using a SweepPattern enum.

 *property *sweep_routing*: SweepRouting*

Set the sweep routing using a SweepRouting enum.

 *property *sweep_speed*: Any*

Set sweep speed. Unit: nm/s. The value is a float, strictly in range 0.5 to 100, with rounding to 1 decimal place.

 *property *sweep_status*: Any*

Return current sweep status as a `SweepStatus` enum.

 wait_for(*query_delay=None*)

Pause for a duration. ‘ask’ uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 *property *wavelength_setpoint*: Any*

Control the output wavelength.

 *property *wavelength_start*: Any*

Control the sweep start wavelength.

 *property *wavelength_step*: Any*

Set the wavelength increment used by step sweep mode.

 *property *wavelength_stop*: Any*

Control the sweep stop wavelength.

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string to send to the instrument

-

**kwargs** – Adapter keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values sent to the device.

-

****kwargs** (**args**,*) – Additional arguments passed to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

## Santec TSL-500 Series Tunable Laser

### Santec TSL-500 Series Tunable Laser

 *class *pymeasure.instruments.santec.tsl500series.TSL500Series(*adapter*, *name='Santec TSL-500 Series'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level control interface for a Santec TSL-500 Series Tunable Laser.

 check_errors()

Collect every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect for errors and write them to the log.

Invoked for a property when `check_get_errors=True` is enabled.

Overriding this method can include raising an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property write, inspect for errors and write them to the log.

Invoked for a property when `check_set_errors=True` is enabled.

Overriding this method can include raising an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

Use this property to coordinate controller and device timing. The Operation Complete query writes ASCII character 1 to the device's Output Queue once every pending selected device operation is done.

 *property *frequency_setpoint*: Any*

Control the output frequency.

 *property *frequency_start*: Any*

Control the sweep start frequency.

 *property *frequency_step*: Any*

Set the frequency increment used by step sweep mode.

 *property *frequency_stop*: Any*

Control the sweep stop frequency.

 *property *id*: Any*

Return the instrument identification.

 *property *next_error*: Any*

Return the next queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *output_enabled*: Any*

Enable or disable output (bool).

 *property *power*: Any*

Measure monitored optical power; units follow `power_unit`.

 *property *power_setpoint*: Any*

Set output optical power; units follow `power_unit`.

 *property *power_unit*: Any*

Select the power unit (str, ‘dBm’ or ‘mW’).

 read(***kwargs*)

Read until read_termination is encountered, excluding it, or return the whole read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Receive binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes requested. Use -1 to consume the whole read buffer.

-

**kwargs** – Adapter keyword arguments.

Returns bytes:

Instrument response bytes, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Put the instrument in a safe, stable condition.

Return type:

`None`

 start_repeat()

Start repeated wavelength sweeps.

 start_sweep()

Start a single wavelength sweep.

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 stop_sweep()

Stop the wavelength sweep.

 *property *sweep_count*: Any*

Return how many sweeps have completed so far.

 *property *sweep_cycles*: Any*

Set the sweep repetition count.

 *property *sweep_delay*: Any*

Set the delay between consecutive scans, in s (float strictly in range 0 to 999.9).

 *property *sweep_dwell*: Any*

Set the step-to-step delay in step sweep mode, in s.

Wavelength tuning time is not included. (float strictly in range 0 to 999.9)

 *property *sweep_mode*: Any*

Set the sweep mode using a `SweepMode` enum.

 *property *sweep_pattern*: SweepPattern*

Set the sweep pattern using a SweepPattern enum.

 *property *sweep_routing*: SweepRouting*

Set the sweep routing using a SweepRouting enum.

 *property *sweep_speed*: Any*

Set sweep speed. Unit: nm/s. Accepted int choices: 1, 2, 5, 10, 20, 50, 100, 200.

 *property *sweep_status*: Any*

Return current sweep status as a `SweepStatus` enum.

 wait_for(*query_delay=None*)

Pause for a duration. ‘ask’ uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to wait between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 *property *wavelength_setpoint*: Any*

Control the output wavelength.

 *property *wavelength_start*: Any*

Control the sweep start wavelength.

 *property *wavelength_step*: Any*

Set the wavelength increment used by step sweep mode.

 *property *wavelength_stop*: Any*

Control the sweep stop wavelength.

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string to send to the instrument

-

**kwargs** – Adapter keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Transmit binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values sent to the device.

-

****kwargs** (**args**,*) – Additional arguments passed to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

## Thorlabs

### Thorlabs

Implemented Thorlabs instruments are covered in this section. For a missing model, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Thorlabs PM100USB Powermeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/thorlabs/thorlabspm100usb.html)
  - [`ThorlabsPM100USB`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thorlabs/thorlabspm100usb.html#pymeasure.instruments.thorlabs.ThorlabsPM100USB)

- [Thorlabs Pro 8000 modular laser driver](https://pymeasure.readthedocs.io/en/latest/api/instruments/thorlabs/thorlabspro8000.html)
  - [`ThorlabsPro8000`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thorlabs/thorlabspro8000.html#pymeasure.instruments.thorlabs.ThorlabsPro8000)

- [Thorlabs MBX Series Modulator Bias Controllers](https://pymeasure.readthedocs.io/en/latest/api/instruments/thorlabs/thorlabsmbxseries.html)
  - [`ThorlabsMBXSeries`](https://pymeasure.readthedocs.io/en/latest/api/instruments/thorlabs/thorlabsmbxseries.html#pymeasure.instruments.thorlabs.ThorlabsMBXSeries)

## Thorlabs Pro 8000 modular laser driver

### Thorlabs Pro 8000 modular laser driver

 *class *pymeasure.instruments.thorlabs.ThorlabsPro8000(*adapter*, *name='Thorlabs Pro 8000'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents Thorlabs Pro 8000 modular laser driver

 *property *LDCCurrent*: Any*

Control laser current.

 *property *LDCCurrentLimit*: Any*

Configure Software current Limit (value must be lower than hardware current limit).

 *property *LDCPolarity*: Any*

Configure laser diode polarity. Allowed values are: [‘AG’, ‘CG’]

 *property *LDCStatus*: Any*

Configure laser diode status. Allowed values are: [‘ON’, ‘OFF’]

 *property *TEDSetTemperature*: Any*

Control TEC temperature

 *property *TEDStatus*: Any*

Configure TEC status. Allowed values are: [‘ON’, ‘OFF’]

 *property *slot*: Any*

Choose slot selection. Allowed values are: range(1, 9)

## Thorlabs PM100USB Powermeter

### Thorlabs PM100USB Powermeter

 *class *pymeasure.instruments.thorlabs.ThorlabsPM100USB(*adapter*, *name='ThorlabsPM100USB powermeter'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents Thorlabs PM100USB powermeter.

 *property *energy

Measure the energy in J.

 *property *power

Measure the power in W.

 *property *wavelength

Control the wavelength in nm.

 *property *wavelength_max*: Any*

Measure maximum wavelength, in nm

 *property *wavelength_min*: Any*

Measure minimum wavelength, in nm

## Thorlabs MBX Series Modulator Bias Controllers

### Thorlabs MBX Series Modulator Bias Controllers

 *class *pymeasure.instruments.thorlabs.ThorlabsMBXSeries(*adapter*, *name='ThorlabsMBXSeries modulator bias controller'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents Thorlabs MBX Series Modulator Bias Controllers.

Note

-

RS-232 serial communication needs a null-modem connector.

-

USB serial communication requires a Silicon Labs® USB to UART DLL.

Abbreviations:

MZM - Mach Zender Modulator VOA - Variable Optical Attenuator

 mzm

Channel:

`ThorlabsMBXSeriesMZM`

 rgb

Channel:

`ThorlabsMBXSeriesRGB`

 voa

Channel:

`ThorlabsMBXSeriesVOA`

## Fluke

### Fluke

Implemented Fluke instruments are covered in this section. For a missing model, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Fluke 7341 Temperature bath](https://pymeasure.readthedocs.io/en/latest/api/instruments/fluke/fluke7341.html)
  - [`Fluke7341`](https://pymeasure.readthedocs.io/en/latest/api/instruments/fluke/fluke7341.html#pymeasure.instruments.fluke.Fluke7341)

## Fluke 7341 Temperature bath

### Fluke 7341 Temperature bath

 *class *pymeasure.instruments.fluke.Fluke7341(*adapter*, *name='Fluke 7341'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model wrapper for Fluke's compact constant temperature bath.

 *property *id*: Any*

Get the instrument model.

 read()

Read until read_termination is encountered, excluding it, or return the whole read buffer.

Parse the value out of the response string.

Response strings follow “type: value optional information”. The optional information may include the unit, such as degree centigrade or Fahrenheit.

 *property *set_point*: Any*

Set the temperature setpoint (float from -40 to 150 °C). The unit follows property `unit`.

 *property *temperature*: Any*

Measure current bath temperature. The unit follows property `unit`.

 *property *unit*: Any*

Select the temperature unit: c for Celsius and f for Fahrenheit`.
