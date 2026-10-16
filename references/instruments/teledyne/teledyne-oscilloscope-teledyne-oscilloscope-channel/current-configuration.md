# pymeasure.instruments.teledyne.teledyne_oscilloscope.TeledyneOscilloscopeChannel.current_configuration

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_configuration

Return channel configuration as a dict containing these keys:

- “channel”: channel number (int)

- “attenuation”: probe attenuation (float)

- “bandwidth_limit”: bandwidth limiting enabled (bool)

- “coupling”: “ac 1M”, “dc 1M”, “ground” coupling (str)

- “offset”: vertical offset (float)

- “skew_factor”: channel-tochannel skew factor (float)

- “display”: currently displayed (bool)

- “unit”: unit string, either “A” or “V” (str)

- “volts_div”: vertical divisions (float)

- “inverted”: inverted (bool)

- “trigger_coupling”: trigger coupling may be “dc” “ac” “highpass” “lowpass” (str)

- “trigger_level”: trigger level (float)

- “trigger_level2”: lower trigger level used for SLEW or RUNT trigger (float)

- “trigger_slope”: trigger slope may be “negative” “positive” “window” (str)
