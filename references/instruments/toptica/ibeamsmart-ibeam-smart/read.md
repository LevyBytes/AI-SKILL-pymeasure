# pymeasure.instruments.toptica.ibeamsmart.IBeamSmart.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read()

Read an instrument reply and extract values when possible.

Read an instrument reply containing at least two lines. Earlier lines hold the command response, while the final line should be ‘[OK]’, acknowledging that the device is ready for more commands.

Note: ‘[OK]’ is still the last message for an invalid command; in that case, an error message appears before the ‘[OK]’.

Value extraction: take &lt;value&gt; from ‘name = &lt;value&gt; [unit]’. If &lt;value&gt; cannot be identified, return the original string.

Returns:

ASCII response string from the instrument, excluding ‘[OK]’.
