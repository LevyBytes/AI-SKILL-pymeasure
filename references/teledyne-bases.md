# Teledyne Bases

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Teledyne Oscilloscope base classes

### Teledyne Oscilloscope

 *class *pymeasure.instruments.teledyne.TeledyneOscilloscope(*adapter*, *name='Teledyne Oscilloscope'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Abstract superclass for Teledyne Lecroy oscilloscope implementations.

Teledyne oscilloscope models expose broadly comparable controls, so shared behavior is collected in this base class. Individual instruments may still differ or expose conflicting interface details.

Attributes:

WRITE_INTERVAL_S: shortest allowed gap between successive commands. When a new command arrives sooner than WRITE_INTERVAL_S after the last one, execution waits until WRITE_INTERVAL_S seconds have elapsed. Since some oscilloscope operations take noticeable time, users may need to adjust the inter-command delay. The WRITE_INTERVAL_S default is 10ms, but the best value depends strongly on the command mix and transport. In practice, values from 10ms through 500ms second have worked, depending on connection latency and the operations being issued.

 ch_1

Channel:

`TeledyneOscilloscopeChannel`

 ch_2

Channel:

`TeledyneOscilloscopeChannel`

 ch_3

Channel:

`TeledyneOscilloscopeChannel`

 ch_4

Channel:

`TeledyneOscilloscopeChannel`

 autoscale()

Autoscale displayed channels.

 *property *bwlimit*: Any*

Configure the internal low-pass filter across every channel.(dynamic)

 center_trigger()

Move trigger levels to the midpoint of the trigger source waveform.

 ch(*source*)

Return a channel object by numeric index or channel name. When source is â€œmathâ€, return the scope object itself instead.

Parameters:

**source** â€“ accepts 1, 2, 3, 4 or C1, C2, C3, C4, MATH

Returns:

handle to the selected source.

 default_setup()

Prepare the oscilloscope for control from a remote client.

COMM_HEADER selects how query replies from the oscilloscope are formatted. It does not change how incoming messages are parsed by the instrument. Header mnemonics may still be sent in either long or short spelling regardless of CHDR. Setting COMM_HEADER to OFF makes replies contain only the essential data, which simplifies parsing. User code should leave COMM_HEADER alone during normal operation, because any value other than OFF prevents this driver from interpreting responses correctly.

 display_parameter(*parameter*, *channel*)

Equivalent to the display_parameter method provided by the Channel subclass.

 download_image()

Capture the oscilloscope display as BMP bytes, using the requested file format.

 download_waveform(*source*, *requested_points=None*, *sparsing=None*)

Read sampled data points from the selected oscilloscope source.

The call returns two np.ndarray objects for data and time values, plus a dict waveform preamble containing waveform metadata.

Parameters:

-

**source** â€“ measurement source; valid values are â€œC1â€, â€œC2â€, â€œC3â€, â€œC4â€, â€œMATHâ€.

-

**requested_points** â€“ count of points to acquire. If None, reuse the point count from the previous call, meaning the value currently stored in oscilloscope memory. If 0, return the largest available point count. (default: `None`)

-

**sparsing** â€“ spacing between returned data points. For example if sparsing = 4, one sample is read for every 4 stored points. If 0 or None, keep the sparsing from the prior call, namely the value recorded in oscilloscope memory. (default: `None`)

Returns:

data_ndarray, time_ndarray, waveform_preamble_dict: the waveform_preamble property describes the dict layout.

 *property *intensity*: Any*

Adjust the grid or trace intensity as a percent value

 measure_parameter(*parameter*, *channel*)

Equivalent to the measure_parameter method implemented on the Channel subclass

 *property *memory_size*: Any*

Set the maximum memory depth using a float or string. Examples include 500, 100e6, â€œ100Kâ€, â€œ25MAâ€.

The response is returned as a float in every case.

 run()

Starts repetitive acquisitions.

This matches pressing the front-panel Run key.

 single()

Instructs the instrument to capture one triggered acquisition.

This matches pressing the front-panel Single key.

 stop()

End acquisition, matching the front-panel Stop key.

 *property *timebase

Return the timebase settings in a dict with these keys:

-

â€œtimebase_scaleâ€: horizontal seconds/div scale (float)

-

â€œtimebase_offsetâ€: seconds from trigger to reference position (float)

 *property *timebase_offset*: Any*

Set the time gap, in seconds, from the trigger event to the reference position, which defaults to screen center.

 *property *timebase_scale*: Any*

Set the main-window horizontal seconds-per-division scale as a float.

 timebase_setup(*scale=None*, *offset=None*)

Configure the timebase while leaving omitted parameters unchanged. Changing one value can also alter related values. Consult the oscilloscope documentation, and call timebase_setup repeatedly when staged adjustments are required.

Parameters:

-

**scale** â€“ seconds between the trigger event and reference position. (default: `None`)

-

**offset** â€“ horizontal seconds/div scale. (default: `None`)

 *property *trigger

Return trigger configuration as a dict containing these keys:

-

“mode”: trigger sweep mode [auto, normal, single, stop]

-

â€œtrigger_typeâ€: waveform acquisition trigger condition [edge, slew,glit,intv,runt,drop]

-

“source”: trigger source [c1,c2,c3,c4]

-

â€œhold_typeâ€: hold type (refer to page 172 of programing guide)

-

â€œhold_value1â€: hold value1 (refer to page 172 of programing guide)

-

â€œhold_value2â€: hold value2 (refer to page 172 of programing guide)

-

â€œcouplingâ€: coupling applied to the chosen trigger sources

-

â€œlevelâ€: active trigger source voltage level

-

â€œlevel2â€: lower trigger voltage for the active source, used only with slew/runt trigger

-

â€œslopeâ€: slope setting for the selected trigger source

 *property *trigger_mode*: Any*

Set the trigger sweep mode using a string value.

<mode>:= {AUTO,NORM,SINGLE,STOP}

-

auto : In AUTO sweep mode, the oscilloscope searches for a signal matching the trigger conditions. When the condition is met, the upper-left running state displays Trigâ€™d and a stable waveform is shown. If it is not met, the state remains Auto and the displayed waveform is unstable.

-

normal : In NORMAL sweep mode, the oscilloscope waits for a trigger and searches for signals satisfying the configured conditions. A successful trigger makes the running state display Trigâ€™d and shows a stable waveform. Without a matching trigger, the state displays Ready and the screen either keeps the previous triggered waveform or, if none exists, shows no waveform.

-

single : In SINGLE sweep mode, the SINGLE key backlight turns on and the oscilloscope waits while checking for a trigger signal that satisfies the conditions. On a match, the running state shows Trigâ€™d and the waveform becomes stable. The oscilloscope then stops scanning, the RUN/STOP key lights red, and the status changes to Stop. If no trigger is found, the state shows Ready and no waveform is displayed.

-

stopped : STOP is accepted by this command as an option, although it is not an oscilloscope trigger mode.

 *property *trigger_select

Choose the condition, as a string, that starts waveform acquisition.

Some trigger types require extra settings. Those settings are supplied as name/value pairs: the first element identifies the variable to update, and the second gives its replacement value. Pairs can appear in any order, and only changed variables need to be included.

Five parameters may be supplied. Parameters 1. 2. 3. are always required, while Parameters 4. 5. are only needed for particular combinations of earlier parameters.

1.

<trig_type>:={edge, slew, glit, intv, runt, drop}

2.

<source>:={c1, c2, c3, c4, line}

3.

<hold_type>:=

  -

{ti, off} for edge trigger.

  -

{ti} for drop trigger.

  -

{ps, pl, p2, p1} applies to glit/runt trigger.

  -

{is, il, i2, i1} applies to slew/intv trigger.

4.

<hold_value1>:= a time value including unit.

5.

<hold_value2>:= a time value including unit.

Note:

-

â€œlineâ€ is valid only when the trigger type is â€œedgeâ€.

-

Provide every time argument as a multiple of seconds, using scientific notation when useful.

-

Permitted hold_values depend on trigger type: [80nS, 1.5S] for â€œedgeâ€ trigger, and [2nS, 4.2S] for others.

-

trigger_select automatically chooses the short, normal, or extended command form from the expected parameter count.

 trigger_setup(*mode=None*, *source=None*, *trigger_type=None*, *hold_type=None*, *hold_value1=None*, *hold_value2=None*, *coupling=None*, *level=None*, *level2=None*, *slope=None*)

Set up trigger.

Omitted parameters are left as-is. Updating one parameter can affect others. Use the oscilloscope documentation, and make multiple trigger_setup and channel_setup calls when stepwise configuration is necessary.

Parameters:

-

**mode** – trigger sweep mode [auto, normal, single, stop] (default: `None`)

-

**source** – trigger source [c1, c2, c3, c4, line] (default: `None`)

-

**trigger_type** â€“ waveform acquisition trigger condition [edge,slew,glit,intv,runt,drop] (default: `None`)

-

**hold_type** â€“ hold type (refer to page 172 of programing guide) (default: `None`)

-

**hold_value1** â€“ hold value1 (refer to page 172 of programing guide) (default: `None`)

-

**hold_value2** â€“ hold value2 (refer to page 172 of programing guide) (default: `None`)

-

**coupling** â€“ coupling used for the selected trigger sources (default: `None`)

-

**level** â€“ voltage level for the active trigger source (default: `None`)

-

**level2** â€“ lower trigger voltage for the active trigger source, only with slew/runt trigger (default: `None`)

-

**slope** â€“ slope setting for the specified trigger source (default: `None`)

 *property *waveform_first_point*: Any*

Set the address of the first transmitted data point as an int. For waveforms captured in sequence mode, the value is the relative address within the selected segment. Addressing begins at zero for the first data point and must remain positive.

 *property *waveform_points*: Any*

Set how many waveform points the digitize method transfers, as an int. NP = 0 transfers every data point.

The oscilloscope can return fewer points than the requested nb value.

 *property *waveform_preamble

Return preamble data for the chosen waveform source as a dict with these keys:

-

â€œrequested_pointsâ€: data point count requested by the user (int)

-

â€œsampled_pointsâ€: data point count sampled by the oscilloscope (int)

-

â€œtransmitted_pointsâ€: data point count actually transmitted, when present (int)

-

â€œmemory_sizeâ€: internal oscilloscope memory size in bytes (int)

-

â€œsparsingâ€: sparse point. It gives the spacing between data points. (int)

-

â€œfirst_pointâ€: address for the first data point to transmit (int)

-

â€œsourceâ€: data source : â€œC1â€, â€œC2â€, â€œC3â€, â€œC4â€, â€œMATHâ€.

-

â€œgrid_numberâ€: count of horizontal grids; this property is read-only

-

â€œxdivâ€: horizontal seconds-per-division scale

-

â€œxoffsetâ€: seconds between the trigger event and the reference position

-

â€œydivâ€: vertical scale, in Volts per division

-

â€œyoffsetâ€: Volts value displayed at screen center

 *property *waveform_sparsing*: Any*

Set the spacing between data points as an integer. For example:

SP = 0 transfers all data points. SP = 4 transfers 1 point out of every 4 data points.

 write(*command*, ***kwargs*)

Send the command to the instrument using the adapter.

Note: when the preceding command was issued less than WRITE_INTERVAL_S ago, this method waits out the remaining interval so command frequency never exceeds 1/WRITE_INTERVAL_S Hz.

Parameters:

**command** â€“ command string sent to the instrument

### Teledyne Channel

 *class *pymeasure.instruments.teledyne.teledyne_oscilloscope.TeledyneOscilloscopeChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Abstract base class representing a channel on a `TeledyneOscilloscope` device.

 *property *bwlimit*: Any*

Configure this channel's internal low-pass filter.

Current bandwidth settings are readable only for all channels together! (dynamic)

 *property *coupling*: Any*

Set coupling with a string parameter: â€œac 1Mâ€, â€œdc 1Mâ€, or â€œgroundâ€.

 *property *current_configuration

Return channel configuration as a dict containing these keys:

-

“channel”: channel number (int)

-

“attenuation”: probe attenuation (float)

-

“bandwidth_limit”: bandwidth limiting enabled (bool)

-

“coupling”: “ac 1M”, “dc 1M”, “ground” coupling (str)

-

“offset”: vertical offset (float)

-

“skew_factor”: channel-tochannel skew factor (float)

-

“display”: currently displayed (bool)

-

â€œunitâ€: unit string, either â€œAâ€ or â€œVâ€ (str)

-

“volts_div”: vertical divisions (float)

-

“inverted”: inverted (bool)

-

â€œtrigger_couplingâ€: trigger coupling may be â€œdcâ€ â€œacâ€ â€œhighpassâ€ â€œlowpassâ€ (str)

-

“trigger_level”: trigger level (float)

-

â€œtrigger_level2â€: lower trigger level used for SLEW or RUNT trigger (float)

-

â€œtrigger_slopeâ€: trigger slope may be â€œnegativeâ€ â€œpositiveâ€ â€œwindowâ€ (str)

 *property *display*: Any*

Enable or disable display output. (strict bool)

 *property *display_parameter*: Any*

Apply the selected algorithm to this channel's waveform processing and show the result on the front panel.

This command takes the parameters listed below:

| Parameter | Description |
| --- | --- |
| PKPK | vertical peak-to-peak |
| MAX | maximum vertical value |
| MIN | minimum vertical value |
| AMPL | vertical amplitude |
| TOP | waveform top value |
| BASE | waveform base value |
| CMEAN | mean value during the first cycle |
| MEAN | average value |
| RMS | RMS value |
| CRMS | RMS measurement during the first cycle |
| OVSN | overshoot of a falling edge |
| FPRE | preshoot of a falling edge |
| OVSP | overshoot of a rising edge |
| RPRE | preshoot of a rising edge |
| PER | period |
| FREQ | frequency |
| PWID | positive pulse width |
| NWID | negative pulse width |
| RISE | rise-time |
| FALL | fall-time |
| WID | Burst width |
| DUTY | positive duty cycle |
| NDUTY | negative duty cycle |
| ALL | All measurement |

 insert_id(*command*)

Substitute the channel id into a command at the placeholder.

Override this method in subclasses for alternate behavior, such as always prefixing commands with the channel id.

 measure_parameter(*parameter*)

Run the selected algorithm on a waveform and return the requested measurement.

Parameters:

**parameter** (`str`) â€“ identical to the display_parameter property

 *property *offset*: Any*

Set the screen center, in Volts, with a float parameter. The allowed range depends on range and scale. If the requested value is outside that range, the nearest permitted offset is selected automatically.

 *property *probe_attenuation*: Any*

Set probe attenuation. Accepted probe attenuation values run from 0.1 to 10000.

 *property *scale*: Any*

Set the vertical Volts-per-division scale.

 setup(***kwargs*)

Configure the channel, leaving unspecified settings unchanged.

Changing values such as probe attenuation can also change offset, range, and related settings. Check the oscilloscope documentation and call setup() multiple times if staged updates are needed. Property descriptions provide additional detail.

Parameters:

-

**bwlimit**

-

**coupling**

-

**display**

-

**invert**

-

**offset**

-

**skew_factor**

-

**probe_attenuation**

-

**scale**

-

**unit**

-

**trigger_coupling**

-

**trigger_level**

-

**trigger_level2**

-

**trigger_slope**

 *property *trigger_coupling*: Any*

Set input coupling for the selected trigger sources using a string.

-

ac: AC coupling blocks the DC component in the trigger path, which removes dc offset voltage from the trigger waveform. Use AC coupling for a stable edge trigger when the waveform carries a large dc offset.

-

dc: DC coupling passes both dc and ac signals into the trigger path.

-

lowpass: HFREJ coupling inserts a lowpass filter into the trigger path.

-

highpass: LFREJ coupling inserts a highpass filter into the trigger path.

 *property *trigger_level*: Any*

Set the trigger level voltage for the active trigger source as a float.

When two trigger levels are required, this command sets the higher trigger level voltage for the chosen source. `trigger_level2` sets the lower trigger level voltage.

When assigning the trigger level, divide it by probe attenuation. The datasheet does not document this behavior, so it is likely a scope firmware bug. Values outside the permitted range are clipped to the nearest legal value.

 *property *trigger_slope*: Any*

Set the trigger slope for the specified trigger source with a string.

<trig_slope>:={NEG,POS,WINDOW} for edge trigger <trig_slope>:={NEG,POS} for other trigger

| parameter | trigger slope |
| --- | --- |
| negative | Negative slope for edge trigger or another trigger |
| positive | Positive slope for edge trigger or another trigger |
| window | Window slope for edge trigger |

(dynamic)

### Teledyne MAUI Oscilloscope

 *class *pymeasure.instruments.teledyne.TeledyneMAUI(*adapter*, *name='Teledyne Oscilloscope'*, ***kwargs*)

Bases: `TeledyneOscilloscope`

Base class for MAUI-style Teledyne oscilloscopes.

This base class is usable immediately. Some attributes, especially channel count, may need adjustment for the connected instrument.

The API is documented in â€œMAUI Oscilloscopes Remote Control and Automation Manualâ€ ([link](https://cdn.teledynelecroy.com/files/manuals/maui-remote-control-and-automation-manual.pdf)).

This Teledyne oscilloscope family can also receive direct VBS commands. See `vbs_ask()` and `vbs_write()`.

 ch_1

Channel:

`TeledyneMAUIChannel`

 ch_2

Channel:

`TeledyneMAUIChannel`

 ch_3

Channel:

`TeledyneMAUIChannel`

 ch_4

Channel:

`TeledyneMAUIChannel`

 download_image(***kwargs*)

Capture the oscilloscope display as BMP bytes, using the requested file format.

By default, the hardcopy destination is â€œREMOTEâ€.

Parameters:

****kwargs** â€“ keyword arguments passed to `hardcopy_setup()`

 force_trigger()

Perform one acquisition when active trigger mode is enabled.

If the device is in â€˜Stop trigger modeâ€™, nothing is done.

 hardcopy_setup(***kwargs*)

Specify hardcopy settings.

Configure a printer connection or file-save behavior. Any subset of these parameters may be set.

Parameters:

-

**device** – {BMP, JPEG, PNG, TIFF}

-

**format** – {PORTRAIT, LANDSCAPE}

-

**background** – {Std, Print, BW}

-

**destination** – {PRINTER, CLIPBOARD, EMAIL, FILE, REMOTE}

-

**area** – {GRIDAREAONLY, DSOWINDOW, FULLSCREEN}

-

**directory** â€“ Legal DOS path, only for FILE mode

-

**filename** â€“ Filename string without extension, only for FILE mode

-

**printername** â€“ Valid printer name, only for PRINTER mode

-

**portname** – {GPIB, NET}

 *property *hardcopy_setup_current*: Any*

Get current hardcopy config.

 *property *trigger

Return trigger configuration as a dict containing these keys:

-

“mode”: trigger sweep mode [auto, normal, single, stop]

-

â€œtrigger_typeâ€: waveform acquisition trigger condition [edge,slew,glit,intv,runt,drop]

-

“source”: trigger source [c1,c2,c3,c4]

-

â€œhold_typeâ€: hold type (refer to page 172 of programing guide)

-

â€œhold_value1â€: hold value1 (refer to page 172 of programing guide)

-

â€œhold_value2â€: hold value2 (refer to page 172 of programing guide)

-

â€œcouplingâ€: coupling applied to the chosen trigger sources

-

â€œlevelâ€: active trigger source voltage level

-

â€œslopeâ€: slope setting for the selected trigger source

 vbs_ask(*name*)

Return a VBS variable's value.

Only target must be supplied; this method builds the query. Note: the target name is not escaped!

See `vbs_write()` for additional detail.

Minimal usage example:

```python
instrument.vbs_ask("app.Display.GridMode")

```

Return type:

`str`

 vbs_write(*message*)

Send a VBS command straight to the device.

This oscilloscope class also permits direct Visual Basic Scripting (VBScript) use. The method sends a literal VBS command. Use the â€˜MAUI Browserâ€™ on the oscilloscope to inspect all available variables.

Minimal usage example:

```python
instrument.vbs_write("app.Display.GridMode = Dual")

```

### Teledyne MAUI Channel

 *class *pymeasure.instruments.teledyne.teledyneMAUI.TeledyneMAUIChannel(*parent*, *id*, ***kwargs*)

Bases: `TeledyneOscilloscopeChannel`

Base class for channels on a `TeledyneMAUI` device.

 autoscale()

Run the channel auto-setup command.

 *property *current_configuration

Return channel configuration as a dict containing these keys:

-

“channel”: channel number (int)

-

“attenuation”: probe attenuation (float)

-

â€œbandwidth_limitâ€: bandwidth limit parsed for this channel (str)

-

“coupling”: “ac 1M”, “dc 1M”, “ground” coupling (str)

-

“offset”: vertical offset (float)

-

“display”: currently displayed (bool)

-

“volts_div”: vertical divisions (float)

-

â€œtrigger_couplingâ€: trigger coupling may be â€œdcâ€ â€œacâ€ â€œhighpassâ€ â€œlowpassâ€ (str)

-

“trigger_level”: trigger level (float)

-

â€œtrigger_slopeâ€: trigger slope may be â€œnegativeâ€ â€œpositiveâ€ â€œwindowâ€ (str)

 setup(***kwargs*)

Configure the channel, leaving unspecified settings unchanged.

Changing values such as probe attenuation can also change offset, range, and related settings. Check the oscilloscope documentation and call setup() multiple times if staged updates are needed. Property descriptions provide additional detail.

Parameters:

-

**bwlimit**

-

**coupling**

-

**display**

-

**offset**

-

**probe_attenuation**

-

**scale**

-

**trigger_coupling**

-

**trigger_level**

-

**trigger_slope**
