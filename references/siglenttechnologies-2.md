# Siglent Sds1072Cml, Siglent Spd1305X

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Siglent SDS1072CML Oscilloscope; Siglent SPD1305X Power Supply.

## Siglent SDS1072CML Oscilloscope

### Siglent SDS1072CML Oscilloscope

 *class *pymeasure.instruments.siglenttechnologies.SDS1072CML(*adapter*, *name='Siglent SDS1072CML Oscilloscope'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

### Represents the SIGLENT SDS1072CML Oscilloscope

 channel_1

Channel:

`VoltageChannel`

 channel_2

Channel:

`VoltageChannel`

 trigger

Channel:

`TriggerChannel`

 arm()

Move acquisition mode from ‘STOPPED’ to ‘SINGLE’. Return True once the scope is armed and ready.

 *property *internal_state*: Any*

Read, then clear, the scope’s Internal state change register.

 *property *is_ready*: Any*

Return whether the scope can perform the next acquisition (bool).

 *property *status*: Any*

Read the scope sampling status (Stop, Ready, Trig’d, Armed).

 *property *template*: Any*

Return a template copy describing the logical entities that together form a complete waveform. The template fully details the variables held in a waveform descriptor.

 *property *time_division*: Any*

Set time division in seconds to the closest available value rounded downwards.

 wait(*time*)

Block further scope activity until the current acquisition finishes (p.146).

Parameters:

**time** – wait duration, expressed in seconds.

 *property *waveform_setup*: Any*

Choose how much waveform data is sent to the controller using a dict with these keys: - sparsing: interval between data points (0 and 1 return all points, 4 returns 1 out of 4 points, etc…) - number: maximum data points to return. 0 returns all points - first: index of the first data point for transfer (0 is first)

 *class *pymeasure.instruments.siglenttechnologies.siglent_sds1072cml.VoltageChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

### Implementation of a SIGLENT SDS1072CML Oscilloscope channel

 *property *coupling*: Any*

Set channel coupling mode (DC or AC).

 get_descriptor(*descriptor=None*)

Return the descriptor for waveform data sent by the device query. If a raw byte stream descriptor is supplied, decode that value; otherwise, query the device for it. :return: dict: A dictionary with the keys: - numDataPoints: point count in the waveform - verticalGain: voltage increment per code value (in V) - verticalOffset: voltage offset added to decoded voltage values - horizInterval: time interval between points in s - horizOffset: offset added to time steps - descriptorOffset: Length of the C1:WF ALL,#9000000346 message

 get_waveform()

Return channel-displayed waveforms as a tuple with elements: - time: (1d array) seconds from the trigger epoch for each waveform voltage value - voltages: (1d array) waveform values in V

 *property *vertical_division*: Any*

Set channel vertical sensitivity in V/divisions.

 *class *pymeasure.instruments.siglenttechnologies.siglent_sds1072cml.TriggerChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

### Implementation of trigger control channel

 get_trigger_config()

Return the active trigger configuration as a dict with these keys: - “type”: waveform acquisition condition [EDGE, slew,GLIT,intv,runt,drop] - “source”: source for trigger (str, {EX,EX/5,C1,C2}) - “hold_type”: hold category (refer to page 131 of programing guide) - “hold_value1”: hold value1 setting (refer to page 131 of programing guide) - “level”: trigger set Level (float) - “slope”: (str,{POS,NEG,WINDOW}) Trigger on rising, falling or Window. - “mode”: post-trigger behavior (str, {NORM, AUTO, SINGLE,STOP}) - “coupling”: trigger-channel coupling (str,{AC,DC})

and refreshes the internal configuration status

 set_trigger_config(***kwargs*)

Apply the active trigger configuration using these keys: - “type”: waveform acquisition condition [EDGE, slew,GLIT,intv,runt,drop] - “source”: source for trigger (str, {EX,EX/5,C1,C2}) - “hold_type”: hold category (refer to page 131 of programing guide) - “hold_value1”: hold value1 setting (refer to page 131 of programing guide) - “level”: trigger set Level (float) - “slope”: (str,{POS,NEG,WINDOW}) Trigger on rising, falling or Window. - “mode”: post-trigger behavior (str, {NORM, AUTO, SINGLE,STOP}) - “coupling”: trigger-channel coupling (str,{AC,DC})

Return a flag showing whether every specified entry was set correctly on the oscilloscope, and refresh the internal trigger configuration.

 *property *trigger_coupling*: Any*

Return the active trigger coupling as a dict with keys: - “source”: source selected for coupling changes (str, {EX,EX/5,C1,C2}) - “coupling”: trigger-channel coupling (str,{AC,DC})

 *property *trigger_level*: Any*

Return the active trigger level as a dict with keys: - “source”: source selected for level changes (str, {EX,EX/5,C1,C2}) - “level”: trigger set Level (float)

 *property *trigger_mode*: Any*

Return the active trigger mode as a dict with keys: - “mode”: post-trigger behavior (str, {NORM, AUTO, SINGLE,STOP})

 *property *trigger_setup*: Any*

Return the active trigger setup as a dict with keys: - “type”: waveform acquisition condition [EDGE, slew,GLIT,intv,runt,drop] - “source”: source for trigger (str, {EX,EX/5,C1,C2}) - “hold_type”: hold category (refer to page 131 of programing guide) - “hold_value1”: hold value1 setting (refer to page 131 of programing guide)

 *property *trigger_slope*: Any*

Return the active trigger slope as a dict with keys: - “source”: source selected for level changes (str, {EX,EX/5,C1,C2}) - “slope”: (str,{POS,NEG,WINDOW}) Trigger on rising, falling or Window.

## Siglent SPD1305X Power Supply

### Siglent SPD1305X Power Supply

 *class *pymeasure.instruments.siglenttechnologies.SPD1305X(*adapter*, *name='Siglent Technologies SPD1305X Power Supply'*, ***kwargs*)

Bases: [`SPDSingleChannelBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html#pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDSingleChannelBase)

Model the Siglent SPD1305X Power Supply.

 ch_1

Channel:

[`SPDChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html#pymeasure.instruments.siglenttechnologies.siglent_spdbase.SPDChannel)
