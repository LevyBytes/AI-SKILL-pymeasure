# pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase.is_valid_response

[Owning PyMeasure class, adapter and connection contract](overview.md)

is_valid_response(*response*, *command*)

Checks whether the response returned after a command is valid and was understood by the instrument.

Parameters:

- **response** - ASCII string response from the device

- **command** - command from the original query

Returns:

True when the response is valid and indicates that the instrument recognised the command
