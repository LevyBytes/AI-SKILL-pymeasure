# Tccxn

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: T&C Power Conversion AG Series Plasma Generator CXN; T&C Power Conversion.

## T&C Power Conversion AG Series Plasma Generator CXN

### T&C Power Conversion AG Series Plasma Generator CXN

 *class *pymeasure.instruments.tcpowerconversion.CXN(*adapter*, *name='T&C RF sputtering power supply'*, *address=0*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

The AG Series Plasma Generator CXN from T&C Power Conversion also appears under AJA International Inc branding as 0113 GTC or 0313 GTC.

Connect to the device over an RS232 serial connection. Its fixed communication settings are 38400, stopbit one, parity none. The device uses command/response communication: each received command is acknowledged by returning '*'. If the device does not recognize the command, it returns '?'.

Command message bytes (B) are arranged as: header: 1B, always 'C'; address: 1B, ignored; command id: 2B; parameter 1: 2B; parameter: 2B; checksum: 2B.

Response message bytes are arranged as: header: 1B, always 'R'; device address: 1B; data package length: 2B; data: variable length; checksum: 2B. Response messages arrive after the acknowledge byte.

Parameters:

-

**adapter** - pyvisa resource name for the instrument, or an adapter instance

-

**name** (*string*) - Name assigned to the instrument.

-

**kwargs** - Any valid Instrument key-word argument

Note

To enable parameter setting, request control and periodically poll any device value, at least once per 2s. Otherwise control is lost and the device resets certain parameters, such as setpoint and disable RF. If no value needs polling but control should stay active, use the ping method.

 preset_1

Channel:

`PresetChannel`

 preset_2

Channel:

`PresetChannel`

 preset_3

Channel:

`PresetChannel`

 preset_4

Channel:

`PresetChannel`

 preset_5

Channel:

`PresetChannel`

 preset_6

Channel:

`PresetChannel`

 preset_7

Channel:

`PresetChannel`

 preset_8

Channel:

`PresetChannel`

 preset_9

Channel:

`PresetChannel`

 *class *Status(**values*)

Bases: `IntFlag`

IntFlag type that represents the CXN status.

The status bits map as follows: bit 14 indicates Analog interface enabled; bit 11 indicates Interlock open; bit 10 indicates Over temperature; bit 9 indicates Reverse power limit; bit 8 indicates Forward power limit; bit 6 indicates MCG mode active; bit 5 indicates load power leveling active; bit 4 indicates External RF source active; bit 0 indicates RF power on.

 *property *dc_voltage*: Any*

Return the DC voltage in volts.

 *property *firmware_version*: Any*

Return the UI-processor and RF-processor firmware version numbers.

 *property *frequency*: Any*

Get operating frequency in Hz.

 *property *id*: Any*

Get the device identification string.

 *property *load_capacity*: Any*

Control load capacity, expressed as a full-scale value percentage. Setting it is allowed only when manual_mode is True.

 *property *manual_mode*: Any*

Control the manual tuner mode.

 *property *operation_mode*: Any*

Control the operation mode.

 ping()

Issue a ping to the instrument.

 *property *power*: Any*

Read forward/reverse/load power values in watts.

 *property *power_limit*: Any*

Return the maximum power of the power supply.

 *property *preset_slot*: Any*

Control the preset slot used for auto-tune mode. Accepts 0 to 9 as valid values; 0 selects no preset.

 *property *pulse_params*: Any*

Return the pulse waveform on/off time.

 *property *ramp_rate*: Any*

Control the ramp rate in watts/second.

 *property *ramp_start_power*: Any*

Control the ramp starting power in watts.

 read()

Read a response message from the instrument.

By reading the message header, this method automatically determines the message length and verifies that the checksum is correct.

Returns:

the data fields

Return type:

bytes

Raises:

**ValueError** - raised when a checksum error is detected

 release_control()

Release instrument control.

Resets selected properties to safe defaults and disables the RF output.

 request_control()

Request control of the instrument.

Required before any properties can be set.

 *property *reverse_power_limit*: Any*

Get maximum reverse power.

 *property *rf_enabled*: Any*

Control the RF output.

 *property *serial*: Any*

Return the instrument serial number.

 *property *setpoint*: Any*

Control the setpoint power level in watts.

 *property *status*: Any*

Return the status field. The returned value is represented by the IntFlag type Status.

 *property *temperature*: Any*

Return heat sink temperature in deg Celsius.

 *property *tune_capacity*: Any*

Control tune capacity, expressed as a full-scale value percentage. Setting it is allowed only when manual_mode is True.

 *property *tuner*: Any*

Return the type of the used tuner.

 values(*command*, *cast=<class 'int'>*, *separator='*, *'*, *preprocess_reply=None*, ***kwargs*)

Send the instrument a command and return the result as a list of formatted values.

This method is derived from CommonBase.values and adapted for bytes communication messages here, with no str conversion and strip. The implementation is general so both PresetChannel and CXN can use it. See Github issue #784 for details.

Parameters:

-

**command** - SCPI command sent to the instrument

-

**separator** - separator character for splitting the string into a list (default: `','`)

-

**cast** - type used to cast the result (default: `<class 'int'>`)

-

**preprocess_reply** - optional callable that processes instrument values before casting. It returns the processed string. (default: `None`)

Returns:

Returns a list in the desired type, with strings kept where casting fails

 write(*command*)

Sends a command to the instrument with the required header and address included.

Parameters:

**command** (*str*) - command sent to the instrument

 *class *pymeasure.instruments.tcpowerconversion.tccxn.PresetChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

 *property *load_capacity*: Any*

Control the load capacity preset as a percentage of full-scale value.

 *property *tune_capacity*: Any*

Control the tune capacity preset as a percentage of full-scale value.

 values(*command*, *cast=<class 'int'>*, *separator='*, *'*, *preprocess_reply=None*, ***kwargs*)

Send the instrument a command and return the result as a list of formatted values.

This method is derived from CommonBase.values and adapted for bytes communication messages here, with no str conversion and strip. The implementation is general so both PresetChannel and CXN can use it. See Github issue #784 for details.

Parameters:

-

**command** - SCPI command sent to the instrument

-

**separator** - separator character for splitting the string into a list (default: `','`)

-

**cast** - type used to cast the result (default: `<class 'int'>`)

-

**preprocess_reply** - optional callable that processes instrument values before casting. It returns the processed string. (default: `None`)

Returns:

Returns a list in the desired type, with strings kept where casting fails

## T&C Power Conversion

### T&C Power Conversion

This section documents the implemented instruments from T&C Power Conversion. For an instrument that is not included, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [T&C Power Conversion AG Series Plasma Generator CXN](https://pymeasure.readthedocs.io/en/latest/api/instruments/tcpowerconversion/tccxn.html)
  - [`CXN`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tcpowerconversion/tccxn.html#pymeasure.instruments.tcpowerconversion.CXN)
  - [`PresetChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tcpowerconversion/tccxn.html#pymeasure.instruments.tcpowerconversion.tccxn.PresetChannel)
