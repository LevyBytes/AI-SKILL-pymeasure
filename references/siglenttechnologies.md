# Siglent Spd1168X, Siglent Spdbase, Siglent Sds1000Xhd

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Siglent SPD1168X Power Supply; Siglent Technologies; Siglent Technologies Base Class; Siglent SDS1000XHD Oscilloscope.

## Siglent SPD1168X Power Supply

### Siglent SPD1168X Power Supply

 *class *pymeasure.instruments.siglenttechnologies.SPD1168X(*adapter*, *name='Siglent Technologies SPD1168X Power Supply'*, ***kwargs*)

Bases: [`SPDSingleChannelBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html#pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDSingleChannelBase)

Model the Siglent SPD1168X Power Supply.

 ch_1

Channel:

[`SPDChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html#pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDChannel)

## Siglent Technologies

### Siglent Technologies

Here, the implemented Siglent Technologies instruments have their dedicated notes. For hardware that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Siglent Technologies Base Class](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html)
  - [`SPDBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html#pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDBase)
  - [`SPDSingleChannelBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html#pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDSingleChannelBase)
  - [`SPDChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html#pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDChannel)
  - [`SystemStatusCode`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html#pymeasure.instruments.siglenttechnologies.siglent_spdbase.SystemStatusCode)

- [Siglent SPD1168X Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spd1168x.html)
  - [`SPD1168X`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spd1168x.html#pymeasure.instruments.siglenttechnologies.SPD1168X)

- [Siglent SPD1305X Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spd1305x.html)
  - [`SPD1305X`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spd1305x.html#pymeasure.instruments.siglenttechnologies.SPD1305X)

- [Siglent SDS1072CML Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1072cml.html)
  - [`SDS1072CML`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1072cml.html#pymeasure.instruments.siglenttechnologies.SDS1072CML)
  - [`VoltageChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1072cml.html#pymeasure.instruments.siglenttechnologies.siglent_sds1072cml.VoltageChannel)
  - [`TriggerChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1072cml.html#pymeasure.instruments.siglenttechnologies.siglent_sds1072cml.TriggerChannel)

- [Siglent SDS1000XHD Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1000xhd.html)
  - [`SDS1000XHD`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1000xhd.html#pymeasure.instruments.siglenttechnologies.SDS1000XHD)
  - [`AnalogChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1000xhd.html#pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.AnalogChannel)
  - [`WaveformChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1000xhd.html#pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.WaveformChannel)
  - [`AdvancedMeasurementItem`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1000xhd.html#pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.AdvancedMeasurementItem)
  - [`MeasureChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1000xhd.html#pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.MeasureChannel)
  - [`TriggerChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1000xhd.html#pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.TriggerChannel)

## Siglent Technologies Base Class

### Siglent Technologies Base Class

 *class *pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDBase(*adapter*, *name='Siglent SPDxxxxX instrument Base Class'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Shared base for Siglent SPDxxxxX instruments.

Uses `SPDChannel` for measurement channels.

 enable_local_interface(*enable=True*)

Set the availability of the local interface.

Type:

bool `True`: turns the local interface on; `False`: turns it off.

 *property *error*: Any*

Return the instrument error code together with its descriptive information.

Type:

string

 *property *fw_version*: Any*

Return the instrument software version.

Type:

string

 recall_config(*index*)

Recall a config from memory.

Parameters:

**index** – int: memory-location index from which the configuration is recalled

 save_config(*index*)

Store the active configuration in memory.

Parameters:

**index** – int: memory-location index where the configuration is saved

 *property *selected_channel*: Any*

Set or read the instrument's selected channel.

:type : int (dynamic)

 shutdown()

Force the voltage setting to zero, then turn off the output.

 *property *system_status_code*: Any*

Get the system status register.

Type:

`SystemStatusCode`

 *class *pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDSingleChannelBase(*adapter*, *name='Siglent SPDxxxxX instrument Base Class'*, ***kwargs*)

Bases: `SPDBase`

 enable_4W_mode(*enable=True*)

Enable 4-wire mode.

Type:

bool `True`: turns 4-wire mode on; `False`: turns it off.

 *class *pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDChannel(*parent*, *id*, *voltage_range=[0, 16]*, *current_range=[0, 8]*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Channel implementation shared by Siglent SPDxxxxX instruments.

 configure_timer(*step*, *voltage*, *current*, *duration*)

Configure the timer step.

Parameters:

-

**step** – int: step index where the configuration is saved

-

**voltage** – float: voltage setpoint assigned to the step

-

**current** – float: step current limit

-

**duration** – int: step duration, in seconds

 *property *current*: Any*

Measure the channel output current.

Type:

float

 *property *current_limit*: Any*

Set or read the channel output-current configuration.

:type : float (dynamic)

 enable_output(*enable=True*)

Enable the channel output.

Type:

bool `True`: turns the output on; `False`: turns it off

 enable_timer(*enable=True*)

Enable the channel timer.

Type:

bool `True`: turns the timer on; `False`: turns it off

 *property *power*: Any*

Measure the channel output power.

Type:

float

 *property *voltage*: Any*

Measure the channel output voltage.

Type:

float

 *property *voltage_setpoint*: Any*

Set or read the channel output-voltage configuration.

:type : float (dynamic)

 *class *pymeasure.instruments.siglenttechnologies.siglent_spdbase.SystemStatusCode(**values*)

System status enum values implemented with `IntFlag`

Use together with `system_status_code`.

>
| Value | Enum |
| --- | --- |
| 256 | WAVEFORM_DISPLAY |
| 64 | TIMER_ENABLED |
| 32 | FOUR_WIRE |
| 16 | OUTPUT_ENABLED |
| 1 | CONSTANT_CURRENT |
| 0 | CONSTANT_VOLTAGE |

## Siglent SDS1000XHD Oscilloscope

### Siglent SDS1000XHD Oscilloscope

 *class *pymeasure.instruments.siglenttechnologies.SDS1000XHD(*adapter*, *name='Siglent SDS1000xHD Oscilloscope'*, *timeout=2000*, *chunk_size=20971520*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model the SIGLENT SDS1000xHD Oscilloscope.

The SDS1000X-HD series provides high-definition oscilloscope models with expanded measurement support and a refined interface. The implementation covers typical oscilloscope workflows, including waveform acquisition, measurement handling, and trigger configuration.

 acquisition

Channel:

`AcquisitionChannel`

 channel_1

Channel:

`AnalogChannel`

 channel_2

Channel:

`AnalogChannel`

 channel_3

Channel:

`AnalogChannel`

 channel_4

Channel:

`AnalogChannel`

 measure

Channel:

`MeasureChannel`

 timebase

Channel:

`TimebaseChannel`

 trigger

Channel:

`TriggerChannel`

 waveform_channels

Channels:

`wf_C1`: `WaveformChannel`, `wf_C2`: `WaveformChannel`, `wf_C3`: `WaveformChannel`, `wf_C4`: `WaveformChannel`, `wf_F1`: `WaveformChannel`, `wf_F2`: `WaveformChannel`, `wf_F3`: `WaveformChannel`, `wf_F4`: `WaveformChannel`, `wf_D0`: `WaveformChannel`, `wf_D1`: `WaveformChannel`, `wf_D2`: `WaveformChannel`, `wf_D3`: `WaveformChannel`, `wf_D4`: `WaveformChannel`, `wf_D5`: `WaveformChannel`, `wf_D6`: `WaveformChannel`, `wf_D7`: `WaveformChannel`, `wf_D8`: `WaveformChannel`, `wf_D9`: `WaveformChannel`, `wf_D10`: `WaveformChannel`, `wf_D11`: `WaveformChannel`, `wf_D12`: `WaveformChannel`, `wf_D13`: `WaveformChannel`, `wf_D14`: `WaveformChannel`, `wf_D15`: `WaveformChannel`

 auto_setup()

Run the oscilloscope automatic setup routine.

 clear_sweeps_acq()

Clear stored sweeps and reset the acquisition statistics.

 *class *pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.AnalogChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Channel implementation for a SIGLENT SDS1000xHD Oscilloscope.

 *property *bandwidth_limit_enabled*: Any*

Set or read whether the bandwidth limit is enabled (bool).

 *property *coupling*: Any*

Set or read the channel coupling mode (str): ‘DC’, ‘AC’, or ‘GND’.

 *property *display_enabled*: Any*

Set or read whether the channel display is on (bool). This switches the specified channel on or off. It differs from visible_enabled, which only changes the display state.

 *property *invert*: Any*

Control signal inversion (bool).

 *property *label*: Any*

Set or read the channel label text (str).

 *property *offset*: Any*

Set or read the channel vertical offset in volts (float).

 *property *probe*: Any*

Set or read the probe attenuation factor (float).

 *property *scale*: Any*

Set or read a channel's vertical scale in V/divisions (float strictly between 1e-3 and 10).

 *property *unit*: Any*

Set or read the channel unit (str): ‘V’ or ‘A’.

 *property *visible_enabled*: Any*

Set or read whether the channel waveform appears on screen (bool). This property only changes waveform visibility. It differs from display_enabled, which controls the physical channel switch.

 *class *pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.WaveformChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

SDS1000XHD oscilloscope waveform channel.

Use this class to read waveform data from the oscilloscope. A waveform record has two parts: the preamble and the waveform data. The preamble supplies the metadata needed to decode the sample data; the waveform data contains the acquired values for each point in the selected source. Read each part with its own command.

 get_data()

Return waveform data from the oscilloscope for the active source.

This method obtains waveform data from the oscilloscope and uses the preamble property for descriptor details about the waveform format.

Returns:

A (time_values, volt_values) tuple: - time_values: list of time samples in seconds - volt_values: list of voltage samples in volts

Return type:

tuple

 *property *interval*: Any*

Set or read the data-point interval used for waveform transfer (int).

This sets the data-point spacing for waveform transfer with :WAVeform:DATA?. Use NR1 format (integer with no decimal point). Note: the accepted range depends on the values configured by :WAVeform:POINt and :WAVeform:STARt.

 *property *max_point*: Any*

Return the per-piece maximum point count used when waveform data is read in pieces (float).

This query reports how many points one piece can contain when waveform data must be split into pieces. Use it to plan segmented transfers for large waveforms.

 *property *point*: Any*

Set or read how many waveform points :WAVeform:DATA? transfers (int).

This sets the waveform-point count returned by :WAVeform:DATA?. Use NR1 format (integer with no decimal point). Note: the permitted range depends on the current waveform point.

 *property *preamble

Return the waveform preamble descriptor data.

The preamble is binary metadata describing the waveform format. It includes offset and voltage scale, trigger delay, time interval, time division, ADC bit depth, probe attenuation factor, and voltage codes per division. Parsing follows the binary approach used by get_descriptor.

Returns:

A dictionary containing these keys:

-

vdiv: Voltage per division (float)

-

voffset: Voltage offset (float)

-

interval: point-to-point time interval (float)

-

trdl: Trigger delay (float)

-

tdiv: Time per division (float)

-

vcode_per: division-to-division voltage code factor (float)

-

adc_bit: ADC bit depth (int)

-

probe: Probe attenuation factor (float)

Return type:

dict

 *property *source*: Any*

Set or read the oscilloscope source used for waveform transfer (str).

 *property *start_point*: Any*

Set or read the first data point used for waveform transfer (int).

This command selects the first data point returned by :WAVeform:DATA?. Its range depends on the current waveform point and the value configured with :WAVeform:POINt. Use NR1 format (integer with no decimal point).

 *property *width*: Any*

Set or read the output format used when waveform data is transferred (str).

This selects the active output format for waveform-data transfer. Options: ‘BYTE’ or ‘WORD’.

 *class *pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.AdvancedMeasurementItem(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Represent an advanced measurement item on the SDS1000xHD oscilloscope.

This class exposes controls for enabling or disabling the measurement item, choosing its source, and reading its value.

 *property *enabled*: Any*

Set or read whether the advanced measurement item is enabled (bool).

 *property *source1*: Any*

Set or read the first source used by the advanced measurement item (str).

 *property *source2*: Any*

Set or read the second source used by the advanced measurement item (str). Measurements that need two sources use this field.

 *property *statistics_all*: Any*

Return every statistic for the advanced measurement item. When statistics are enabled, all statistical data is returned; when disabled, the result is ‘OFF’.

 *property *statistics_count*: Any*

Return the measurement count used in the statistics calculation.

 *property *statistics_current*: Any*

Return the current statistical value as NR3 format (scientific notation, e.g., 1.23E+2).

 *property *statistics_maximum*: Any*

Return the maximum statistical value as NR3 format (scientific notation, e.g., 1.23E+2).

 *property *statistics_mean*: Any*

Return the mean statistical value as NR3 format (scientific notation, e.g., 1.23E+2).

 *property *statistics_minimum*: Any*

Return the minimum statistical value as NR3 format (scientific notation, e.g., 1.23E+2).

 *property *statistics_stddev*: Any*

Return the statistics standard deviation for the advanced measurement item. The value is reported in NR3 format (e.g., 1.23E+2).

 *property *type*: Any*

Set or read the advanced measurement type (str). This selects which advanced measurement is performed.

 *property *value*: Any*

Set or read the advanced measurement item value. The command returns the item's current value in NR3 format (e.g., 1.23E+2).

 *class *pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.MeasureChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Unified SDS1000xHD oscilloscope measurement class.

This class brings Simple, Advanced, Gate, and Threshold measurement features under one interface. It covers all measurement operations exposed for the SDS1000xHD.

 *property *advanced_line_number*: Any*

Set or read the total count of advanced measurement items shown (int strictly between 1 and 12).

 *property *advanced_mode_enabled*: Any*

Set or read whether advanced measurement mode is active (bool).

 clear_advanced()

Clear advanced measurements.

 clear_simple()

Clear simple measurements.

 *property *enabled*: Any*

Set or read whether the measurement function is active (bool).

 get_simple_value(*measurement_type*)

Return the value for a selected simple measurement type.

This method reads the current value for the requested simple measurement type.

Parameters:

**measurement_type** (*str*) –

Measurement type to query.
Valid values include PKPK, MAX, MIN, AMPL, TOP, BASE, LEVELX, CMEAN, MEAN, and STDEV.
Additional values include VSTD, RMS, CRMS, MEDIAN, CMEDIAN, OVSN, FPRE, OVSP, RPRE, and PER.
Timing-related values include FREQ, TMAX, TMIN, PWID, NWID, DUTY, NDUTY, WID, NBWID, and DELAY.
Edge and area values include TIMEL, RISE, FALL, RISE20T80, FALL80T20, CCJ, PAREA, NAREA, AREA, and ABSAREA.
Pulse and accumulated-area values include CYCLES, REDGES, FEDGES, EDGES, PPULSES, NPULSES, PACArea, NACArea, ACArea, and ABSACArea.

Note: use the simple_value_all property to retrieve every measurement value in one call.

Returns:

Measurement value returned in NR3 format (e.g., 1.23E+2)

Return type:

float

 reset_statistics()

Reset statistics for advanced measurements.

 *property *simple_item*: Any*

Set the simple measurement item.

This command configures a simple measurement type and whether it is active. Pass a tuple of (item, state).
For item (str), choose the measurement item to configure.
Valid item values include PKPK, MAX, MIN, AMPL, TOP, BASE, LEVELX, CMEAN, MEAN, and STDEV.
More item values include VSTD, RMS, CRMS, MEDIAN, CMEDIAN, OVSN, FPRE, OVSP, RPRE, and PER.
Timing item values include FREQ, TMAX, TMIN, PWID, NWID, DUTY, NDUTY, WID, NBWID, and DELAY.
Edge and area item values include TIMEL, RISE, FALL, RISE20T80, FALL80T20, CCJ, PAREA, NAREA, AREA, and ABSAREA.
Pulse and accumulated-area item values include CYCLES, REDGES, FEDGES, EDGES, PPULSES, NPULSES, PACArea, NACArea, ACArea, and ABSACArea.
For state (str), use the measurement-item state ON or OFF.

 *property *simple_source*: Any*

Set or read the source used for simple measurements.

 *property *simple_value_all*: Any*

Return all simple measurement values. Delay measurements are excluded from the returned set.

 *property *statistics_enabled*: Any*

Set or read whether measurement statistics are enabled (bool).

 *class *pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.TriggerChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

SDS1000xHD oscilloscope trigger channel.

This class exposes full SDS1000xHD trigger control through SCPI commands. It manages trigger-type-specific settings, because trigger types such as EDGE, SLOPe, etc. keep separate source, level, and coupling values. Supported source parameter values are: C1, C2, C3, C4, EX, EX5, LINE, where: - C1-C4: inputs from channels - EX: the external trigger input - EX5: the external trigger input divided by 5 - LINE: trigger from line frequency

 *property *edge_coupling*: Any*

Set or read the edge trigger coupling mode.

 *property *edge_high_impedance*: Any*

Control whether edge trigger uses high impedance (bool).

When True, select the 1MΩ high impedance input. When False, select the 50Ω low impedance input.

 *property *edge_hld_event*: Any*

Set or read the edge trigger holdoff event count (int strictly between 1 and 100000000). This count specifies how many trigger events are ignored before another trigger can be accepted.

 *property *edge_hld_off*: Any*

Set or read the edge trigger holdoff type (str).

Available options: - ‘OFF’: disable holdoff - ‘EVENTS’: use holdoff based on event count - ‘TIME’: use holdoff based on time

 *property *edge_hld_start*: Any*

Set or read the starting position for the edge trigger holdoff.

 *property *edge_hld_time*: Any*

Set or read the edge trigger holdoff time (float strictly between 8e-9 and 30). This value is the edge trigger holdoff duration in seconds. It defines the wait after one trigger event before the next trigger may be accepted.

 *property *edge_level*: Any*

Set or read the edge trigger level. The value is expressed in volts. For SDS1000X HD models, the range is: [-4.1*vertical_scale-vertical_offset, 4.1*vertical_scale-vertical_offset] See programming manual for other models.

 *property *edge_noise_reject*: Any*

Set or read edge trigger noise rejection (bool).

 *property *edge_slope*: Any*

Set or read the edge trigger slope.

 *property *edge_source*: Any*

Set or read the edge trigger source.

 force_trigger()

Force a trigger event.

 *property *frequency*: Any*

Return the trigger frequency reported by the hardware frequency counter. If available, the returned value is in hertz. Default precision is 3 digits, and the maximum valid precision is 7 digits. Use “:FORMat:DATA” command to configure data precision.

 *property *mode*: Any*

Control the trigger mode.

Available options:

-

AUTO: the oscilloscope searches for a trigger signal. If the condition is met, it displays ‘Trig’d’ with a stable waveform. Otherwise, it displays ‘Auto’ and an unstable waveform.

-

NORMal: the oscilloscope waits for a trigger signal. If the condition is met, it displays ‘Trig’d’ with a stable waveform. Otherwise, it displays ‘Ready’ and the last triggered waveform.

-

SINGle: single trigger mode. The oscilloscope waits for a trigger, then stops scanning once the trigger condition is satisfied.

-

FTRIG: force a trigger so a frame is acquired regardless of trigger conditions.

 run()

Put the oscilloscope into run state. This command starts acquisition and places the oscilloscope in running mode. Waveforms are then acquired and displayed continuously.

 *property *status*: Any*

Return the present trigger status, such as STOP, READY, ARM, TD, WAIT, etc.

 stop()

Put the oscilloscope into stop state. This command stops acquisition. The oscilloscope stops acquiring new waveforms and continues showing the most recently acquired waveform.

 *property *type*: Any*

Return the current trigger type as a dict.
Keys include “type”, which stores the trigger type.
Trigger type values include EDGE, SLOPe, PULSe, VIDeo, WINDow, INTerval, DROPout, and RUNT.
Additional trigger type values include PATTern, QUALified, DELay, NEDGe, SHOLd, IIC, SPI, UART, CAN, LIN, etc.
