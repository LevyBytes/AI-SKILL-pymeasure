# Redpitaya, Kuhneelectronic, Ophir

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers Redpitaya support, including the Redpitaya board for analog signal acquisition/generation and digital input/output. Also covers Kuhne Electronic `KU SG 2.45 250 A - 2.45 GHz ISM-Band Microwave Generator`, plus Ophir `Nova II`, `Ophir Base`, `Nova`, and `Vega` instruments.

## Redpitaya

### Redpitaya

This part documents the implemented Redpitaya instruments. For hardware that is not listed here, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Redpitaya board for analog signal acquisition and generation as well as digital input/output](https://pymeasure.readthedocs.io/en/latest/api/instruments/redpitaya/redpitaya_scpi.html)
  - [`RedPitayaScpi`](https://pymeasure.readthedocs.io/en/latest/api/instruments/redpitaya/redpitaya_scpi.html#pymeasure.instruments.redpitaya.redpitaya_scpi.RedPitayaScpi)

## Redpitaya board for analog signal acquisition and generation as well as digital input/output

### Redpitaya board for analog signal acquisition and generation as well as digital input/output

 *class *pymeasure.instruments.redpitaya.redpitaya_scpi.RedPitayaScpi(*adapter=None*, *ip_address='169.254.134.87'*, *port=5000*, *name='Redpitaya SCPI'*, *read_termination='\\r\\n'*, *write_termination='\\r\\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class wrapper for the Redpitaya reconfigurable board.

Connect to the instrument over a TCP/IP Socket adapter written as "TCPIP::x.y.z.k::port::SOCKET". In that string, x.y.z.k is the SCPI server IP address, and port is the TCP/IP port, commonly 5000; the board must already have its SCPI server running.

To start the SCPI server, attach the redpitaya to the computer or network, then open the URL printed on the board's network connector. It should look similar to "RP-F06432.LOCAL/". In the web interface, go to the menu, launch the Development application, and enable the SCPI server; the interface then reports the IP/port address needed by this Instrument.

Parameters:

-

**ip_address** (`str`) - IP address used when adapter is None. (default: `'169.254.134.87'`)

-

**port** (`int`) - Port number used when adapter is None. (default: `5000`)

 analog_in

Channels:

`ain1`: `AnalogInputFastChannel`, `ain2`: `AnalogInputFastChannel`

 analog_in_slow

Channels:

`ainslow0`: `AnalogInputSlowChannel`, `ainslow1`: `AnalogInputSlowChannel`, `ainslow2`: `AnalogInputSlowChannel`, `ainslow3`: `AnalogInputSlowChannel`

 analog_out_slow

Channels:

`aoutslow0`: `AnalogOutputSlowChannel`, `aoutslow1`: `AnalogOutputSlowChannel`, `aoutslow2`: `AnalogOutputSlowChannel`, `aoutslow3`: `AnalogOutputSlowChannel`

 dioN

Channels:

`dioN0`: `DigitalChannelN`, `dioN1`: `DigitalChannelN`, `dioN2`: `DigitalChannelN`, `dioN3`: `DigitalChannelN`, `dioN4`: `DigitalChannelN`, `dioN5`: `DigitalChannelN`, `dioN6`: `DigitalChannelN`

 dioP

Channels:

`dioP0`: `DigitalChannelP`, `dioP1`: `DigitalChannelP`, `dioP2`: `DigitalChannelP`, `dioP3`: `DigitalChannelP`, `dioP4`: `DigitalChannelP`, `dioP5`: `DigitalChannelP`, `dioP6`: `DigitalChannelP`

 led

Channels:

`led0`: `DigitalChannelLed`, `led1`: `DigitalChannelLed`, `led2`: `DigitalChannelLed`, `led3`: `DigitalChannelLed`, `led4`: `DigitalChannelLed`, `led5`: `DigitalChannelLed`, `led6`: `DigitalChannelLed`, `led7`: `DigitalChannelLed`

 *property *acq_buffer_filled*: Any*

Read whether the buffer is full; the returned value is a bool, with True meaning full.

 *property *acq_format*: Any*

Choose the returned buffer data format (str): either 'BIN' or the default 'ASCII'.

 *property *acq_trigger_delay_ns

Set trigger delay in nanoseconds (int), using the range [-8192, 8192] / CLOCK.

 *property *acq_trigger_delay_samples*: Any*

Set trigger delay by sample count (int), with accepted values from [-8192, 8192].

 *property *acq_trigger_level*: Any*

Set trigger level in volts. The valid range is determined dynamically from the gain setting, using either +-LV_MAX or +- HV_MAX.

 *property *acq_trigger_position*: Any*

Read the buffer position at which the trigger event occurred.

 *property *acq_trigger_source*: Any*

Select the trigger source (str) from RedPitayaScpi.TRIGGER_SOURCES. PE denotes a Positive edge, while NE denotes a Negative edge.

 *property *acq_trigger_status*: Any*

Read trigger status as a bool; True means the trigger has fired or triggering is disabled.

 *property *acq_units*: Any*

Select output units for data (str): either 'RAW' or the default 'VOLTS'.

 analog_reset()

Reset all analog channel voltages.

 *property *average_skipped_samples*: Any*

Enable or disable averaging of skipped samples, when decimation > 1, for the returned acquisition array (bool).

 *property *board_name*: Any*

Get the RedPitaya board name

 *property *buffer_length*: Any*

Read the buffer length, meaning the number of acquisition points.

 *property *date*: Any*

Set the board date; pass the value as a datetime.date object.

 *property *decimation*: Any*

Set decimation (int) as 2**n, where n is in [0, 16]. Sampling rate is 125MS/s divided by decimation.

 digital_reset()

Reset every digital line state.

 *property *time*: Any*

Set the board time; pass the value as a datetime.time object.

## Kuhne Electronic

### Kuhne Electronic

This part documents the implemented Kuhne Electronic instruments. For an unsupported instrument, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [KU SG 2.45 250 A - 2.45 GHz ISM-Band Microwave Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/kuhneelectronic/kusg245_250a.html)
  - [`Kusg245_250A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/kuhneelectronic/kusg245_250a.html#pymeasure.instruments.kuhneelectronic.Kusg245_250A)

## KU SG 2.45 250 A - 2.45 GHz ISM-Band Microwave Generator

### KU SG 2.45 250 A - 2.45 GHz ISM-Band Microwave Generator

 *class *pymeasure.instruments.kuhneelectronic.Kusg245_250A(*adapter*, *name='KU SG 2.45 250 A'*, *power_limit=250*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

High-level interface for operating the KU SG 2.45 250 A - 2.45 GHz ISM-Band Microwave Generator.

Parameters:

**power_limit** - maximum allowed power set-point in Watts, as an integer from 0 to 250. See `power_setpoint` and `tune()`. (default: `250`)

Usage example:

```python
from pymeasure.instruments.kuhneelectronic import Kusg245_250A

generator = Kusg245_250A("ASRL3::INSTR", power_limit=100) # limits the output
                                                          # power set-point to 100 W

generator.external_enabled = False      # biasing and RF output controlled by serial comm
generator.power = 20                    # Sets the output power to 20 Watts
generator.bias_enabled = True           # Enables amplifier biasing
generator.rf_enabled = True             # Enables the RF output

p_fwd = generator.power_forward         # Reads forward power in Watts
p_rev = generator.power_reverse         # Reads reflected power in Watts

```

 *property *bias_enabled

Enable or disable transistor biasing (boolean).

Turn on biasing before enabling RF; see `rf_enabled`.

 clear_VSWR_error()

Clear the VSWR error.

See: `reflection_limit`.

 *property *external_enabled

Choose whether amplifier enabling comes from external inputs on the 8-pin connector or from the serial interface (boolean).

 *property *freq_steps_fine_enabled

Enable or disable fine frequency steps (boolean).

 *property *frequency_coarse*: Any*

Set coarse frequency in MHz, as an integer from 2400 to 2500.

Fine frequency mode must be off; see `freq_steps_fine_enabled`. Resolution is 1 MHz, and invalid values are truncated.

 *property *frequency_fine*: Any*

Set fine frequency in kHz, as an integer from 2400000 to 2500000.

Fine frequency mode must be on; see `freq_steps_fine_enabled`. Resolution is 10 kHz. Invalid entries are truncated, and values are rounded to tens.

 *property *off_time*: Any*

Set pulse-mode off time in ms, as an integer from 10 to 1000.

Resolution is 5 ms. Invalid entries are truncated, and values are rounded to multiples of 5.

 *property *phase_shift

Set phase shift in degrees, as a float from 0 to 358.6.

Resolution is 8-bits. Out-of-range values are truncated.

 *property *power_forward

Measure forward power in Watts.

 *property *power_reverse

Measure reverse power in Watts.

 *property *power_setpoint*: Any*

Set output power set-point in Watts, as an integer from 0 up to the constructor's `power_limit` parameter.

Resolution is 1 W. Invalid entries are truncated. (dynamic)

 *property *pulse_mode_enabled

Enable or disable pulse mode (boolean).

Note

Biasing must be on before pulse mode can be enabled; see `bias_enabled`.

 *property *pulse_width*: Any*

Set pulse width in ms, as an integer from 10 to 1000.

Resolution is 5 ms. Invalid entries are truncated, and values are rounded to multiples of 5.

 *property *reflection_limit

Set the reflection limit in Watts; accepted integer choices are 0 for no limit, 100, 150, 180, 200, and 230.

Note

When reflected power hits the configured limit, forward power is lowered to that value and power control stays locked until the user clears the alarm with `clear_VSWR_error()`.

 *property *rf_enabled

Enable or disable RF output (boolean).

Note

Biasing must be on before RF can be enabled; see `bias_enabled`.

 store_settings()

Save actual settings to EEPROM.

Stored settings include the fine-frequency mode flag (`freq_steps_fine_enabled`), the active frequency value (`frequency_coarse` or `frequency_fine`), and the output power target (`power_setpoint`). They also include external ON/OFF control (`external_enabled`), reflection limiting (`reflection_limit`), pulse on time (`pulse_width`), and pulse off time (`off_time`).

 *property *temperature*: Any*

Read the temperature near the final transistor in ?C.

 tune(*power*)

Search for and apply the frequency with the lowest reflection at the specified power.

Parameters:

**power** - power set-point used while tuning, in Watts, as an integer from 0 up to the constructor's `power_limit` parameter.

 turn_off()

Safe turn-off the generator.

1.

Disable RF output.

2.

Deactivate biasing.

 turn_on()

Safe turn-on the generator.

1.

Activate biasing.

2.

Enable RF output.

 *property *version*: Any*

Get firmware version.

 *property *voltage_32v

Read the 32V supply voltage in Volts.

 *property *voltage_5v

Read the internal 5V supply voltage in Volts.

 write(*command*, ***kwargs*)

Send a string command to the instrument, adding write_termination.

Parameters:

-

**command** - command string sent to the instrument

-

**kwargs** - Keyword arguments passed to the adapter.

## Nova II

### Nova II

 *class *pymeasure.instruments.ophir.novaII.NovaII(*adapter*, *name='NovaII'*, ***kwargs*)

Bases: [`AverageMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.AverageMixin), [`KeyMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.KeyMixin), [`OphirBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.OphirBase)

Represents an Ophir Nova II laser power/energy meter.

 *class *Modes(**values*)

Bases: `IntEnum`

Supported Nova II measurement modes.

## Ophir Base

### Ophir Base

This subpackage provides the `OphirBase` base class, which already supports many devices, plus Mixins for selected features.

 *class *pymeasure.instruments.ophir.ophir_base.OphirCommunication(*adapter*, *name='Ophir'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Base class for serial communication with Ophir devices; it does not define properties.

Communication uses ASCII and works with RS-232 and USB connections.

For USB, a COM (win32) object is also available as another option instead of this driver.

 check_errors()

After setting a value, check for errors.

Return type:

`list`[`Any`]

 read(***kwargs*)

Read a response.

Return type:

`str`

 values(*command*, *separator='*, *'*, *cast=<class 'float'>*, ***kwargs*)

Write a command to the instrument, then return formatted values from the response as a list.

Return type:

`list`[`Union`[`TypeVar`(`T`), `str`]]

 write(*command*, ***kwargs*)

Send a command to the device.

Return type:

`None`

 *class *pymeasure.instruments.ophir.ophir_base.OphirBase(*adapter*, *name='Ophir'*, ***kwargs*)

Bases: `OphirCommunication`

Represents an Ophir laser power/energy meter device.

The shared command set applies to USBI, Juno, Juno+, NovaII, Vega, StarLite, StarBright, and Centauri devices. Some of those devices support additional commands exposed through Mixin classes. Other devices, including Nova and Pulsar, implement only a subclass of this command group.

 *class *Capabilities(**values*)

Bases: `IntFlag`

 *class *LegacyModes(**values*)

Bases: `Enum`

 *class *Modes(**values*)

Bases: `IntEnum`

 *class *ScreenModes(**values*)

Bases: `IntEnum`

 *property *actual_range*: Any*

Read the range currently in effect, especially useful when `range` is 'AUTO'.

 *property *baud_rate*: Any*

Control the communication baud rate.

 *property *bc20_mode*: Any*

Set BC20 sensor mode. Some devices also allow mode to be used.

 clear_wavelength_entry(*index*)

Remove the wavelength-list entry at the given zero-based index.

The entry cannot be the active index. Use `define_wavelength_entry()` to assign a new value. Read `wavelength_list` for the configured entries and wavelength limits.

Return type:

`None`

 define_wavelength_entry(*index*, *value*)

Set a wavelength in nm at the given zero-based position in the wavelength list.

The target wavelength-list slot must be empty; clear it with `clear_wavelength_entry()`. Read `wavelength_list` for the configured entries and wavelength limits.

Return type:

`None`

 *property *diffuser*: Any*

Control pyroelectric sensors diffuser.

 *property *energy*: Any*

Read the latest energy measurement in J. (dynamic)

 *property *energy_flag*: Any*

Read whether a fresh energy measurement has arrived.

 *property *energy_ready*: Any*

Read whether the sensor is ready to take another energy measurement.

 *property *energy_threshold*: Any*

Set the sensor energy threshold and return the possible values as a list.

 *property *exposure_energy*: Any*

Read exposure energy in J, pulse count, and elapsed time in s.

 *property *frequency*: Any*

Get latest frequency in Hz.

 *property *head_information*: HeadInfo*

Read sensor-head information.

 *property *head_type*: Any*

Read the more detailed head type.

 *property *id*: Any*

Read instrument information as a list containing 'instrument', 'serialNumber', and 'name'.

 *property *mains*: Any*

Control the configured mains frequency.

 *property *maximum_frequency*: Any*

Read the maximum sensor pulse frequency for energy pulses in Hz.

 *property *mode*: Any*

Set the device measurement mode; use `Modes`. (dynamic)

 *property *mode_legacy*: Any*

Set measurement mode using one of `LegacyModes`; when possible, prefer `mode`.

 *property *position*: Any*

Read position (x,y) and spot size in mm.

 *property *power*: Any*

Read the next power measurement in W. (dynamic)

 *property *pulse_length*: Any*

Set the maximum pulse length used for measurement. (dynamic)

 *property *range*: Any*

Set the current range; see `range_entries` for allowed values. (dynamic)

 *property *range_entries*: dict[str, int]*

Read every supported range together with its index.

When Auto is available, its index is -1. The highest numeric range has index 0.

 *property *range_index*: Any*

Set the index of the selected range from the range list.

 *property *range_max*: Any*

Read the largest permitted reading for the active range.

 reset()

Reset the device, such as after changing the head.

Return type:

`None`

 save_head_configuration(*config*)

Save selected sensor configuration. :rtype: `None`

-

‘S’ for startup

-

‘C’ for calibration

-

'R' means Responsive for thermopile sensors.

The response is "*SAVED", "*UNCHANGED", or "?FAILED".

 save_instrument_configuration()

Save instrument configuration.

The response is "*SAVED", "*UNCHANGED", or "?FAILED".

Return type:

`None`

 save_zero()

Store the zeroing-process result in memory.

Return type:

`None`

 *property *screen_mode*: Any*

Select a screen mode for the device; use `ScreenModes`.

 *property *sensor_filter*: Any*

Control photodiode sensors filter.

 *property *software_version*: Any*

Get the current software version.

 start_streaming(*downsampling=0*)

Begin streaming mode, in which the device sends every downsampling measurement.

Return type:

`None`

 stop_streaming()

Stop streaming mode.

Return type:

`None`

 *property *threshold*: Any*

Set the sensor threshold as a fraction with 4 decimals, returning current, minimum, and maximum values.

 *property *units*: Any*

Get the current measurement unit.

 *property *wavelength*: Any*

Set the selected wavelength range from the wavelength list.

Read this attribute or `wavelength_list` to refresh the available wavelength list. Use `wavelength_value` to assign the value for the current wavelength entry. (dynamic)

 *property *wavelength_index*: Any*

Set the selected wavelength index in the wavelength list.

 *property *wavelength_list*: tuple[tuple[float, float] | None, Sequence[float | str | None]]*

Read wavelength limits for the continuous sensor and the wavelength list.

 *property *wavelength_value*: Any*

For continuous sensors only, set the currently selected entry's wavelength in nm as an int. (dynamic)

 zero()

Zero the measurement circuitry; doing this once every two months is recommended.

Return type:

`None`

 zero_abort()

Abort an active zeroing operation, if one is running, and return its status string.

Return type:

`None`

 *property *zero_status*: Any*

Read the zeroing process status.

 *class *pymeasure.instruments.ophir.ophir_base.ChannelMixin

Bases: `object`

Mixin for channels.

For Pulsar, Centauri.

 *property *channel*: Any*

Channel number for Pulsar or Centauri devices; numbering begins at 1.

 *class *pymeasure.instruments.ophir.ophir_base.AverageMixin

Bases: `object`

Mixin for averaging methods.

For Nova II, Vega.

 *property *average*: Any*

Get the latest averaged measurement.

 *property *average_configuration*: Any*

Set sensor averaging.

 *property *average_flag*: Any*

Read whether a new averaged reading has been processed.

 *class *pymeasure.instruments.ophir.ophir_base.KeyMixin(***kwargs*)

Bases: [`CommonBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase)

Mixin for pressing keys remotely.

 *class *Keys(**values*)

Bases: `IntEnum`

 key_legends()

Return key legends. A tilde '~' marks the active key.

Return type:

`str`

 press_key(*key*)

Simulate a keypress.

Display keys below, from left to right, are 0 to 3. Arrow keys are right (4), left (5), up (6), and down (7); Enter is 8.

Return type:

`None`

## Nova

### Nova

 *class *pymeasure.instruments.ophir.nova.Nova(*adapter*, *name='Nova'*, ***kwargs*)

Bases: [`KeyMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.KeyMixin), `NovaEnums`, [`OphirCommunication`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.OphirCommunication)

For the older Nova device.

Most commands are unsupported. Available commands are grouped here as `AT`, `BC`, `BM`, `DI`, `EF`, `ER`, `FE`, `FO`, `FP`, `FS`, and `FZ`; also `HI`, `HT`, `II`, `KL`, `LI`, `LR`, `LS`, `RE`, `RN`, and `SE`; and finally `SF`, `SI`, `SK`, `SL`, `SP`, `VE`, `WL`, `WN`, and `WW`.

 *property *diffuser*: Any*

Control pyroelectric sensors diffuser.

 *property *energy*: Any*

Read the latest energy measurement in J. (dynamic)

 *property *energy_flag*: Any*

Read whether a fresh energy measurement has arrived.

 *property *energy_ready*: Any*

Read whether the sensor is ready to take another energy measurement.

 *property *energy_timeout*: float*

Set the timeout, in ms, while waiting for an energy signal.

 *property *frequency*: Any*

Get latest frequency in Hz.

 *property *head_information*: HeadInfo*

Read sensor-head information.

 *property *head_type*: Any*

Read the more detailed head type.

 *property *id*: Any*

Read instrument information as a list containing 'instrument', 'serialNumber', and 'name'.

 *property *mode*: Any*

Set the measurement mode with one of [`LegacyModes`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.OphirBase.LegacyModes); when possible, prefer `mode`.

 *property *power*: Any*

Read the next power measurement in W. (dynamic)

 *property *power_timeout*: float*

Set the timeout, in ms, while waiting for a power signal.

 *property *range*: Any*

Set the current range; see `range_entries` for allowed values. (dynamic)

 reset()

Reset the device, such as after changing the head.

Return type:

`None`

 *property *screen_mode*: Any*

Select a screen mode for the device; use [`ScreenModes`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.OphirBase.ScreenModes).

 *property *software_version*: Any*

Get the current software version.

 *property *units*: Any*

Get the current measurement unit.

 *property *wavelength*: Any*

Set the selected wavelength range from the wavelength list.

Read this attribute or `wavelength_list` to refresh the available wavelength list. Use `wavelength_value` to assign the value for the current wavelength entry. (dynamic)

## Vega

### Vega

 *class *pymeasure.instruments.ophir.vega.Vega(*adapter*, *name='Vega'*, ***kwargs*)

Bases: [`AverageMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.AverageMixin), [`KeyMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.KeyMixin), [`OphirBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.OphirBase)

Represents an Ophir Vega laser power/energy meter.

 *class *Modes(**values*)

Bases: `IntEnum`

Supported Vega measurement modes.

## Ophir

### Ophir

This part documents the implemented Ophir instruments. Ophir is an MKS instruments brand. For unsupported hardware, see [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Ophir Base](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html)
  - [`OphirCommunication`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.OphirCommunication)
  - [`OphirBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.OphirBase)
  - [`ChannelMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.ChannelMixin)
  - [`AverageMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.AverageMixin)
  - [`KeyMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html#pymeasure.instruments.ophir.ophir_base.KeyMixin)

- [Nova](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/nova.html)
  - [`Nova`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/nova.html#pymeasure.instruments.ophir.nova.Nova)

- [Nova II](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/novaII.html)
  - [`NovaII`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/novaII.html#pymeasure.instruments.ophir.novaII.NovaII)

- [Vega](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/vega.html)
  - [`Vega`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/vega.html#pymeasure.instruments.ophir.vega.Vega)
