# pymeasure.instruments.ni.virtualbench.VirtualBench.PowerSupply.validate_channel

[Owning PowerSupply contract](overview.md)

validate_channel(*channel*, *current=False*, *voltage=False*)

Validate the channel string and confirm the requested output current/voltage values are inside that channel's output ranges

Parameters:

- **channel** (*str*) – Channel string (`"ps/+6V","ps/+25V","ps/-25V"`)

- **current** (*bool**, **optional*): Current output flag, defaults to False (default: `False`)

- **voltage** (*bool**, **optional*): Voltage output flag, defaults to False (default: `False`)

Returns:

channel or channel, current & voltage

Return type:

str or (str, float, float)
