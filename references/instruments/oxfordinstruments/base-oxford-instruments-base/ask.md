# pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command*)

Sends the command to the instrument, checks that the response is valid, and returns the resulting ASCII response. If the response is invalid, another attempt is made until the maximum number of attempts has been reached.

Parameters:

**command** - ASCII command string sent to the instrument

Returns:

Instrument response as an ASCII string

Raises:

`OxfordVISAError` if the maximum number of attempts is exceeded before a valid response is obtained
