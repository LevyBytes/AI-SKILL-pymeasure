# pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*)

Writes a command to the instrument and checks whether the reply says that the supplied command was not understood. Oxford Instruments devices answer with '?xxx' for a command 'xxx' when that command is unknown, and answer with 'x' when the command is understood. A command beginning with "$" receives no reply from the instrument, so no reply check is performed in that case.

Raises:

Raises `OxfordVISAError` when the supplied command is not recognised by the instrument or the instrument response cannot be understood
