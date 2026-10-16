# pymeasure.instruments.teledyne.teledyneMAUI.TeledyneMAUIChannel.current_configuration

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *current_configuration

Return channel configuration as a dict containing these keys:

- “channel”: channel number (int)

- “attenuation”: probe attenuation (float)

- “bandwidth_limit”: bandwidth limit parsed for this channel (str)

- “coupling”: “ac 1M”, “dc 1M”, “ground” coupling (str)

- “offset”: vertical offset (float)

- “display”: currently displayed (bool)

- “volts_div”: vertical divisions (float)

- “trigger_coupling”: trigger coupling may be “dc” “ac” “highpass” “lowpass” (str)

- “trigger_level”: trigger level (float)

- “trigger_slope”: trigger slope may be “negative” “positive” “window” (str)
