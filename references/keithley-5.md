# Keithley2260B, Keithley2281S, Keithley2600, Keithley4200

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Coverage includes Keithley 2260B DC Power Supply. It also includes Keithley 2281S power supply and battery simulator / characterizer, Keithley 2600 SourceMeter, and Keithley 4200A-SCS Parameter Analyzer.

## Keithley 2260B DC Power Supply

### Keithley 2260B DC Power Supply

 *class *pymeasure.instruments.keithley.Keithley2260B(*adapter*, *name='Keithley 2260B DC Power Supply'*, *read_termination='\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 2260B Power Supply with a minimal implementation and exposes a high-level interface for instrument operations.

For tcpip access, use the fixed port 2268; the device does not allow that port to be changed. Use ‘TCPIP::xxx.xxx.xxx.xxx::2268::SOCKET’ as the example connection string. For this interface, read termination is

```python
source = Keithley2260B("GPIB::1")
source.voltage = 1
print(source.voltage)
print(source.current)
print(source.power)
print(source.applied)

```

 *property *applied*: Any*

Set voltage (volts) and current (amps) together. Supply the pair as a tuple of (voltage, current). The actual output can diverge from the requested values according to whether the instrument is operating in constant current or constant voltage mode.

 check_errors()

Retrieve every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect the error queue and log any entries.

Used for a property when `check_get_errors=True` has been enabled.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property write, inspect the error queue and log any entries.

Used for a property when `check_set_errors=True` has been enabled.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property synchronizes a controller with a device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the device’s Output Queue.

 *property *current*: Any*

Return the current, in Ampere, that the dc power supply is delivering.

 *property *current_limit*: Any*

Set source current in amps. The value is not validated against the permitted range. In constant current or constant voltage mode, the achieved current may not equal the requested setting. (float)

 *property *enabled

Set whether the output is enabled; refer to `output_enabled`.

 *property *error

Return the instrument’s next error as a list containing code and message.

 *property *id*: Any*

Return the instrument identification string.

 *property *next_error*: Any*

Return one queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 *property *output_enabled*: Any*

Enable or disable the source with True or False. (bool)

 *property *power*: Any*

Return the power, in Watt, currently produced by the dc power supply.

 read(***kwargs*)

Read until, but not including, read_termination; otherwise return the full read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Bytes requested from the instrument. Use -1 to consume the full read buffer.

-

**kwargs** – Adapter keyword arguments.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Disable output, call parent function

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 *property *voltage*: Any*

Return the voltage, in Volt, currently output by the dc power supply.

 *property *voltage_setpoint*: Any*

Set source voltage in volts. The value is not validated against the permitted range. In constant current or constant voltage mode, the achieved voltage may not equal the requested setting. (float)

 wait_for(*query_delay=None*)

Pause briefly. ‘ask’ uses this delay before a read.

Parameters:

**query_delay** (`Optional`[`float`]) – Time, in seconds, between the write and the following read. None selects the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Adapter keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

-

****kwargs** (**args**,*) – Additional arguments forwarded to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

## Keithley 2281S power supply and battery simulator / characterizer

### Keithley 2281S power supply and battery simulator / characterizer

 *class *pymeasure.instruments.keithley.Keithley2281S(*adapter*, *name='Keithley2281S'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument), `KeithleyBuffer`

Models the Keithley 2281S-20-6 power supply and battery simulator / characterizer as an instrument class. Common commands other than function_mode and power supply commands are expected to operate on Keithley 2280S power supplies as well, but that has not been tested.

 bs

Channel:

`BatterySimulationChannel`

 bt

Channel:

`BatteryTestChannel`

 ps

Channel:

`PowerSupplyChannel`

 *property *buffer_data

Return buffer values as a pandas dataframe.

 *property *buffer_points*: Any*

Set the maximum count of buffer points retained.

 characterize(*lower_voltage*, *upper_voltage*, *charge_current*, *memory_slot*, *model_voltage_offset=0.05*, *charge_delay=0*)

Convenience routine for running a battery test and storing its model in internal memory.

The device discharges only at a fixed 1A. When that current is too high, place a series resistor in the discharge path to limit it. If discharge goes below the lower limit, the instrument charges at a 10th of the set charge current until the lower limit is reached, and only then characterizes the battery profile. This call blocks until measurement completion.

Parameters:

-

**lower_voltage** (*float*) – Discharge stop voltage; choose a value slightly lower (~0.05V) than normal operation.

-

**upper_voltage** (*float*) – Charge stop voltage; choose a value slightly higher (~0.05V) than normal operation.

-

**charge_current** (*float*) – Maximum charge current. The (dis-)charge end current is 1/100th of this value.

-

**memory_slot** (*int*) – Internal memory slot where the model is saved

-

**model_voltage_offset** (*float**, **optional*) – Offset applied to the generated model upper and lower voltage limits. The limits must remain inside the measured values, between the hard measurement limits. Default is 0.05. (default: `0.05`)

-

**charge_delay** (*float**, **optional*) – Wait time in seconds between discharge and charge phases. The real elapsed time is longer because the device delays reporting test completion internally. Default is 0. (default: `0`)

 check_errors()

Retrieve every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect the error queue and log any entries.

Used for a property when `check_get_errors=True` has been enabled.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property write, inspect the error queue and log any entries.

Used for a property when `check_set_errors=True` has been enabled.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property synchronizes a controller with a device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the device’s Output Queue.

 *property *display_text_data*: Any*

Set the control text shown on the display (24 characters).

 *property *function_mode*: Any*

Control function mode to use.

Allowed values are “POWER”, “TEST”, and “SIMULATOR”.

 *property *id*: Any*

Return the instrument identification string.

 *property *line_frequency*: Any*

Get line frequency.

 *property *measurement_event*: Any*

Get measurement event register.

 *property *measurement_ongoing*: bool*

Get measurement status.

 *property *next_error*: Any*

Return one queued error. To read and log every error, call `check_errors()` instead.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until, but not including, read_termination; otherwise return the full read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Bytes requested from the instrument. Use -1 to consume the full read buffer.

-

**kwargs** – Adapter keyword arguments.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 *property *reading_available*: bool*

Get availability of a reading.

 reset()

Reset the instrument.

 shutdown()

Return the instrument to a stable and safe state.

Return type:

`None`

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 *property *summary_event*: Any*

Get summary event register.

 wait_for(*query_delay=None*)

Pause briefly. ‘ask’ uses this delay before a read.

Parameters:

**query_delay** (`Optional`[`float`]) – Time, in seconds, between the write and the following read. None selects the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Adapter keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

-

****kwargs** (**args**,*) – Additional arguments forwarded to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.keithley.keithley2281S.Keithley2281SOperationEventRegister(**values*)

Enum containing Keithley2281S Operation Instrument Summary Event Register definition

 *class *pymeasure.instruments.keithley.keithley2281S.Keithley2281SMeasurementEventRegister(**values*)

Enum containing Keithley2281S Measurement Instrument Summary Event Register definition

## Keithley 2600 SourceMeter

### Keithley 2600 SourceMeter

 *class *pymeasure.instruments.keithley.Keithley2600(*adapter*, *name='Keithley 2600 SourceMeter'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Keithley 2600 series SourceMeter with channel A and channel B support.

 check_errors()

Retrieve every error reported by the instrument.

Returns:

List of error entries.

 check_get_errors()

After a property read, inspect the error queue and log any entries.

Used for a property when `check_get_errors=True` has been enabled.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 check_set_errors()

After a property write, inspect the error queue and log any entries.

Used for a property when `check_set_errors=True` has been enabled.

Overrides may raise an Exception for selected errors.

Returns:

`list` – List of error entries.

 clear()

Clear the instrument status byte.

 *property *complete*: Any*

Get the synchronization bit.

This property synchronizes a controller with a device. After all pending selected device operations finish, the Operation Complete query puts ASCII character 1 in the device’s Output Queue.

 *property *error

Return the next queued error.

Since version 0.15, this is deprecated; use next_error instead.

 *property *id*: Any*

Return the instrument identification string.

 *property *next_error

Return a tuple containing the error code and message for one error.

 *property *options*: Any*

Get the device options installed.

 read(***kwargs*)

Read until, but not including, read_termination; otherwise return the full read buffer.

Return type:

`str`

 read_binary_values(***kwargs*)

Retrieve binary values from the device.

 read_bytes(*count*, ***kwargs*)

Read the requested byte count from the instrument.

Parameters:

-

**count** (*int*) – Bytes requested from the instrument. Use -1 to consume the full read buffer.

-

**kwargs** – Adapter keyword arguments.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 reset()

Reset the instrument.

 shutdown()

Return the instrument to a stable and safe state.

Return type:

`None`

 *property *status*: Any*

Return the status byte together with the Master Summary Status bit.

 wait_for(*query_delay=None*)

Pause briefly. ‘ask’ uses this delay before a read.

Parameters:

**query_delay** (`Optional`[`float`]) – Time, in seconds, between the write and the following read. None selects the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Adapter keyword arguments.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values that will be transmitted.

-

****kwargs** (**args**,*) – Additional arguments forwarded to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

Return type:

`None`

## Keithley 4200A-SCS Parameter Analyzer

### Keithley 4200A-SCS Parameter Analyzer

 Class signature: *class *pymeasure.instruments.keithley.Keithley4200(*adapter*, *name='Keithley 4200A-SCS'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the Keithley 4200A-SCS Parameter Analyzer.

This driver controls the SMUs using only user mode commands.

Run the ‘KXCI’ program on the 4200A-SCS before remote control. Configure the remote interface with the Keithley Configuration Utility ‘KCon’.

At present, the driver works only with the ethernet interface.

 add_smu(*id*)

Register a SMU channel on the device.

 check_set_errors()

After sending a command, check whether errors occurred.

Raise:

Raise ValueError when the response is not ‘ACK’.

 clear()

Remove all entries from the buffer.

This also clears bit B0 (DATA_READY) in the status byte.

 *property *id*: Any*

Return the instrument identification string (str).

 *property *options*: Any*

Return the installed options (list of str).

 *property *status*: Any*

Get the status byte (IntFlag).

 *class *pymeasure.instruments.keithley.keithley4200.SMU(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Class for an SMU (source/measure unit) channel.

 *property *current*: Any*

Measure the current in Amps.

 *property *current_setpoint*: Any*

Configure range, output current, and voltage compliance (int, float, float).

Current uses Amps and voltage uses Volts.

```python
inst = Keithley4200("TCPIP::192.168.1.1::1225::SOCKET")
inst.smu1.current_setpoint = (9, 55e-3, 10)  # (range, value, compliance)
# Set SMU1 to output 55 mA in 100 mA range with 10 V voltage compliance

```

Current source range:

-

0: autorange

-

1: 1 nA range; requires a preamplifier

-

2: 10 nA range; requires a preamplifier

-

3: 100 nA range

-

4: 1 µA range

-

5: 10 µA range

-

6: 100 µA range

-

7: 1 mA range

-

8: 10 mA range

-

9: 100 mA range

-

10: 1 A range; requires a 4210-SMU or 4211-SMU

-

11: 1 pA range; requires a preamplifier

-

12: 10 pA range; requires a preamplifier

-

13: 100 pA range; requires a preamplifier

 disable()

Disable the SMU.

 *property *voltage*: Any*

Measure voltage in Volts (float).

 *property *voltage_setpoint*: Any*

Configure range, output voltage, and current compliance (int, float, float).

Voltage uses Volts and current uses Amps.

```python
inst = Keithley4200("TCPIP::192.168.1.1::1225::SOCKET")
inst.smu1.voltage_setpoint = (0, 3.3, 1e-2)  # (range, value, compliance)
# Set SMU1 to output 3.3 V in autorange with 10 mA current compliance

```

Voltage source range:

-

0: autorange

-

1: 20 V range

-

2: 200 V range

-

3: 200 V range

-

4: 200 mV range; requires a preamplifier

-

5: 2 V range; requires a preamplifier

 *class *pymeasure.instruments.keithley.keithley4200.StatusCode(**values*)

Bases: `IntFlag`

Class for Keithley 4200 status codes.

Status codes:

-

0: NONE

-

1: DATA_READY

-

2: SYNTAX_ERROR

-

16: BUSY

-

64: SERVICE_REQUEST
