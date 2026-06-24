# Tdk Gen40 38, Tdk Gen80 65

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: TDK Lambda Genesys 40-38 DC power supply; TDK Lambda Genesys 80-65 DC power supply; TDK Lambda.

## TDK Lambda Genesys 40-38 DC power supply

### TDK Lambda Genesys 40-38 DC power supply

 *class *pymeasure.instruments.tdk.tdk_gen40_38.TDK_Gen40_38(*adapter*, *name='TDK Lambda Gen40-38'*, *address=6*, ***kwargs*)

Bases: `TDK_Lambda_Base`

Models the TDK Lambda Genesys 40-38 DC power supply. Its commands come from the TDK_Lambda_Base parent class, and dynamic properties constrain the allowed values for selected properties.

```python
psu = TDK_Gen40_38("COM3", 6)       # COM port and daisy-chain address
psu.remote = "REM"                  # PSU in remote mode
psu.output_enabled = True           # Turn on output
psu.ramp_to_current(2.0)            # Ramp to 2.0 A of current
print(psu.current)                  # Measure actual PSU current
print(psu.voltage)                  # Measure actual PSU voltage
psu.shutdown()                      # Run shutdown command

```

To initialize a TDK instrument, supply the current TDK power supply address. For TDK Lambda, the default address is 6.

Parameters:

-

**adapter** – VISAAdapter instance

-

**name** – Instrument name; default value is “TDK Lambda Gen40-38” (default: `'TDK Lambda Gen40-38'`)

-

**address** – Serial port daisy chain number; default value is 6. (default: `6`)

 *property *address*: Any*

Configure the power supply address.

Accepts integer values from 0 - 30, inclusive.

 *property *auto_restart_enabled*: Any*

Configure auto restart mode, which starts by restoring the previous output voltage and current settings and enabling output.

Use `True` to restore output settings with output enabled at startup; use `False` to skip restoring settings and leave output disabled at startup.

 check_errors()

Retrieve every error from the instrument and log the results.

Returns:

`list` – List of error entries.

 check_get_errors()

After a property get, inspect for errors and log any findings.

Invoked for a property when `check_get_errors=True` is configured.

Overriding this method lets you raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

Use this command only for setters, meaning commands that are not queries.

For a non-querying command, meaning one without the “?” symbol such as the instrument command “PV 10”, the instrument responds with “OK” for an accepted command or with an error code. That acknowledgement confirms receipt. Querying commands, meaning commands that include the “?” symbol such as “PV?”, return the requested value instead of that acknowledgement.

 clear()

Set both FEVE and SEVE registers back to zero.

 *property *complete

Get the synchronization bit.

This property synchronizes a controller with a device. The Operation Complete query writes ASCII character 1 to the device’s Output Queue once every pending selected device operation is complete.

 *property *current*: Any*

Measure the actual output current.

Produces a float at five-digit precision.

 *property *current_setpoint*: Any*

Set the programmed (set) output current.(dynamic)

 *property *display*: Any*

Read the voltage and current currently shown on the display.

Provides ordered floating point values: [ measured voltage; then programmed voltage; then measured current; then programmed current; then over voltage set point; then under voltage set point ].

 *property *foldback_delay*: Any*

Control the fold back delay.

Extends the standard fold back delay (250 ms) by applying the set value times 0.1. Accepted values are integers from 0 to 255.

 *property *foldback_enabled*: Any*

Configure the power supply fold back protection.

Use `True` to arm fold back protection, or `False` to cancel it.

 foldback_reset()

Set fold back delay back to 0 s, which restores the standard 250 ms delay.

Property is UNTESTED.

 *property *id*: Any*

Read the instrument identity.

Provides the instrument manufacturer and model as a list formatted like `["LAMBDA", "GENX-Y"]`

 *property *last_test_date*: Any*

Read the most recent test date, possibly the calibration date.

Provides a string using the yyyy/mm/dd format.

 *property *master_slave_setting*: Any*

Read the master and slave settings.

Master may return 1, 2, 3, or 4. Slave returns 0.

Property is UNTESTED.

 *property *mode*: Any*

Read the power supply output mode.

With the power supply on, the return is either `'CV'` for control voltage or `'CC'` for control current. With the power supply off, the return is `'OFF'`.

 *property *multidrop_capability*: Any*

Read whether the power supply includes the multi-drop option.

A `False` return means the option is unavailable; `True` means it is available.

Property is UNTESTED.

 *property *next_error

Read the instrument's next error as a tuple of code and message.

 *property *options

Get the device options installed.

 *property *output_enabled*: Any*

Configure the power supply output.

Use `True` to enable output, or `False` to disable output and shut down voltage or current.

 *property *over_voltage*: Any*

Configure over voltage protection. (dynamic)

 *property *pass_filter*: Any*

Configure the low pass filter frequency of the A to D converter used for voltage and current measurement.

Frequency choices are 18, 23, or 46 Hz. The default value is 18 Hz.

 ramp_to_current(*target_current*, *steps=20*, *pause=0.2*)

Ramp from the set current value to a target current over a specified number of linear steps, with a pause duration between each step.

Parameters:

-

**target_current** – Target current, in amps

-

**steps** – Integer step count (default: `20`)

-

**pause** – Seconds to wait between steps (default: `0.2`)

 read(***kwargs*)

Read until read_termination, excluding it, or read the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Fetch binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Bytes to read. A value of -1 means read the entire read buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 recall()

Recall last saved instrument settings.

 *property *remote*: Any*

Configure the power supply's current remote operation mode.

Use `'LOC'` for local mode, `'REM'` for remote mode, or `'LLO'` for local lockout mode.

 *property *repeat*: Any*

Measure the last command again.

Provides the output from the previous command.

 reset()

Restore default values on the instrument.

 save()

Save current instrument settings.

 *property *serial*: Any*

Read the instrument serial number.

Provides the instrument serial number as an ASCII string.

 set_max_over_voltage()

Raise over voltage protection to the power supply's maximum level.

 shutdown()

Safety shutdown the power supply.

Use `self.ramp_to_current(0.0)` to ramp the power supply to zero current, then switch output off.

 *property *status*: Any*

Get the power supply status.

Provides this ordered list: [ actual voltage (MV); then programmed voltage (PV); then actual current (MC); then programmed current (PC); then status register (SR); then fault register (FR) ].

 *property *under_voltage*: Any*

Control the under voltage limit.

Property is UNTESTED. (dynamic)

 *property *version*: Any*

Read the instrument software version.

Provides the software version as an ASCII string.

 *property *voltage*: Any*

Measure the actual output voltage.

 *property *voltage_setpoint*: Any*

Set the programmed (set) output voltage.(dynamic)

 wait_for(*query_delay=None*)

Pause briefly; ‘ask’ uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to delay between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Write a string command to the instrument and append write_termination.

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

Write the bytes payload to the instrument.

Return type:

`None`

## TDK Lambda Genesys 80-65 DC power supply

### TDK Lambda Genesys 80-65 DC power supply

 *class *pymeasure.instruments.tdk.tdk_gen80_65.TDK_Gen80_65(*adapter*, *name='TDK Lambda Gen80-65'*, *address=6*, ***kwargs*)

Bases: `TDK_Lambda_Base`

Models the TDK Lambda Genesys 80-65 DC power supply. Its commands come from the TDK_Lambda_Base parent class, and dynamic properties constrain the allowed values for selected properties.

```python
psu = TDK_Gen80_65("COM3", 6)       # COM port and daisy-chain address
psu.remote = "REM"                  # PSU in remote mode
psu.output_enabled = True           # Turn on output
psu.ramp_to_current(2.0)            # Ramp to 2.0 A of current
print(psu.current)                  # Measure actual PSU current
print(psu.voltage)                  # Measure actual PSU voltage
psu.shutdown()                      # Run shutdown command

```

To initialize a TDK instrument, supply the current TDK power supply address. For TDK Lambda, the default address is 6.

Parameters:

-

**adapter** – VISAAdapter instance

-

**name** – Instrument name; default value is “TDK Lambda Gen80-65” (default: `'TDK Lambda Gen80-65'`)

-

**address** – Serial port daisy chain number; default value is 6. (default: `6`)

 *property *address*: Any*

Configure the power supply address.

Accepts integer values from 0 - 30, inclusive.

 *property *auto_restart_enabled*: Any*

Configure auto restart mode, which starts by restoring the previous output voltage and current settings and enabling output.

Use `True` to restore output settings with output enabled at startup; use `False` to skip restoring settings and leave output disabled at startup.

 check_errors()

Retrieve every error from the instrument and log the results.

Returns:

`list` – List of error entries.

 check_get_errors()

After a property get, inspect for errors and log any findings.

Invoked for a property when `check_get_errors=True` is configured.

Overriding this method lets you raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

Use this command only for setters, meaning commands that are not queries.

For a non-querying command, meaning one without the “?” symbol such as the instrument command “PV 10”, the instrument responds with “OK” for an accepted command or with an error code. That acknowledgement confirms receipt. Querying commands, meaning commands that include the “?” symbol such as “PV?”, return the requested value instead of that acknowledgement.

 clear()

Set both FEVE and SEVE registers back to zero.

 *property *complete

Get the synchronization bit.

This property synchronizes a controller with a device. The Operation Complete query writes ASCII character 1 to the device’s Output Queue once every pending selected device operation is complete.

 *property *current*: Any*

Measure the actual output current.

Produces a float at five-digit precision.

 *property *current_setpoint*: Any*

Set the programmed (set) output current.(dynamic)

 *property *display*: Any*

Read the voltage and current currently shown on the display.

Provides ordered floating point values: [ measured voltage; then programmed voltage; then measured current; then programmed current; then over voltage set point; then under voltage set point ].

 *property *foldback_delay*: Any*

Control the fold back delay.

Extends the standard fold back delay (250 ms) by applying the set value times 0.1. Accepted values are integers from 0 to 255.

 *property *foldback_enabled*: Any*

Configure the power supply fold back protection.

Use `True` to arm fold back protection, or `False` to cancel it.

 foldback_reset()

Set fold back delay back to 0 s, which restores the standard 250 ms delay.

Property is UNTESTED.

 *property *id*: Any*

Read the instrument identity.

Provides the instrument manufacturer and model as a list formatted like `["LAMBDA", "GENX-Y"]`

 *property *last_test_date*: Any*

Read the most recent test date, possibly the calibration date.

Provides a string using the yyyy/mm/dd format.

 *property *master_slave_setting*: Any*

Read the master and slave settings.

Master may return 1, 2, 3, or 4. Slave returns 0.

Property is UNTESTED.

 *property *mode*: Any*

Read the power supply output mode.

With the power supply on, the return is either `'CV'` for control voltage or `'CC'` for control current. With the power supply off, the return is `'OFF'`.

 *property *multidrop_capability*: Any*

Read whether the power supply includes the multi-drop option.

A `False` return means the option is unavailable; `True` means it is available.

Property is UNTESTED.

 *property *next_error

Read the instrument's next error as a tuple of code and message.

 *property *options

Get the device options installed.

 *property *output_enabled*: Any*

Configure the power supply output.

Use `True` to enable output, or `False` to disable output and shut down voltage or current.

 *property *over_voltage*: Any*

Configure over voltage protection. (dynamic)

 *property *pass_filter*: Any*

Configure the low pass filter frequency of the A to D converter used for voltage and current measurement.

Frequency choices are 18, 23, or 46 Hz. The default value is 18 Hz.

 ramp_to_current(*target_current*, *steps=20*, *pause=0.2*)

Ramp from the set current value to a target current over a specified number of linear steps, with a pause duration between each step.

Parameters:

-

**target_current** – Target current, in amps

-

**steps** – Integer step count (default: `20`)

-

**pause** – Seconds to wait between steps (default: `0.2`)

 read(***kwargs*)

Read until read_termination, excluding it, or read the complete read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Fetch binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read a requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Bytes to read. A value of -1 means read the entire read buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 recall()

Recall last saved instrument settings.

 *property *remote*: Any*

Configure the power supply's current remote operation mode.

Use `'LOC'` for local mode, `'REM'` for remote mode, or `'LLO'` for local lockout mode.

 *property *repeat*: Any*

Measure the last command again.

Provides the output from the previous command.

 reset()

Restore default values on the instrument.

 save()

Save current instrument settings.

 *property *serial*: Any*

Read the instrument serial number.

Provides the instrument serial number as an ASCII string.

 set_max_over_voltage()

Raise over voltage protection to the power supply's maximum level.

 shutdown()

Safety shutdown the power supply.

Use `self.ramp_to_current(0.0)` to ramp the power supply to zero current, then switch output off.

 *property *status*: Any*

Get the power supply status.

Provides this ordered list: [ actual voltage (MV); then programmed voltage (PV); then actual current (MC); then programmed current (PC); then status register (SR); then fault register (FR) ].

 *property *under_voltage*: Any*

Control the under voltage limit.

Property is UNTESTED. (dynamic)

 *property *version*: Any*

Read the instrument software version.

Provides the software version as an ASCII string.

 *property *voltage*: Any*

Measure the actual output voltage.

 *property *voltage_setpoint*: Any*

Set the programmed (set) output voltage.(dynamic)

 wait_for(*query_delay=None*)

Pause briefly; ‘ask’ uses this before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Seconds to delay between writing and reading. None uses the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Write a string command to the instrument and append write_termination.

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

Write the bytes payload to the instrument.

Return type:

`None`

## TDK Lambda

### TDK Lambda

This section documents the implemented TDK Lambda instruments. For an instrument that is not present, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [TDK Lambda Genesys 40-38 DC power supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/tdk/tdk_gen40_38.html)
  - [`TDK_Gen40_38`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tdk/tdk_gen40_38.html#pymeasure.instruments.tdk.tdk_gen40_38.TDK_Gen40_38)

- [TDK Lambda Genesys 80-65 DC power supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/tdk/tdk_gen80_65.html)
  - [`TDK_Gen80_65`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tdk/tdk_gen80_65.html#pymeasure.instruments.tdk.tdk_gen80_65.TDK_Gen80_65)
