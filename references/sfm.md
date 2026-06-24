# Sfm

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### R&S SFM TV test transmitter

 *class *pymeasure.instruments.rohdeschwarz.sfm.SFM(*adapter*, *name='Rohde&Schwarz SFM'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Interface representation for the Rohde&Schwarz SFM TV test transmitter, used to communicate with the instrument.

Note

This implementation currently supports only the first system in the unit.

Supporting systems 2-6 would require additional source-code extension.

The intermodulation subsystem has not been implemented yet.

 *property *R75_out*: Any*

Bool property enabling or disabling use of the 75R output, when that option is installed.

| Value | Meaning |
| --- | --- |
| False | 50R output active (N) |
| True | 75R output active (BNC) |

See chapter 3.6.5 of the manual as well.

 *property *TV_country*: Any*

String property selecting the country-specific video/sound system behavior to use.

Possible values are:

| Value | Meaning |
| --- | --- |
| BG_G | BG General |
| DK_G | DK General |
| I_G | I General |
| L_G | L General |
| GERM | Germany |
| BELG | Belgium |
| NETH | Netherlands |
| FIN | Finland |
| AUST | Australia |
| BG_T | BG Th |
| DENM | Denmark |
| NORW | Norway |
| SWED | Sweden |
| GUS | Russia |
| POL1 | Poland |
| POL2 | Poland |
| HUNG | Hungary |
| CHEC | Czech Republic |
| CHINA1 | China |
| CHINA2 | China |
| GRE | Great Britain |
| SAFR | South Africa |
| FRAN | France |
| USA | United States |
| KOR | Korea |
| JAP | Japan |
| CAN | Canada |
| SAM | South America |

Check the manual to confirm the details for these settings.

 *property *TV_standard*: Any*

String property selecting the video standard type.

Possible values are:

| Value | Lines | System |
| --- | --- | --- |
| BG | 625 | PAL |
| DK | 625 | SECAM |
| I | 625 | PAL |
| K1 | 625 | SECAM |
| L | 625 | SECAM |
| M | 525 | NTSC |
| N | 625 | NTSC |

Check the manual to confirm the details for these settings.

 *property *basic_info*: Any*

String property reporting which hardware modules are installed in the unit.

 *property *beeper_enabled*: Any*

Bool property for controlling beeper status,

See chapter 3.6.8 of the manual as well.

 calibration(*number=1*, *subsystem=None*)

Function that calibrates the full modulator when subsystem is omitted, or calibrates one modulator subsystem when that parameter is provided.

Valid subsystem selections: “NICam, VISion, SOUNd1, SOUNd2, CODer”

 channel_down_relative()

Moves the output frequency downward to the next lower channel or special channel, using the active country settings.

 *property *channel_sweep_start*: Any*

Float property setting the channel-sweep start frequency in Hz.

-

Minimum 5 MHz

-

Maximum 1 GHz

 *property *channel_sweep_step*: Any*

Float property setting the channel-sweep start frequency in Hz.

-

Minimum 5 MHz

-

Maximum 1 GHz

 *property *channel_sweep_stop*: Any*

Float property setting the channel-sweep start frequency in Hz.

-

Minimum 5 MHz

-

Maximum 1 GHz

 *property *channel_table*: Any*

String property selecting the channel table in use.

Possible selections are:

| Value | Meaning |
| --- | --- |
| DEF | Default channel table |
| USR1 | User table No. 1 |
| USR2 | User table No. 2 |
| USR3 | User table No. 3 |
| USR4 | User table No. 4 |
| USR5 | User table No. 5 |

See chapter 3.6.6.1 of the manual as well.

 channel_up_relative()

Moves the output frequency upward to the next higher channel or special channel, using the active country settings.

 coder_adjust()

Begins automatic adjustment of the differential deviation.

See chapter 3.6.6.4 of the manual as well.

 *property *coder_id_frequency*: Any*

int property setting the coder identification frequency.

valid range 0 .. 200 Hz

 *property *coder_modulation_degree*: Any*

float property setting the modulation degree for coder identification.

valid range: 0 .. 0.9

 *property *coder_pilot_deviation*: Any*

int property setting deviation for the coder pilot frequency.

valid range: 1 .. 4 kHz

 *property *coder_pilot_frequency*: Any*

int property setting the coder pilot frequency.

valid range: 40 .. 60 kHz

 *property *cw_frequency*: Any*

Float property setting the CW-frequency in Hz.

-

Minimum 5 MHz

-

Maximum 1 GHz

 *property *date*: Any*

List property containing the RTC date for the unit.

 *property *event_reg*: Any*

Event-register content for the Status Operation Register; also see chapter 3.6.7 of the manual.

 *property *ext_ref_base_unit*: Any*

Bool property for the basic unit external reference.

| Value | Meaning |
| --- | --- |
| False | Internal 10 MHz is used |
| True | External 10 MHz is used |

 *property *ext_ref_extension*: Any*

Bool property for the extension-frame external reference.

| Value | Meaning |
| --- | --- |
| False | Internal 10 MHz is used |
| True | External 10 MHz is used |

 *property *ext_vid_connector*: Any*

String property selecting which connector supplies the video-source input.

Possible selections are:

| Value | Meaning |
| --- | --- |
| HIGH | Front connector - Hi-Z |
| LOW | Front connector - 75R |
| REAR1 | Rear connector 1 |
| REAR2 | Rear connector 2 |
| AUTO | Automatic assignment |

 *property *external_modulation_frequency*: Any*

int property setting the external modulator frequency.

valid range: 32 .. 46 MHz

 *property *external_modulation_power*: Any*

int property setting the external modulator output power.

valid range: -7..0 dBm

See chapter 3.6.6.5 of the manual as well.

 *property *external_modulation_source*: Any*

Bool property for selecting the modulation source.

See chapter 3.6.6.8 of the manual as well.

 *property *frequency*: Any*

Float property setting the frequency in Hz.

-

Minimum 5 MHz

-

Maximum 1 GHz

 *property *frequency_mode*: Any*

String property selecting which unit is used.

Possible selections are:

| Value | Meaning |
| --- | --- |
| CW | Continuous wave mode |
| FIXED | fixed frequency mode |
| CHSW | Channel sweep |
| RFSW | Frequency sweep |

Note

Choosing the sweep mode starts the sweep immediately!

 *property *gpib_address*: Any*

int property setting the unit's GPIB address.

valid range: 0..30

 *property *high_frequency_resolution*: Any*

Property for controlling the frequency resolution,

Possible selections are:

| Value | Meaning |
| --- | --- |
| False | Low resolution (1000Hz) |
| True | High resolution (1Hz) |

 *property *level*: Any*

Float property setting the output level in dBm,

-

Minimum -99dBm

-

Maximum is 10dBm, depending on output mode.

See chapter 3.6.6.2 of the manual as well.

 *property *level_mode*: Any*

String property selecting output attenuator behavior and linearity mode.

Possible selections are:

| Value | Meaning | max. output level |
| --- | --- | --- |
| NORM | Normal mode | +6 dBm |
| LOWN | low noise mode | +10 dBm |
| CONT | continuous mode | +10 dBm |
| LOWD | low distortion mode | +0 dBm |

Continuous mode permits as much as 14 dB of level adjustment without engaging the mechanical attenuator.

 *property *lower_sideband_enabled*: Any*

Bool property enabling or disabling use of the lower sideband.

See chapter 3.6.6.10 of the manual as well.

 *property *modulation_enabled*: Any*

Bool property for controlling modulation status.

 *property *nicam_IQ_inverted*: Any*

Bool property selecting whether NICAM IQ signals are inverted.

| Value | Meaning |
| --- | --- |
| False | normal (IQ) |
| True | inverted (QI) |

 *property *nicam_additional_bits*: Any*

int property setting additional data in the NICAM modulator.

valid range: 0 .. 2047

 *property *nicam_audio_frequency*: Any*

int property setting the internal sound-generator frequency.

valid range: 0 Hz .. 15 kHz

 *property *nicam_audio_volume*: Any*

float property setting NICAM modulator audio volume in dB.

valid range: 0..60 dB

 *property *nicam_bit_error_enabled*: Any*

Bool property enabling an artificial bit error rate to be applied.

 *property *nicam_bit_error_rate*: Any*

float property setting the artificial bit error rate.

valid range: 1.2E-7 .. 2E-3

 *property *nicam_carrier_enabled*: Any*

Bool property selecting whether the NICAM carrier is on or off.

 *property *nicam_carrier_frequency*: Any*

float property setting the NICAM carrier frequency.

valid range: 33.05 MHz +/- 0.2 Mhz

 *property *nicam_carrier_level*: Any*

float property setting the NICAM carrier value.

valid range: -40 .. -13 dB

 *property *nicam_control_bits*: Any*

int property setting additional data in the NICAM modulator.

valid range: 0 .. 3

 *property *nicam_data*: Any*

int property setting data in the NICAM modulator.

valid range: 0 .. 2047

 *property *nicam_intercarrier_frequency*: Any*

float property setting the NICAM carrier inter-carrier frequency.

valid range: 5 .. 9 MHz

 *property *nicam_mode*: Any*

String property selecting the signal type transmitted through NICAM.

Possible values are:

| Value | Meaning |
| --- | --- |
| MON | Mono sound + NICAM data |
| STER | Stereo sound |
| DUAL | Dual channel sound |
| DATA | NICAM data only |

See chapter 3.6.6.6 of the manual as well.

 *property *nicam_preemphasis_enabled*: Any*

Bool property for the J17 preemphasis status.

 *property *nicam_source*: Any*

String property selecting the signal source for NICAM.

Possible values are:

| Value | Meaning |
| --- | --- |
| INT | Internal audio generator(s) |
| EXT | External audio source |
| CW | Continuous wave signal |
| RAND | Random data stream |
| TEST | Test signal |

 *property *nicam_test_signal*: Any*

int property selecting the applied test signal.

| Value | Meaning |
| --- | --- |
| 1 | Test signal 1 (91 kHz square wave, I&Q 90deg apart) |
| 2 | Test signal 2 (45.5 kHz square wave, I&Q 90deg apart) |
| 3 | Test signal 3 (182 kHz sine wave, I&Q in phase) |

 *property *normal_channel*: Any*

int property for the currently selected regular/normal channel number; valid selections depend on the country settings.

 *property *operation_enable_reg*: Any*

Enable-register content for the Status Operation Register.

Valid range: 0…32767

 *property *output_voltage*: Any*

Float property setting the output level in Volt,

Minimum is 2.50891e-6, maximum is 0.707068, depending on output mode; also see chapter 3.6.6.12 of the manual.

 *property *questionable_event_reg*: Any*

Event-register content for the Status Questionable Operation Register.

 *property *questionable_operation_enable_reg*: Any*

Enable-register content for the Status Questionable Operation Register.

Valid range 0…32767

 *property *questionanble_status_reg*: Any*

Condition-register content for the Status Questionable Operation Register.

 *property *remote_interfaces*: Any*

String property selecting remote-control interfaces.

Possible selections are:

| Value | Meaning |
| --- | --- |
| OFF | no remote control |
| GPIB | GPIB only enabled |
| SER | RS232 only enabled |
| BOTH | GPIB & RS232 enabled |

 *property *rf_out_enabled*: Any*

Bool property for controlling RF-output status.

 *property *rf_sweep_center*: Any*

Float property setting the sweep center frequency in Hz.

-

Minimum 5 MHz

-

Maximum 1 GHz

 *property *rf_sweep_span*: Any*

Float property setting the sweep span in Hz,

-

Minimum 1 kHz

-

Maximum 1 GHz

 *property *rf_sweep_start*: Any*

Float property setting the sweep start frequency in Hz.

-

Minimum 5 MHz

-

Maximum 1 GHz

 *property *rf_sweep_step*: Any*

Float property setting the sweep stepwidth in Hz,

-

Minimum 1 kHz

-

Maximum 1 GHz

 *property *rf_sweep_stop*: Any*

Float property setting the sweep stop frequency in Hz.

-

Minimum 5 MHz

-

Maximum 1 GHz

 *property *scale_volt*: Any*

String property selecting the unit used for voltage entries on the unit.

Allowed values are AV,FV, PV, NV, UV, MV, V, KV, MAV, GV; then TV, PEV, EV, DBAV, DBFV, DBPV, DBNV, DBUV, DBMV, DBV; then DBKV, DBMAv, DBGV, DBTV, DBPEv, DBEV.

See chapter 3.6.9 of the manual as well.

 *property *serial_baud*: Any*

int property setting the serial communication speed,

Possible values are: 110,300,600,1200,4800,9600,19200

 *property *serial_bits*: Any*

int property setting how many bits serial communication uses.

Possible values are: 7 or 8

 *property *serial_flowcontrol*: Any*

String property selecting the handshake type used for serial communication.

Possible values are:

| Value | Meaning |
| --- | --- |
| NONE | no flow-control/handshake |
| XON | XON/XOFF flow-control |
| ACK | hardware handshake with RTS&CTS |

 *property *serial_parity*: Any*

String property selecting the parity type used for serial communication.

Possible values are:

| Value | Meaning |
| --- | --- |
| NONE | no parity |
| EVEN | even parity |
| ODD | odd parity |
| ONE | parity bit fixed to 1 |
| ZERO | parity bit fixed to 0 |

 *property *serial_stopbits*: Any*

int property setting the number of stop-bits used in serial communication,

Possible values are: 1 or 2

 *property *sound_mode*: Any*

String property selecting the audio-signal type.

Possible values are:

| Value | Meaning |
| --- | --- |
| MONO | MOnoaural sound |
| PIL | pilot-carrier + mono |
| BTSC | BTSC + mono |
| STER | Stereo sound |
| DUAL | Dual channel sound |
| NIC | NICAM + Mono |

 *property *special_channel*: Any*

int property for the currently selected special channel number; valid selections depend on the country settings.

 *property *status_info_shown*: Any*

Bool property selecting whether the display shows information during remote control.

 status_preset()

Partly resets the SCPI status-reporting structures.

 *property *status_reg*: Any*

Condition-register content for the Status Operation Register.

 *property *subsystem_info*: Any*

String property reporting information about the system configuration.

 *property *system_number*: Any*

int property for the selected systems, if more than 1 available.

-

Minimum 1

-

Maximum 6

 *property *time*: Any*

List property containing the RTC time for the unit.

 *property *vision_average_enabled*: Any*

Bool property for controlling average mode in the vision system.

 *property *vision_balance*: Any*

float property setting the vision modulator balance.

valid range: -0.5 .. 0.5

 *property *vision_carrier_enabled*: Any*

Bool property for controlling vision carrier status.

See chapter 3.6.6.9 of the manual as well.

 *property *vision_carrier_frequency*: Any*

float property setting the vision carrier frequency.

valid range: 32 .. 46 MHz

 *property *vision_clamping_average*: Any*

float property setting the vision modulator operation point.

valid range: -0.5 .. 0.5

 *property *vision_clamping_enabled*: Any*

Bool property for controlling vision modulator clamping behavior.

 *property *vision_clamping_mode*: Any*

String property selecting the vision modulator clamping mode.

Possible selections: HARD or SOFT.

 *property *vision_precorrection_enabled*: Any*

Bool property for controlling vision modulator precorrection behavior.

 *property *vision_residual_carrier_level*: Any*

float property setting the residual carrier value.

valid range: 0 .. 0.3 (30%)

 *property *vision_sideband_filter_enabled*: Any*

Bool property controlling use of the VSBF (vestigal sideband filter) in the vision modulator.

 *property *vision_videosignal_enabled*: Any*

Bool property selecting whether the video signal is on or off.

 *class *pymeasure.instruments.rohdeschwarz.sfm.Sound_Channel(*instrument*, *number*)

Bases: `object`

Class object representing the two sound channels.

See chapter 3.6.6.7 of the user manual as well.

 *property *carrier_enabled*: Any*

Bool property selecting whether the audio carrier is on or off.

 *property *carrier_frequency*: Any*

float property setting the sound carrier frequency.

valid range: 32 .. 46 MHz

 *property *carrier_level*: Any*

float property setting audio-carrier level in dB relative to the vision carrier (0dB).

valid range: -34 .. -6 dB

 *property *deviation*: Any*

int property setting deviation for the selected audio signal.

valid range: 0 .. 110 kHz

 *property *frequency*: Any*

int property setting the internal sound-generator frequency.

valid range: 300 Hz .. 15 kHz

 *property *modulation_degree*: Any*

float property setting audio-signal modulation depth; note: only for use of AM in Standard L.

valid range: 0 .. 1 (100%)

 *property *modulation_enabled*: Any*

Bool property for controlling audio modulation status.

| Value | Meaning |
| --- | --- |
| False | modulation disabled |
| True | modulation enabled |

 *property *preemphasis_enabled*: Any*

Bool property selecting whether audio preemphasis is on or off.

 *property *preemphasis_time*: Any*

int property controlling the audio-signal preemphasis mode.

| Value | Meaning |
| --- | --- |
| 50 | 50 us preemphasis |
| 75 | 75 us preemphasis |

 *property *use_external_source*: Any*

Bool property for selecting the audio source.

| Value | Meaning |
| --- | --- |
| False | Internal audio generator(s) |
| True | External signal source |

 values(*command*, ***kwargs*)

Reads a value set from the instrument via the adapter and forwards any keyword arguments.
