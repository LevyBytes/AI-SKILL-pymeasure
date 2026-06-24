# Activetechnologies, Heidenhain, Ipgphotonics, Comedi

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Active Technologies; Active Technologies AWG-401x 1.2GS/s Arbitrary Waveform Generator; Heidenhain ND287 Position Display Unit; Heidenhain; YAR fiber amplifier series; IPG Photonics; Comedi data acquisition.

## Active Technologies

### Active Technologies

Implemented Active Technologies instruments are documented in this section. To cover a missing instrument, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Active Technologies AWG-401x 1.2GS/s Arbitrary Waveform Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/activetechnologies/AWG401x.html)
  - [`AWG401x_AFG`](https://pymeasure.readthedocs.io/en/latest/api/instruments/activetechnologies/AWG401x.html#pymeasure.instruments.activetechnologies.AWG401x_AFG)
  - [`AWG401x_AWG`](https://pymeasure.readthedocs.io/en/latest/api/instruments/activetechnologies/AWG401x.html#pymeasure.instruments.activetechnologies.AWG401x_AWG)
  - [`ChannelAFG`](https://pymeasure.readthedocs.io/en/latest/api/instruments/activetechnologies/AWG401x.html#pymeasure.instruments.activetechnologies.AWG401x.ChannelAFG)

## Active Technologies AWG-401x 1.2GS/s Arbitrary Waveform Generator

### Active Technologies AWG-401x 1.2GS/s Arbitrary Waveform Generator

 *class *pymeasure.instruments.activetechnologies.AWG401x_AFG(*adapter*, ***kwargs*)

Bases: `AWG401x_base`

Models the Active Technologies AWG-401x Arbitrary Waveform Generator when it is operating in AFG mode.

```python
wfg = AWG401x_AFG("TCPIP::192.168.0.123::INSTR")

wfg.reset()                     # Reset the instrument at default state

wfg.channels[1].shape = "SINUSOID"    # Sets a sine waveform on CH1
wfg.channels[1].frequency = 4.7e3     # Sets the frequency to 4.7 kHz on CH1
wfg.channels[1].amplitude = 1         # Set amplitude of 1 V on CH1
wfg.channels[1].offset = 0            # Set the amplitude to 0 V on CH1
wfg.channels[1].enabled = True        # Enables the CH1

wfg.channels[2].shape = "SQUARE"      # Sets a square waveform on CH2
wfg.channels[2].frequency = 100e6     # Sets the frequency to 100 MHz on CH2
wfg.channels[2].amplitude = 0.5         # Set amplitude of 0.5 V on CH2
wfg.channels[2].offset = 0            # Set the amplitude to 0 V on CH2
wfg.channels[2].enabled = True        # Enables the CH2

wfg.enabled = True              # Enable output of waveform generator
wfg.beep()                      # "beep"

print(wfg.check_errors())       # Get the error queue

```

 ch_1

Channel:

`ChannelAFG`

 ch_2

Channel:

`ChannelAFG`

 *property *enabled*: Any*

Enable or disable signal generation (bool).

 *class *pymeasure.instruments.activetechnologies.AWG401x_AWG(*adapter*, ***kwargs*)

Bases: `AWG401x_base`

Models the Active Technologies AWG-401x Arbitrary Waveform Generator when it is operating in AWG mode.

```python
wfg = AWG401x_AWG("TCPIP::192.168.0.123::INSTR")

wfg.reset()             # Reset the instrument at default state

# Set a oscillating waveform
wfg.waveforms["MyWaveform"] = [1, 0] * 8

for i in range(1, wfg.num_ch + 1):
    wfg.entries[1].channels[i].voltage_high = 1       # Sets high voltage = 1
    wfg.entries[1].channels[i].voltage_low = 0        # Sets low voltage = 1
    wfg.entries[1].channels[i].waveform = "SQUARE"    # Sets a square wave
    wfg.setting_ch[i].enabled = True            # Enable channel

wfg.entries.resize(2)           # Resize the number of entries to 2

wfg.entries[2].channels[1].waveform = "MyWaveform"   # Set custom waveform

wfg.enabled = True              # Enable output of waveform generator
wfg.beep()                      # "beep"

print(wfg.check_errors())       # Get the error queue

```

 *class *DummyEntriesElements(*parent*, *number_of_channel*)

Bases: `Sequence`

Dummy List Class used to enumerate every sequencer entry, with the contents loaded in real-time.

 *class *WaveformsLazyDict(*parent*)

Bases: `MutableMapping`

This class derives from MutableMapping to provide a custom dict that can lazy load, edit, remove, and create instrument waveform entries.

 reset()

Reset the class state by reloading the waveforms from the instrument.

 *property *burst_count*: Any*

Set or query the burst count parameter.(dynamic)

 *property *burst_count_max*: Any*

Return the maximum allowed burst count parameter.

 *property *burst_count_min*: Any*

Return the minimum allowed burst count parameter.

 *property *enabled*: Any*

Enable or disable signal generation.

 *property *entry_level_strategy*: Any*

Set or query the Entry Length Strategy. This setting determines how sequencer entry lengths relate to the channel waveform lengths assigned to each entry. The possible values are:

-

ADAPTL<ONGER>: by default, a sequencer entry uses the length of the longest analog-channel waveform assigned to that entry.

-

ADAPTS<HORTER>: by default, a sequencer entry uses the length of the shortest analog-channel waveform assigned to that entry.

-

DEF<AULT>: by default, a sequencer entry uses the value configured by the Sequencer Item Default Length [N] parameter

 list_files(*path=None*)

Return a List of tuples for every file found in a directory. When no path is supplied, the current directory is used

 *property *num_ch*: Any*

Return the analog channel count.

 *property *num_dch*: Any*

Return the digital channel count.

 remove_file(*file_name*, *path=None*)

Remove a specified file

 *property *run_mode*: Any*

Set or query the AWG run mode. The possible values are:

-

CONT<INUOUS>: waveforms repeat according to the entry repetition parameter, and the full sequence loops circularly.

-

BURS<T>: the AWG waits for a trigger event. After that trigger, each waveform repeats according to the entry repetition parameter, and the full sequence loops circularly for the number of cycles specified by Burst Count[N]. With Burst Count[N]=1, the instrument enters Single mode and runs the sequence one time.

-

TCON<TINUOUS>: the AWG waits for a trigger event, then repeats each waveform according to the entry repetition parameter while the full sequence loops circularly.

-

STEP<PED>: before executing each sequencer entry, the AWG waits for a trigger event. The entry waveform repeats according to the entry repetition parameter. After an entry finishes generating, the output holds either that entry final sample or the upcoming entry initial sample until another trigger arrives. When the sequence reaches its end, execution starts again at the first entry.

-

ADVA<NCED>: enables the Ã¢â‚¬Å“AdvancedÃ¢â‚¬Â mode. In this mode, sequence execution may be redirected with conditional and unconditional jumps (JUMPTO and GOTO commands) plus dynamic jumps (PATTERN JUMP commands).

The *RST command restores this parameter to CONTinuous.

 *property *run_status*: Any*

Return the AWG run state. Possible values are: STOPPED, WAITING_TRIGGER, RUNNING

 *property *sample_decreasing_strategy*: Any*

Set or query the Sample Decreasing Strategy. When the waveform is longer than the sequencer entry, this parameter decides how the excess samples are handled. Accepted values: DECIM<ATION>, CUTT<AIL>, CUTH<EAD>.

 *property *sample_increasing_strategy*: Any*

Set or query the Sample Increasing Strategy. The â€œSample increasing strategyâ€ parameter chooses how to extend a waveform when its length is less than the sequencer entry length. Allowed settings: INTER<POLATION>, RETURN<ZERO>, HOLD<LAST>, SAMPLESM<ULTIPLICATION>

 *property *sampling_rate*: Any*

Set or query the Sampling Clock sample rate.(dynamic)

 *property *sampling_rate_max*: Any*

Return the maximum Sampling Clock sample rate.

 *property *sampling_rate_min*: Any*

Return the minimum Sampling Clock sample rate.

 save_file(*file_name*, *data*, *path=None*, *override_existing=False*)

Write a string to a file stored on the instrument

 trigger()

Force a trigger event to occur.

 *property *trigger_source*: Any*

Set or query the instrument trigger source. The possible values are:

-

TIM<ER>: triggers are generated at regular intervals.

-

EXT<ERNAL>: triggers are received from the external BNC connector.

-

MAN<UAL>: triggers are generated through software or with the trigger button on front panel.

 *property *waveforms

Return a dict of every waveform present in the instrument system (Wave. List). The returned values can be changed, deleted, or expanded with new waveforms

 *class *pymeasure.instruments.activetechnologies.AWG401x.ChannelAFG(*instrument*, *id*)

Bases: `ChannelBase`

Implements an Active Technologies AWG-4000 channel in AFG mode.

 *property *baseline_offset*: Any*

Set or query the offset level for the specified channel. The amplitude parameter determines the available offset range. (dynamic)

 *property *baseline_offset_max*: Any*

Return the maximum offset voltage level allowed for the output waveform.

 *property *baseline_offset_min*: Any*

Return the minimum offset voltage level allowed for the output waveform.

 *property *frequency*: Any*

Set or query the output waveform frequency. This command can be used when Run Mode is set to any value except Sweep. The output waveform type determines the frequency range; changing that type can also change the active output frequency because the allowed range changes. The amplitude parameter also affects the frequency range.(dynamic)

 *property *frequency_max*: Any*

Return the maximum frequency allowed for the output waveform.

 *property *frequency_min*: Any*

Return the minimum frequency allowed for the output waveform.

 *property *load_impedance*: Any*

Set or query the output load impedance for the specified channel. The chosen value is applied to amplitude, offset, and high/low level settings. The impedance may be any value from 1 ÃŽÂ© to 1 MÃŽÂ©. The default value is 50 ÃŽÂ©.

 *property *output_impedance*: Any*

Set or query the output impedance used by the instrument. Choose 5 Ohm, or use the default setting, 50 Ohm.

 *property *phase*: Any*

Set or query the output waveform phase for the specified channel. Values are expressed in degrees.(dynamic)

 *property *phase_max*: Any*

Return the maximum phase allowed for the output waveform.

 *property *phase_min*: Any*

Return the minimum phase allowed for the output waveform.

 *property *shape*: Any*

Set or query the carrier waveform shape. The available choices depend on the selected modality; consult the instrument manual. Changing this property while output is running stops the instrument.
Choices include SIN<USOID>, SQU<ARE>, PULS<E>, RAMP, PRN<OISE>, DC, and SINC.
Additional choices include GAUS<SIAN>, LOR<ENTZ>, and ERIS<E>.
The list also includes EDEC<AY>, HAV<ERSINE>, ARBB, EFIL<E>, and DOUBLEPUL<SE>.

 *property *voltage_amplitude*: Any*

Set or query output amplitude for the specified channel. The voltage_unit property selects the amplitude measurement unit. Noise carriers use Vpk instead of Vpp, while DC level carriers make this command raise an error. The carrier waveform frequency and offset parameter can limit the permitted amplitude range. (dynamic)

 *property *voltage_amplitude_max*: Any*

Return the maximum amplitude voltage level allowed for the output waveform.

 *property *voltage_amplitude_min*: Any*

Return the minimum amplitude voltage level allowed for the output waveform.

 *property *voltage_high*: Any*

Set or query the waveform high level. Noise level may limit the high level so the maximum amplitude is not exceeded. If the carrier is Noise or DC level, this command and its query produce an error.(dynamic)

 *property *voltage_high_max*: Any*

Return the maximum high voltage level allowed for the output waveform.

 *property *voltage_high_min*: Any*

Return the minimum high voltage level allowed for the output waveform.

 *property *voltage_low*: Any*

Set or query the waveform low level. Noise level may limit the low level so the maximum amplitude is not exceeded. If the carrier is Noise or DC level, this command and its query produce an error.(dynamic)

 *property *voltage_low_max*: Any*

Return the maximum low voltage level allowed for the output waveform.

 *property *voltage_low_min*: Any*

Return the minimum low voltage level allowed for the output waveform.

 *property *voltage_offset*: Any*

Set or query the offset level for the specified channel. The amplitude parameter determines the available offset range. (dynamic)

 *property *voltage_offset_max*: Any*

Return the maximum offset voltage level allowed for the output waveform.

 *property *voltage_offset_min*: Any*

Return the minimum offset voltage level allowed for the output waveform.

 *property *voltage_unit*: Any*

Set or query output amplitude units. The possible choices are: VPP, VRMS, DBM. This command leaves output offset, high level, and low level unchanged.

## Heidenhain ND287 Position Display Unit

### Heidenhain ND287 Position Display Unit

 *class *pymeasure.instruments.heidenhain.ND287(*adapter*, *name='Heidenhain ND287'*, *units='mm'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents the Heidenhain ND287 position display unit, which displays and reads absolute position values measured by Heidenhain encoders.

 check_errors()

Read an error status message and log it when an error is detected.

Returns:

String containing the error message.

 *property *id

Return the device string identification property.

 *property *position*: Any*

Measure the encoder current position (float). The get_process maps the returned value to a float in the units specified by `ND287.units`. Because the mapping varies slightly by unit, get_process is adjusted dynamically.(dynamic)

 *property *status*: Any*

Return the encoder status bar

 *property *units

Set or query the unit of measure recorded for the device. Valid values are Ã¢â‚¬ËœmmÃ¢â‚¬â„¢ and Ã¢â‚¬ËœinchÃ¢â‚¬â„¢. This parameter can only be changed manually on the device, so the property only checks that the instance units match the physical device configuration. I.e., it does not alter any physical device setting.

## Heidenhain

### Heidenhain

Implemented Heidenhain instruments are documented in this section. To cover a missing instrument, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Heidenhain ND287 Position Display Unit](https://pymeasure.readthedocs.io/en/latest/api/instruments/heidenhain/nd287.html)
  - [`ND287`](https://pymeasure.readthedocs.io/en/latest/api/instruments/heidenhain/nd287.html#pymeasure.instruments.heidenhain.ND287)

## YAR fiber amplifier series

### YAR fiber amplifier series

 *class *pymeasure.instruments.ipgphotonics.yar.YAR(*adapter*, *name='YAR fiber amplifier'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Communicates with the YAR fiber amplifier series from IPG Photonics.

This describes the RS232 command set; GPIB uses different commands.

 *class *Status(**values*)

Bases: `IntFlag`

 check_set_errors()

After setting a property, check whether errors were reported.

Called when `check_set_errors=True` is configured for that property.

 clear()

Reset all errors.

 *property *current*: Any*

Measure diode current in A.

 *property *emission_enabled*: Any*

Enable or disable amplifier emission (bool).

 *property *firmware*: Any*

Get firmware version

 *property *id

Get the model number.

 *property *maximum_case_temperature*: Any*

Measure the optical module maximum temperature in Ã‚Â°C.

 *property *minimum_display_power*: Any*

Measure the lowest displayable output power in W.

 *property *power*: Any*

Measure current output power in W.(dynamic)

 *property *power_range

Return the power limits in W.

 *property *power_setpoint*: Any*

Set or query the output power setpoint in W.(dynamic)

 read()

Read an instrument response and determine whether it indicates an error.

 *property *status

Get the current status.

 *property *temperature*: Any*

Measure case temperature in °C.

 *property *temperature_seed*: Any*

Measure the current seed temperature in Ã‚Â°C

 *property *wavelength_temperature*: Any*

Set or query the seed wavelength control temperature in Ã‚Â°C.

## IPG Photonics

### IPG Photonics

Implemented IPG Photonics instruments are documented in this section. To cover a missing instrument, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [YAR fiber amplifier series](https://pymeasure.readthedocs.io/en/latest/api/instruments/ipgphotonics/yar.html)
  - [`YAR`](https://pymeasure.readthedocs.io/en/latest/api/instruments/ipgphotonics/yar.html#pymeasure.instruments.ipgphotonics.yar.YAR)

## Comedi data acquisition

### Comedi data acquisition

Comedi libraries offer a convenient way to work with data acquisition cards, but they are limited to Linux compatible operating systems.

 pymeasure.instruments.comedi.getAI(*device*, *channel*, *range=None*)

Return the analog input channel selected for a given device

 pymeasure.instruments.comedi.getAO(*device*, *channel*, *range=None*)

Return the analog output channel selected for a given device

 pymeasure.instruments.comedi.readAI(*device*, *channel*, *range=None*, *count=1*)

Read a single measurement (count==1) from the analog input channel of the specified device. Multiple readings can be performed when count is not one; those readings are separated by an arbitrary time

 pymeasure.instruments.comedi.writeAO(*device*, *channel*, *voltage*, *range=None*)

Write one voltage value to the analog output channel of the specified device
